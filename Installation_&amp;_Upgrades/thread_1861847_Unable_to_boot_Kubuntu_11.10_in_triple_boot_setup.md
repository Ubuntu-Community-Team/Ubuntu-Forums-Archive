---
title: "Unable to boot Kubuntu 11.10 in triple boot setup"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by moon_raker on 2011-10-16
Maybe someone can guide me here.
I have 2 hard disks. sda has Ubuntu Lucid with grub installed to mbr and 40_custom entries to boot the distros installed on sdb.
Newly installed Kubuntu 11.10 (replacing Ubuntu Maverick) is on sdb1 root and sdb5 home. (booted by symlink from Lucid)
Scientific Linux is on sdb6 root and sdb7 home. (booted by chainloader from Lucid)

The 40_custom file entries before installing new Kubuntu looked like this:-

In /etc/grub.d 40_custom added:

echo "Adding 40_custom menu entries." >&2
(added after the first line - "#!/bin/bash" - and before the "exec tail -n +3 $0" line.)

 cat << EOF
menuentry "Ubuntu Maverick Meercat Symlink Boot" {
    linux    (hd1,1)/vmlinuz root=UUID=d04d3941-e565-4600-88fb-e80fc335b955 ro quiet splash
    initrd    (hd1,1)/initrd.img
}
EOF

cat << EOF
menuentry "Scientific linux 6" {
    set root=(hd1,6)
    chainloader +1    
}
EOF

After install of new Kubuntu 11.10 the Ubuntu Maverick entry was replaced with one for Kubuntu as follows:
cat << EOF
menuentry "Kubuntu 11.10" {
    linux    (hd1,1)/vmlinuz root=0312dff4-7415-466a-9dee-3b647ae018e5 ro quiet splash
    initrd    (hd1,1)/initrd.img
}
EOF

Now I thought easy, just change the UUID for the newly installed Kubuntu to point to sdb1 and of course the menuentry title :)
However this did not work. Kernel panic on booting.The only way I can boot into Kubuntu 11.10 is from the commandline, i.e.
grub> linux (hd1,1)/vmlinuz root=/dev/sdb1
grub> initrd (hd1,1)/initrd.img
grub> boot
It could easily be that I did stupid things during the install. I chose manual install, selected sdb1, selected 'Change', selected ext4, selected / and selected format. Then selected sdb5, selected 'Change', selected ext4, selected /home and selected format. Of course selected to install mbr to sdb. The install completed without problems, so I don't really understand why I can't boot from Lucid. Maybe I should have deleted the sdb1 and sdb6 Maverick partitions instead of just reusing them for the Kubuntu install ? Boot info script can't seem to find partition #1 for /boot/grub.  Any advice much appreciated.

~$ sudo blkid
/dev/sda1: UUID="c7b41922-ec1c-4be2-b757-ab5407f24fb1" TYPE="ext4" 
/dev/sda5: UUID="1d242549-d40a-4cfb-91be-0e6b390aefdf" TYPE="swap" 
/dev/sda6: UUID="fd389860-8765-4fdc-bf9b-c185b2d55290" TYPE="ext4" 
/dev/sda7: UUID="6d8289a1-9b9f-4f83-9e2d-90ec92fd6040" TYPE="ext4" 
/dev/sdb1: UUID="0312dff4-7415-466a-9dee-3b647ae018e5" TYPE="ext4" 
/dev/sdb5: UUID="a9f3c222-6903-472d-a38e-7563e74c4873" TYPE="ext4" 
/dev/sdb6: LABEL="_SL-60-x86_64-Li" UUID="253aa607-14da-439a-8421-9ebb90073eb4" TYPE="ext4" 
/dev/sdb7: LABEL="SL6_home" UUID="d883cd82-7952-4790-ade9-b4c557a157fb" TYPE="ext4" 
/dev/ramzswap0: TYPE="swap" 
~$ 


~$ sudo fdisk -l

Disk /dev/sda: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00073a79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14647296   83  Linux
/dev/sda2            1824        9040    57962497    5  Extended
/dev/sda5            1824        2073     1998848   82  Linux swap / Solaris
/dev/sda6            2073        6936    39061504   83  Linux
/dev/sda7            6936        9040    16900096   83  Linux

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000223d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2490    19998720   83  Linux
/dev/sdb2            2490       18242   126522369    5  Extended
/dev/sdb5            2490       10461    64020480   83  Linux
/dev/sdb6           10461       12680    17825792   83  Linux
/dev/sdb7           12680       18242    44673024   83  Linux
~$ 

New Kubuntu's fstab..

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=0312dff4-7415-466a-9dee-3b647ae018e5 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=a9f3c222-6903-472d-a38e-7563e74c4873 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=1d242549-d40a-4cfb-91be-0e6b390aefdf none            swap    sw              0       0


Here the boot info script results [http://sharetext.org/BS2E](http://sharetext.org/BS2E)

EDIT. OK now. I had to delete the Maverick partions.

---

