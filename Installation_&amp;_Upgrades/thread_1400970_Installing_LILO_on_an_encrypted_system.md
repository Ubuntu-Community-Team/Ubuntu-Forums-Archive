---
title: "Installing LILO on an encrypted system"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by narcisgarcia on 2010-02-07
The scenario: Clean and single hard disk installed with the alternate CD (Ubuntu 9.10) and partitioned manually with:
[LIST]
[*]Primary partition for /boot
[*]Primary partition for encryption
[LIST]
[*]Single volume for LVM
[LIST]
[*]logical volume for swap
[*]logical volume for root (/)
[*]logical volume for /home
[/LIST]
[/LIST]
[/LIST]
For [some reason]("http://ubuntuforums.org/showthread.php?t=1399851") there must be installed LiLo instead of GRUB. I describe here the steps done, once installed the system, the steps done with a Live-CD to install LiLo:

(Supposing sda1 is the /boot and sda2 is the crypt area)

```

# Sure to have LVM amb Crypt software installed and running
sudo apt-get install lvm2 cryptsetup
sudo modprobe dm-crypt
sudo cryptsetup luksOpen /dev/sda2 sda2
sudo vgscan --mknodes
sudo vgchange -ay
sudo pvs # to see the list of LVM groups
sudo lvdisplay /dev/MyGroup # to see the list of logical volumes in a group called "MyGroup"
sudo mkdir /tmp/theroot
sudo mount /dev/MyGroup/MyRootVolume /tmp/theroot
sudo mount --bind /dev /tmp/theroot/dev
sudo mount --bind /proc /tmp/theroot/proc
sudo cp /etc/resolv.conf /tmp/theroot/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot /tmp/theroot
#Then run whatever commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain you mounted the correct partition).
mount /dev/sda1 /boot
apt-get update
apt-get remove grub-pc grub-common
apt-get install lilo
# At this point, edit the file /etc/fstab to change UUID references to traditional references: /dev/sda1 , /dev/sda2 , /dev/mapper/MyGroup-MyRootVolume ,...
# For some reason there isn't /etc/lilo.conf and we need to use a super-simple sample:
cp /usr/share/doc/lilo/examples/conf.sample /etc/lilo.conf
# Now edit the new file /etc/lilo.conf to set ALL the "boot" and "root" parameters according to /etc/fstab
liloconfig # All options to YES.
lilo
#When done:
exit
sudo umount /tmp/theroot/dev
sudo umount /tmp/theroot/proc
sudo umount /tmp/theroot
sudo cryptsetup luksClose sda2

```

...but with the "liloconfig" and "lilo" commands it shows a lot of warnings and the bootloader doesn't install in the MBR. I don't know the reason, and now I've left the LVM & Crypt idea, but I've written this here for somebody that wants to complete the recipe.

---

