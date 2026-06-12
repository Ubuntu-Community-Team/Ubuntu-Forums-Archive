---
title: "problem with grub2"
date: 2016-04-13
forum: Installation &amp; Upgrades
---

### Post by neil40 on 2016-04-13
I am having trouble upgrading a system it had ubuntu 12.10 9#onit . it has no CD drive and despite  being bios capable refuses to boot from a pendrive.

So I have downloaded an iso and I am trying to boot from it.
This is my 40_custom file

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Ubuntu ISO"{
set isofile="/home/neil/Downloads/ubuntu-14.04.4-desktop-i386.iso"
loopback loop(hd0,1)$isofile 
linuxefi(loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile nopromp
t noeject
initrdefi(loop)/casper/initrd.lz
}


previously I tried linux and initrd as commands

The menu come up but when I chose the option it gives two Can't find command errors on those lines which I have varied as speified above.

Can anyone help please?

---

### Post by Bashing-om on 2016-04-13
neil40; Hello; Welcome to the forum.

I have to question:
1) Is this system a 32 bit system ?
2) Is this system UEFI ?
3) Is this:
> 
linuxefi(loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile nopromp
t noeject

a typo, or is there an unwanted return before "t" ?
4) Is this:
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
the reference you are using ?

Let's see what we can do to get you booting and installed.

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2016-04-13
Welcome. Curious as to why you are not doing a clean install of a supported version [the regular way]("http://www.ubuntu.com/download/desktop/install-ubuntu-desktop"), by downloading the ISO, burning USB or DVD install media and installing? :-k

Unsure why you're going this way. There is no upgrade path from the ancient and unsupported 12.10 to 14.04 LTS, if that's what you're attempting.

---

### Post by neil40 on 2016-04-13
> **Bashing-om said:**
> neil40; Hello; Welcome to the forum.

I have to question:
1) Is this system a 32 bit system ?


No. I don't think so. If it helps it is an  ASUS Eeepc 900. 
> 

2) Is this system UEFI ?


I am unsure. I can't seem to find out. I think I have tried both versions of the code?

> 
3) Is this:

a typo, or is there an unwanted return before "t" ?

No. It is an artefact of the small screen size causing wrap around. The line does not contain a break.

> 
4) Is this:
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
the reference you are using ?


It is one of the things that I have found and does contain the code I have tried.
> 
Let's see what we can do to get you booting and installed.[INDENT][INDENT]together we can
[/INDENT]
[/INDENT]


THANKS!

---

### Post by neil40 on 2016-04-13
> **Bucky Ball said:**
> Welcome. Curious as to why you are not doing a clean install of a supported version [the regular way]("http://www.ubuntu.com/download/desktop/install-ubuntu-desktop"), by downloading the ISO, burning USB or DVD install media and installing? :-k


As I said above it has no CD/DVD drive. It is too small a machine to have one. It won't boot from USB. It is supposed to but it won't I recall years ago when I first put Ubuntu on it that I had a lot of trouble as it would only work with the USB to boot erratically and it steadfastly refuses to boot from the one I have now. I  vaguely recall googling this and finding others had similar problems.

> 
Unsure why you're going this way. There is no upgrade path from the ancient and unsupported 12.10 to 14.04 LTS, if that's what you're attempting.

Yes I know!!. It is an old machine. The screen is broken but I have a use for it now where it will be networked and controlled remotely.
It works OK with an external screen. In fact I made the first posting from it as I needed to copy the files,

---

### Post by yancek on 2016-04-13
If it is an old machine it is highly likely to use EFI since that as only been commonly used for about the last 3+ years.
Your menuentry doesn't look right to me.  You need to be precise and if you are not, you are not going to get any message telling you specifically what to do.  Things that I see which are incorrect if what you  posted is exactly what you have in the 40_custom file are:

after 'loopback loop' you have no space before the (hd0,1)
After 'linux' and before 'loop' you have no space
After 'initrd' and before 'loop' you have no space
On the linux line, your might need the curly brackets around isofile, try it both ways if you want.

All the above are required.  Change it to below.  Also, if you are just planning to use it to boot one time, you could have just put it in grub.cfg but, your choice.

> menuentry "Ubuntu ISO"{
set isofile="/home/neil/Downloads/ubuntu-14.04.4-desktop-i386.iso"
loopback loop (hd0,1)$isofile 
linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=${isofile} noprompt noeject
initrd  (loop)/casper/initrd.lz
}

If it doesn't boot, try moving the iso to the /boot directory but it should work.

---

### Post by Bashing-om on 2016-04-13
neil40; OK ..

This:
> 
ubuntu-14.04.4-desktop-i386.iso

Why use 32 bits on a more modern system ? 64 bit may do the better.

And as this is an older system .. EFI is not a factor and the boot codes:
```

linuxefi(loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noprompt noeject
initrdefi(loop)/casper/initrd.lz


```
do not apply. As given in the reference I use ( above) will work .

Be aware. I tried some while back to install 15.10 (systemd) in this manner, I never did find a means I was comfortable with to "UNmount" the partition I was booting the .iso from . We may have to work real hard on this aspect.

What I do suggest is to download the 64 bit version:
check the md5sum:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Make sure you can boot the .iso in "try ubuntu" mode AND then we see what it will take to install.

[INDENT][INDENT]up for a challenge
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2016-04-13
I do not think that the 32 bit Ubuntu ISO images have efi boot files. The recommendation for UEFI systems is 64 bit Ubuntu.

[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1025555](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1025555)

But you must use a 32 bit ISO image so the references to efi are not going to work. And would someone please show me where in cdimage.ubuntu.com a person can download a Ubuntu 32 bit ISO image of 14.04.4?

If this is Lubuntu then the image name is lubuntu-14.04.4-desktop-i386. According to the Lubuntu web site download page. And according to from where it will be downloaded from.

[http://cdimage.ubuntu.com/lubuntu/releases/trusty/release/](http://cdimage.ubuntu.com/lubuntu/releases/trusty/release/)

Regards.

---

### Post by kansasnoob on 2016-04-13
If you want to try booting from USB again I seem to recall that the Eee's I messed with all recognized USB drives as hard drives. So instead of just setting boot priority to "boot from USB" first I had to open the section in BIOS that said hard drive boot priority. Then from there I could select the USB drive and use either the + and - keys, or maybe the page up & down keys to move the USB drive to the top of the listed hard drives and press F10 to save. I think that's right but it's been a few years.

Booting an iso from grub has limited usefulness anyway because you won't be able to resize mounted partitions and such, so performing a full install could be nearly impossible booting the iso from grub if that's your intention. And I believe I settled for Lubuntu i386 on the Eee's I fiddled with, but I think they were all 1GB RAM so I never tried to find out if the CPU's were 64 bit capable or not.

---

### Post by Bucky Ball on 2016-04-13
> **kansasnoob said:**
> ... instead of just setting boot priority to "boot from USB" first I had to open the section in BIOS that said hard drive boot priority. Then from there I could select the USB drive and use either the + and - keys, or maybe the page up & down keys to move the USB drive to the top of the listed hard drives and press F10 to save. I think that's right but it's been a few years.

That's still it. Sometimes it's the F5 and F6 keys that move the selections. You'll need to hit a key to get to the BIOS, could be F2, could be delete. You may need to check the manual. 

My laptop (different make and model), on the other hand, only recognises the boot order when I bring up the boot device list at boot with F12 and select USB. Seems to take little notice of the BIOS boot order. ... :-k

---

### Post by neil40 on 2016-04-13
> **kansasnoob said:**
> If you want to try booting from USB again I seem to recall that the Eee's I messed with all recognized USB drives as hard drives. So instead of just setting boot priority to "boot from USB" first I had to open the section in BIOS that said hard drive boot priority. Then from there I could select the USB drive and use either the + and - keys, or maybe the page up & down keys to move the USB drive to the top of the listed hard drives and press F10 to save. I think that's right but it's been a few years.

Booting an iso from grub has limited usefulness anyway because you won't be able to resize mounted partitions and such, so performing a full install could be nearly impossible booting the iso from grub if that's your intention. And I believe I settled for Lubuntu i386 on the Eee's I fiddled with, but I think they were all 1GB RAM so I never tried to find out if the CPU's were 64 bit capable or not.

THANK YOU!.

It seems  by altering the BIOS  settings as you describe I **can **boot from my USB stick. I doesn't seem to be working properly but that is maybe what I have on the stick. It is getting quite late here in the UK so I am going to look at this again in the morning.

The eepc came with its own variety of Linux and became unusable because there were no upgrades available. I'm pretty sure  I didn't do this when I installed Ubuntu the first time.

---

### Post by yancek on 2016-04-13
> Booting an iso from grub has limited usefulness anyway because you won't  be able to resize mounted partitions and such, so performing a full  install could be nearly impossible booting the iso from grub if that's  your intention.

You can resize partitions which the iso is not installed on.  The problem for the OP might be that he has only one partition on the  drive which would probably prevent him from installing because he would  need to shrink that partition to have another partition or unallocated  space.     I installed Linux Lite, Zorin and CentOS last week booting the iso directly with no problems with entries similar to that posted above and have been doing this for years.

---

### Post by neil40 on 2016-04-15
> **neil40 said:**
> THANK YOU!.

It seems  by altering the BIOS  settings as you describe I **can **boot from my USB stick. I doesn't seem to be working properly but that is maybe what I have on the stick. It is getting quite late here in the UK so I am going to look at this again in the morning.

The eepc came with its own variety of Linux and became unusable because there were no upgrades available. I'm pretty sure  I didn't do this when I installed Ubuntu the first time.


Can I just add to this a little. There is a quirk I have discovered with the eeepc's BIOS settings. Currently this machine has a broken screen and I am running it with a VGA cable which plugs in to the right hand side of the machine. Further down the right hand side of the laptop that is to say towards the user and away from the screen end of the machine. There are two USB sockets. If I put the USB stick into the one nearest the BIOS cable and the screen. The BIOS gives me the opportunity to set the Hard drive to the USB drive. However, if I put it into the other one It does not. This was very confusing because it looked as if the BIOS had changed. Its menu literally changes to avoid any mention of hard disk boot settings and just treats the USB drive as "external device" or something similar. I forget exactly what.

I am putting this in as a piece off information should anyone else have issues with an ASUS Eeepc 900 and getting grub to work or have problems installing Ubuntu

---

