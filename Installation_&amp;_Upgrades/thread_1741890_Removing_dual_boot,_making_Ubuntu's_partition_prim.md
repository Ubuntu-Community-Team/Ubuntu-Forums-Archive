---
title: "Removing dual boot, making Ubuntu's partition primary"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by hojjat on 2011-04-28
Hello.

I used to have a primary partition where my Windows resided, and an extended partition in which I created the root and swap for Ubuntu. I want to delete the Windows partition, and resize the Ubuntu root partition to span over the whole disk space (except for the 10GB used for swap).

Here is how my partitions look like right now:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190262&stc=1&d=1304015363[/IMG]

Here is the relevant parts of my GRUB config:

```

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-31-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set df03afe0-60d9-499a-a5dd-a203c4376b9d
	linux	/boot/vmlinuz-2.6.32-31-generic-pae root=UUID=df03afe0-60d9-499a-a5dd-a203c4376b9d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-31-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set df03afe0-60d9-499a-a5dd-a203c4376b9d
	echo	'Loading Linux 2.6.32-31-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-31-generic-pae root=UUID=df03afe0-60d9-499a-a5dd-a203c4376b9d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-31-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set df03afe0-60d9-499a-a5dd-a203c4376b9d
	linux	/boot/vmlinuz-2.6.32-30-generic-pae root=UUID=df03afe0-60d9-499a-a5dd-a203c4376b9d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-30-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set df03afe0-60d9-499a-a5dd-a203c4376b9d
	echo	'Loading Linux 2.6.32-30-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-30-generic-pae root=UUID=df03afe0-60d9-499a-a5dd-a203c4376b9d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-30-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set df03afe0-60d9-499a-a5dd-a203c4376b9d
	linux	/boot/vmlinuz-2.6.32-29-generic-pae root=UUID=df03afe0-60d9-499a-a5dd-a203c4376b9d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set df03afe0-60d9-499a-a5dd-a203c4376b9d
	echo	'Loading Linux 2.6.32-29-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-29-generic-pae root=UUID=df03afe0-60d9-499a-a5dd-a203c4376b9d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set df03afe0-60d9-499a-a5dd-a203c4376b9d
	linux	/boot/vmlinuz-2.6.32-28-generic-pae root=UUID=df03afe0-60d9-499a-a5dd-a203c4376b9d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set df03afe0-60d9-499a-a5dd-a203c4376b9d
	echo	'Loading Linux 2.6.32-28-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-28-generic-pae root=UUID=df03afe0-60d9-499a-a5dd-a203c4376b9d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set df03afe0-60d9-499a-a5dd-a203c4376b9d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set df03afe0-60d9-499a-a5dd-a203c4376b9d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 567c82637c823e2d
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

```

I would be grateful if you would provide me with details advice on how to:

(1) Expand the Ubuntu file system to use the first 120 GB (currently unallocated space) as well.

(2) Modify GRUB options accordingly.

---

### Post by oldfred on 2011-04-28
You may be able to do what you want, but you would have to move the extended partition over to include the unallocated, then move / (root) partition start left. 

But then all your partitions will be logical. A few BIOS require a boot flag on a primary partition or they do not let you boot. Grub does not need a boot flag, but windows has to have an active partition. If your BIOS lets you it may work.

But why not just make it /home or just another partition for data? And if anything move / & extended right to make / smaller. You have only used 14GB of 337GB so far.

Moving partition should not change UUID, so grub may still work.
But if you have to reinstall:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Move /home essentially the same just using different copy commands.
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  (create mount may be missing)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by srs5694 on 2011-04-28
AFAIK, most of the BIOSes that require an boot/active flag are Intel BIOSes, so if hojjat has an Intel board, s/he should be concerned, but if not chances are it will work without a boot/active flag. My suspicion is that such a BIOS would be satisfied with a boot/active flag on an extended partition, but I've not tested that hypothesis.

If you've got such a BIOS and marking the extended partition as active/bootable doesn't work, you could convert /dev/sda5 to be a primary with my [FixParts](http://www.rodsbooks.com/fixparts/) program, then resize it.

Creating a separate partition as oldfred suggests is certainly the safest approach; moving the start of a partition is always a bit risky. Unfortunately, the sizes you've got make it a rather awkward split. If I were in your shoes, I'd probably either resize /dev/sda5 or completely reconfigure the system by doing a fresh install to a new ~20 GiB /dev/sda1 with a new primary or logical /home partition, move my existing files over, delete the old installation, and resize /home to fill the remaining space. That's obviously a lot more work, but it's probably a bit safer than resizing /dev/sda5 (provided you're careful with the partitioning!), and with Ubuntu 11.04 just released, if you want to upgrade it's not that much more work than upgrading what you've already got.

---

### Post by IPEX-731BA5DD06 on 2011-04-29
Bah People tend to make it too complicated, I like it nice and simple, if it works and ain't broken, fiddle with it till it is ;)

This link [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome) details how to set up a separate home.

On Dual boot, I had the same, removed windows, I just copied out the data from Windows in Ubuntu 10.04.2 by mounting the windows partition and just cut and paste it to  Ubuntu.

I then used Gparted to remove the windows partition, resize and move partitions about, set up the seperate /home+Data combined partition, Ubuntu 10.04.2 LTS partition, and a Ubuntu 11.04 Beta trial partition.

Its all very easy and straight forward to list again.

1. Copy all data out of windows you want to keep, cut and paste into Ubuntu.
2. Gparted, format windows partition, remove it, make it ubuntu, expand ubuntu, MAKE UBUNTU a primary partition, (boot from Installation CD 1ST)
3. Boot Ubuntu, Grub, it'll update itself, Just flag the /home+Data partitions as Bootable.
4. Of course, you've got a swap file=> Ram installed.
5. Sit back and enjoy the simplicity of it all

I know I've been very simplistic, BUT IT REALLY IS.

REALLY AND TRULY. If I can continuously, break UBUNTU, mess about with Gparted, and run a Dual installation of Ubuntu, ANY ONE CAN. 

P.S. Monkey with a machine gun type of computer user.

---

### Post by hojjat on 2011-04-29
Thanks for all excellent answers. I ended up using the Gparted live disk to resize the extended partition and the root partition (took about 3 hours) and it worked fine for me (probably because my mainboard is not Intel, though I didn't check).

---

