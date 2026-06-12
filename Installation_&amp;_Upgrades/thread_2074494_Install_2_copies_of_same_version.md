---
title: "Install 2 copies of same version"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by mdavies5 on 2012-10-21
I have 12.04 installed on an SDD drive running fine. I would like to copy this image to another physical drive to use as a test bed for upgrading to 12.10.
I did this using DD to clone the image. I renamed the new partition and gave it a new UUID to remove any conflicts. I then generated grub.cfg.
If I boot into the new image I can see it is trying as, for some reason, it uses a different font to my original image. However, after a pause, it reboots into the original image. I can mount the new image and see all the files, the partition is bootable. Both images have a grub.cfg. Obviously the original one boots first. Does it then read the cfg file from the new image. I amended this to make the new image the default but that still didn't help.
Any suggestions or do I need a separate machine to use as a test bed? I could install from scratch onto the new drive but that rather defeats the purpose of testing updates on my existing image.

---

### Post by oldfred on 2012-10-22
In addition to grub.cfg using UUID, you also mount partitions by UUID. Did you update fstab with your new UUIDs?

# Find your UUID:
sudo blkid -o list

sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab


Above paths are for current install. If you mount from liveCD or other install it may need adjustment as then the different install will be in /media/UUID or label. I like to label partitions so I know what they are. You can use Disk Utility, gparted or command line to add labels.

---

### Post by mdavies5 on 2012-10-22
Thanks oldFred,
In my fstab I use labels instead of UUID:
/dev/sdc3 /mnt/23Ubuntu1210 ext4 defaults 0 0

This works fine when I am logged into the 12.04 version, I can see the 12.10 version ok.
Here is the grub entry generated automatically:
menuentry "Ubuntu, with Linux 3.2.0-32-generic (on /dev/sdc3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos3)'
	search --no-floppy --fs-uuid --set=root 1ce8c238-651a-4e19-a5b4-615d690b797e
	linux /boot/vmlinuz-3.2.0-32-generic root=UUID=675fcd94-7c85-48e7-bc0a-443c0b857401 ro elevator=noop quiet splash $vt_handoff
	initrd /boot/initrd.img-3.2.0-32-generic
}

The root "1ce..." is the guid I generated for the partition.
The UUID "675f..." is the UUID of the boot drive containing the 12.04 version. If I re-installed from scratch I would boot from my sda drive which may solve the problem.

---

### Post by oldfred on 2012-10-23
Unless you have a separate /boot the UUIDs in each Ubuntu boot stanza should be the same. You do not boot from one and load the other. Then fstab may even add more confusion. You need to be consistent. 

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by mdavies5 on 2012-10-23
Via the bios I can boot from the first partition on any drive. Initially I had WindowsXP on SDA1. I used that to install Win7 on SDC1. I then deleted XP and installed Ubuntu 10.04 on SDC3 using SDA1 as my Ubuntu swap file. It seems that Ubuntu wrote some info to SDA1 because I could boot into Ubuntu when selecting SDA1 from the bios. It is not possible to select from the bios any partition >1.
I then bought a new drive and installed Ubuntu 12.04 while it was the only drive plugged in. I wanted to avoid using grub but when I replugged all the drives then grub automatically created it's own menus. My new drive is now SDD1.
When I tried booting from SDA1 it said "no such object <GUID>". I used the uuid quoted and re-identified SDC3. I also modified the grub.cfg on SDC3. It was necessary to put the same GUID in both sections. I can now boot into SDC3 from the bios. By default I boot into SDD1.
I do not need the grub menu but I will now test to see if either allow me to select either version of Ubuntu.

---

### Post by mdavies5 on 2012-10-24
Finally I got 2 copies of 12.04 working on 2 drives. One copy to use as a test bed. As soon as I upgraded to 12.10 it wrecked the boot partitions for the other 12.04 and Windows.
Thanks to G4Linux I restored to my old system of 12.04, Win7 and LinuxMint.
I can boot into any OS from the BIOS or from either grub menu.
My recommendation is always to use a separate machine for test purposes!

---

