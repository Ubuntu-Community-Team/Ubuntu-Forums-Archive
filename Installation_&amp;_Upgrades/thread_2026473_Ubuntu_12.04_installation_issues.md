---
title: "Ubuntu 12.04 installation issues"
date: 2012-07-15
forum: Installation &amp; Upgrades
---

### Post by mswaminathan on 2012-07-15
I installed ubuntu 12.04 on my hplaptop dv6000 from a usb flash. This laptop previously had two partition one with Ubuntu 10.04 and another one with Windows vista along with recovery partitions. 

When I installed 12.04, I selected to wipe out all the existing OS and install 12.04.

After the installation when I tried to restart the system is not booting up from the hard drive.

Here is the report url  from boot-repair:

[http://paste.ubuntu.com/1093207/](http://paste.ubuntu.com/1093207/)

Appreciate any help.  Thanks for your time.

---

### Post by darkod on 2012-07-15
No partitions on the hdd are even recognized. This might be due to an error or corruption in the partition table, or similar.

Try to run fixparts on the disk, to see if it repairs something.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

If you are happy to delete your vista too, you can also consider writing a new empty partition table on the disk and start from scratch.

If you do need vista, and fixparts can do anything, you can try testdisk for recovering the correct partition table.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by OM55 on 2012-07-15
Here is another thing you can try:

Boot with Gparted ([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)) to see if you have any visible partitions. Ubuntu will typically create two partitions - a Linux Ext4 partition and a Swap partition.
- If you see those two partitions, you may only need to recreate the Grub2 MBR (see explanation below).
- If you don't see any partitions, you may have a faulty partition table. Just erase the existing partition table, create a new one (from the menu) and then exit and try to reinstall Ubuntu again

To recreate the Grub2 MBR:

1. Boot with Ubuntu Live CD (or USB)

2. Open terminal (command prompt)

3. Type: sudo fdisk -l

You will get a list of partitions, similar to the following list:

/dev/sda1 13 102400 de Dell Utility
/dev/sda2 * 13 1926 15360000 7 HPFS/NTFS
/dev/sda3 1926 30892 232676566 7 HPFS/NTFS
/dev/sda4 30893 60802 240245761 5 Extended
/dev/sda5 30893 59584 230467584 83 Linux
/dev/sda6 59585 60802 9777152 82 Linux swap / Solaris 

Ubuntu partition is the one with the name "Linux" (not necessarily the one with the star, although could be).
On this case is on '/dev/sda5' so we have to mount it:

4. sudo mount /dev/sda5 /mnt
   (replace 'sda5' with the partition name in your case)

5. And then install grub:
   sudo grub-install --root-directory=/mnt /dev/sda

6. Reboot (remember to remove the bootable CD or USB after shutoff completes) and verify that all is working fine.
You can do so also by: sudo reboot

Explanation: 
A) When Ubuntu installer finds an existing partition table, it will try to make the changes to it. If the partition was non-standard or had some previous issues, the result may be a corrupted partition table. So also the Linux partitions were created and installed, there is no way to access them with the corrupt partition table.
With Gparted you remove the old partition table and create a fresh one, then do again the Ubuntu installation that this time will be accessible.

B) On occasion, the Grub2 MBR (first program loaded and run from the hard disk - in our case the Grub2 'menu') was corrupt or missed. But if you see the partitions on the hard disk, you can simply re-create the Grub2 menu using the command above.
If you need later on to customize this menu, you can use Grub Customizer (google it), but since you mentioned you intended to install Ubuntu as the only system, you will probably not need it.

---

### Post by YannBuntu on 2012-07-15
Hello

Darkod +1

**@OM55:** the Ubuntu partition can't be read, so it's impossible to reinstall GRUB now.

---

