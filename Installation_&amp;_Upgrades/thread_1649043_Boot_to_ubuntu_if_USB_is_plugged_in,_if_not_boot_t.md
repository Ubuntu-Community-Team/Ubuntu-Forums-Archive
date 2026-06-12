---
title: "Boot to ubuntu if USB is plugged in, if not boot to windows?"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by rob__ on 2010-12-19
Hi, this is my first post here. Hope all goes well. 

I'v used windows for too long and wont to make a attempt to move over (though I still need windows).

I just installed lubuntu on an old machine that was running XP and was really impressed in the speed improvement. 

Anyway to my question. As the title says. I wont to boot to ubuntu if I have a usb stick plugged in and windows If I don't. I wont the ubuntu install to be on my (only) HDD in a different partition to windows (windows being partion 2 and ubuntu 4). 

Being a complete beginner to bootloaders I though I would ask here. I was thinking I could do this by having a USB as top priority in BIOS, therefore loading the bootloader on the USB pointing at the partionion on the HDD. If it was not plugged in, windows bootloader wouldn't know the difference and would boot straight into windows.  

Is this possible? I would like to use the newest version 10.10.

I did search for posts before and only found ones linking to dead websites. 

Thanks for any help, Rob.

---

### Post by oldfred on 2010-12-19
Welcome to the forums.

You can do what you mention. I in fact have several USB flash drives set up to boot grub, with additional entries to boot my hard drive or with manual editing boot just about anything.

But it is better to have the boot loader on the same hard drive or USB drive that your install is one. If you have both windows and Ubuntu on one hard drive you just let grub2 boot and it will give you a choice to boot windows or Ubuntu. If you really want windows to automatically boot you can also set that. 

And if you ever want to reinstall a windows boot loader you can do that from a windows repairCD or install a generic windows boot loader from a Ubuntu liveCD.

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Dual drive internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

### Post by rob__ on 2010-12-19
Thanks for links. I'll make I'll look at them in detail tomorrow when I'm on my desktop. 

You said it was better to have the bootloader on the same partition, after a quick flick of the links. I couldn't see why? Sorry if I missed something. 

The main reason I wont this is because I'll have to use windows for say a week then I'll go and use Ubuntu for a few months (or at least that is what I'm hoping). I like to be able to press the power and then go get a drink or something and for other users of my computer that press the power and only know how to get to hotmail it may be a bit much.

At least I now know its possible to do this. I'll make sure everything is backed up and try it tomorrow. 

Thanks again, Rob.

---

### Post by oldfred on 2010-12-19
No, almost never install grub to a partition but to the same drive's MBR master boot record as the install.

You can set it so it defaults to windows with a short timeout (do not set 0 or you have issues), but then you have to be quick to get to Ubuntu.

If you want to install grub2 to some other location than the default sda, the drive most boot from, you have to use manual install. Any of the other choices do not let you choose where to install grub. If you have flash you want to use as boot flash you can have it plugged in during install. I think that may work. I have just installed grub to a flash and manually updated grub.cfg. (Normally you do not edit grub.cfg but my entire grub boot was on flash). You will just have MBR on flash.

If you have Vista or 7, use windows to resize the windows partition and reboot several times for it to run chkdsk and recognize its new size. Then use gparted to create Ubuntu's partitions in the new free space.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by rob__ on 2010-12-19
Thanks for taking the time to sum it up for me I really appreciate it. Yeh sorry about that I meant HDD instead of partition for the bootloader :). 

Thanks for the tips. They will be really useful.

I only have 3 GB memory atm so i'll include some space for swap. 

I already have a separate partition for files, as a windows user it made reinstalling a lot easier (that happened far too much).

Thanks, Rob. (I'll leave the post unsolved encase I come across any problems tomorrow. Might as well keep the same thread)

---

### Post by C.S.Cameron on 2010-12-19
One problem with the "Boot to ubuntu if USB is plugged in, if not boot to win" thing is that a lot of BIOS once set to boot USB first will reset itself to boot internal first the first time the USB is not plugged in.

On some computers BIOS you can press Esc or F12 or something that will give a boot menu.

Otherwise there should be no problem making a USB stick that will boot whatever you want.

---

### Post by thrvers on 2010-12-20
'
maybe you instal bootloader on USB, not on your harddisk.
use [_reinstaling grub2_]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202"), and don't forget location your hardisk [sda or hda]
maybe your USB located on sdb :D

CMIIW

---

### Post by theasprint on 2010-12-20
agree with thrvers

You can install a suitable bootloader to the USB and boot the bootloader.

Its not necessary to install Grub, Chameleon is also good.

---

### Post by rob__ on 2010-12-20
Install was ok just having a problem with my bios now :). It has booted from usb before without this problem. It only boots from the usb if its set at top priority on boot order and it is listed as the first HDD. This is all fine but when I remove it and plug it back in next boot its listed as the second HDD and doesn't boot even though it has top priority which is a bit weird. 

I'll go look though bios settings again and maybe try a different usb. 

Thanks, Rob.

---

### Post by C.S.Cameron on 2010-12-20
You could add your internal drive to the bootloader on the USB and then leave it plugged in all the time, except for those spells you are Windows only.

---

