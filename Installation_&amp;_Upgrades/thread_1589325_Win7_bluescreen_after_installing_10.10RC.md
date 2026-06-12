---
title: "Win7 bluescreen after installing 10.10RC"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by Mythix on 2010-10-06
I installed Ubuntu 10.10 RC this weekend, installation went almost perfect, the partitioning manager in 10.4 installation was a lot clearer imho, and it worked :)

I Think the partitioning went OK, but I can't seem to boot Windows 7 anymore... and the win7 rescue disk does not find any system partitions...
When I select win7 in grub, the windows loading screen comes up for about 2 seconds, and then I get a bluescreen flashing by, and a reboot...
(I'm on an HP Elitbook btw)

Now i've tried a lot of things such as Windows recovery console (bootfix) and Super GRUB, but they did not solve my problem.

Can someone help me with this? :)

Grub windows menuentries:
> ### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 0ade60a2de608831
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set 56766cfd766cdeed
	chainloader +1
}

---

### Post by efflandt on 2010-10-06
Which partition was originally marked as the boot partition (before installing Linux)?  Just because your Win7 is on sda3 does not necessarily mean that it booted that partition.  For example on my Dell sda2 (RECOVERY) was originally marked as the boot partition and that is what boots Win7 on sda3, so maybe you are just trying to start Win7 from the wrong partition.

You might try looking at or posting the output of bootinfo script [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Download it
chmod 755 boot_info_script*
sudo ./boot_info_script055.sh
Paste RESULTS.txt into a reply, highlight that and click # in the message window to put code tags around it.

---

