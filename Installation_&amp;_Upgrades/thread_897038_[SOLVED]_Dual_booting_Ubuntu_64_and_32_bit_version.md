---
title: "[SOLVED] Dual booting Ubuntu 64 and 32 bit versions"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by 73ckn797 on 2008-08-21
No one has replied to my last posts about this topic (stated differently before).

Will a dual boot of 8.04 64 and 32 bit versions work? I am about to find out but would like some feedback.

You may ask "Why?" and the reason(s) are really few. If I can get several issues working with the 64 bit I will wipe the 32 bit. That simple!

---

### Post by ggaaron on 2008-08-21
I will ask 'Why do you think that it won't work?'. I can't think of anything that would prevent you from using two or more independent operating systems on one computer. Good luck=)

---

### Post by Sef on 2008-08-21
> If I can get several issues working with the 64 bit I will wipe the 32 bit.

What are the issues?

---

### Post by 73ckn797 on 2008-08-22
The primary issue is with a Java applet. My work requires photo uploads daily and one source uses Aurigma Image Uploader. The system prompts for Java and when I select the prompt to get a package there are 4 choices. I have not been able to get any of those chioces to work under the 64 bit version. I have done further reading and believe that the Icedtea Java may be the cure. Many posts regarding this issue were older and a more recent one stated that by now or in a couple of months that there will be something available that will fix the problem.

I really did not think that installing another OS would be a problem. What I do find is that the selections for which drive to install on do not show the ext3 partition I created on the drive where I have XP. My second drive is dedicated to Ubuntu 32 bit and running great.

If XP gets over-written, I will not consider it much of a loss. I have backed up my necessary data to a 3rd drive and it is also in the 32 bit environment.

---

### Post by 73ckn797 on 2008-08-22
I am a newbie to the Linux OS's but not afraid to figure things out. I have learned much with computers over the years by trying things, craching a system and then figuring out what I did and how to fix things. I will, and have, already experienced that with Ubuntu but mostly on the booting with XP.

I ask because I need/want to know before I screw things up. Otherwise I can try it and see what happens. It is not like I cannot reload from scratch if necessary.

---

### Post by ggaaron on 2008-08-22
Probably nothing will break=) And yes you are right - OpenJDK and IcedTea do run on 64 bits, OpenJDK is now Ubuntu's default, I think you need gcj-plugin to make it work in Firefox.

---

### Post by 73ckn797 on 2008-08-22
I just installed the 64 bit and it over-wrote the XP drive completely. OH Well, no big loss.

When the system boots there is only the old boot screen for Ubuntu 32 bit and the XP is still listed. I have Super Grub. Should I run that to fix the boot process so that I can bual boot to 32 or 64 bit? I ran it the other day to make Ubuntu the default system but then XP would not load when selected. That is another issue that is now a moot point.

I am about to leave for work so I may not be able to reply back for several hours.

Thanks for your input.

---

### Post by ggaaron on 2008-08-22
You don't specify where did you install the new grub. MBR, partition with 64bit? You could install grub on partition with 64bit and set chainloader in main grub.

Add chainloader to grub conf:
title Ubuntu GNU+Linux
rootnoverify (hd0,6)
chainloader +1

Run grub in command line
grub> root (hd0,6)    (Specify where your /boot partition resides)
grub> setup (hd0,6)     (Install GRUB in the /dev/sda6)
grub> quit            (Exit the GRUB shell)

Remember to get those numbers right hd0 will probably be good as it will point to first drive - probably sda. Note that sda1 is hd0,0 as grub numbers partitions from 0 up.

---

### Post by 73ckn797 on 2008-08-22
The install for the 64 bit never gave an option for the Grub location.
I believe that the Super Grub put Grub on the second drive prior to me loading the 64 bit system. I have all weekend to figure this out.

The 64 bit loaded on sda1. I would assume that the second drive with the 32 bit is hd1/sdb1?? The 32 bit is the only option besides having the XP still listed. It is loading without problem and that is where I am operating now.

---

### Post by ggaaron on 2008-08-22
hd1, hd2 and so on are physical drives, hd1,0 hd1,1 are partitions. Ubuntu gives option to install/not install/where install boot loader just before launching installation in advanced settings. If you know on which drive you've installed 64 bit you can install grub manually on this partition with above commands and then add option to global grub to run the second one. This way you'll get two independent boot loaders that can be auto updated by apt to match your newly updated linux.

---

### Post by 73ckn797 on 2008-08-22
The 64 bit was loaded onto the hd1 (typical C drive?) and the 32 was already on hd2 (D drive). The install wanted to repartition hd2 where the 32 is installed. I designated hd1,1 (correct?) where I created a 100gig partition with XP on the remaining hd1,0? 150gig space.

Bear with me in this, please. I will be able to more fully get into things later today.

---

### Post by sandysandy on 2008-08-22
i have dual booted 32 bit and 64 bit with no problem whatsoever. the 64 bit ubuntu was able to pick up the other OS (7 in all) with no problem.

post output of [COLOR="Blue"]sudo fdisk -lu[/COLOR] and 

[COLOR="Blue"]gksudo gedit /boot/grub/menu.lst[/COLOR] of both 32 bit and 64 bit ubuntu.

u can manually make entry for XP in 64 bit ubuntu.

regards

---

### Post by ggaaron on 2008-08-22
Manually adding 64bit to grub will have side effects when you upgrade linux. C and D drives have nothing to do with the real drives=) Output of fdisk will help.

---

### Post by sandysandy on 2008-08-22
> **ggaaron said:**
> Manually adding 64bit to grub will have side effects when you upgrade linux. C and D drives have nothing to do with the real drives=) Output of fdisk will help.

can u amplify on that. :)

as long as u keep the 64 bit linux entry (which is added manually to 32 bit ubuntu's menu.lst) outside (above / below) the AUTOMAGIC KERNEL LIST of the 32 bit's menu.lst i presume it should not matter when u upgrade the 32 bit linux.

regards

---

### Post by 73ckn797 on 2008-08-22
Thanks. I have run the commands and printed them out and will study things. The current Grub reads as follows:

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5fc47a15-7d16-40db-b97f-a9f8c11b26f3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5fc47a15-7d16-40db-b97f-a9f8c11b26f3 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Microsoft Windows XP Home Edition
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


The only problem is that when I installed the 64 bit, it completely reformatted hd2 to the full 250 gig size and installed. I could care less about losing XP but would like to boot to either Ubuntu version. Maybe my studying will figure out how to edit the Grub. Or you could make a suggestion and I will look things over. The first entries are the 32 bit Ubuntu. There appears to be no 64 bit version written into the Grub. Would Super Grub fix this?

---

### Post by 73ckn797 on 2008-08-22
Here is the fdisk info:


Disk /dev/sda: 40.0 GB, 40020664320 bytes 
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0x9b230d97 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *          63    61769924    30884931    6  FAT16 
/dev/sda2        61769925    78156224     8193150    f  W95 Ext'd (LBA) 
/dev/sda5        61769988    78156224     8193118+   7  HPFS/NTFS 

Disk /dev/sdb: 160.0 GB, 160041885696 bytes 
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0x00000001 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1              63   300431564   150215751   83  Linux 
/dev/sdb2       300431565   312576704     6072570    5  Extended 
/dev/sdb5       300431628   312576704     6072538+  82  Linux swap / Solaris 

Disk /dev/sdc: 250.0 GB, 250059350016 bytes 
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0x67d43a77 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1              63   476311184   238155561   83  Linux 
/dev/sdc2       476311185   488392064     6040440    5  Extended 
/dev/sdc5       476311248   488392064     6040408+  82  Linux swap / Solaris 




This will help me figures some things out, most certainly.

Thanks!

---

### Post by ggaaron on 2008-08-22
> **sandysandy said:**
> can u amplify on that. :)

as long as u keep the 64 bit linux entry (which is added manually to 32 bit ubuntu's menu.lst) outside (above / below) the AUTOMAGIC KERNEL LIST of the 32 bit's menu.lst i presume it should not matter when u upgrade the 32 bit linux.

regards

32bit will be fine, but 64 bit won't get automagic kernel list you've just mentioned=)

---

### Post by ggaaron on 2008-08-22
OK, first thing to try - remove XP from grub menu, add this lines:
title Ubuntu GNU+Linux
rootnoverify (hd2)
chainloader +1
save, reboot, try if it doesn't work try the second option:

Second option.
Add this to menu.1st:
title Ubuntu GNU+Linux
rootnoverify (hd2,0)
chainloader +1

remove the XP section.
run sudo grub in command line issue this commands (without grub> prompt and comments in brackets):
grub> root (hd2,0) (Specify where your /boot partition resides)
grub> setup (hd2,0) (Install GRUB in the /dev/sda6)
grub> quit (Exit the GRUB shell)

---

### Post by 73ckn797 on 2008-08-22
The boot list I sent earlier was not the correct one. I was loading and editing the grub/menu.lst from sdb1, the 32 bit version. The system is booting from sda1 where the 64 bit was installed. The 64 is the first selection that comes up and I receive error 17.

Here is the menu.lst from sda1:

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=03b59aa8-708f-4382-a895-2199d17b4245 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=03b59aa8-708f-4382-a895-2199d17b4245 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5fc47a15-7d16-40db-b97f-a9f8c11b26f3 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5fc47a15-7d16-40db-b97f-a9f8c11b26f3 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


What do you think?

---

### Post by ggaaron on 2008-08-22
Looks quite correct - you say that you can boot into 32bit version? I'd change this option to chainloader but match it to your taste. As for 64bit you can try to remove ',0'. Actually you don't have to do this in config - you can do this during boot, press e to edit an entry in grub, e again to edit a line and then b to try booting.

---

### Post by 73ckn797 on 2008-08-22
One correction to my last comments: The 64 bit is on sdc not sda.

What do you mean by match it to your taste?

I will check the info again in grub.

---

### Post by ggaaron on 2008-08-22
As I've posted before you can make one grub point to the other one or add entries for the second system into first grub manually. If you have two grubs - then you just have two of them, could be annoying, but I run this setup and it's ok for me, if you have one grub, then you can only take advantage of one automagic kernel list. You can choose which approach you like more.

---

### Post by 73ckn797 on 2008-08-22
Success!

Though the info you gave was correct I was confused on the sda/hd0 relationships. I went to gparted and the list showed the 64 bit drive as sda and the 32 bit drive as sdb. I boot up and edited at the boot menu designating the 64 drive hd0. That finally got the system to boot to the 64 bit version. I also played around with Super Grub to get the GRUB on the hd0 drive.

The fdisk info ( shown in earlier post reply) displayed the drive as sdc but later, probably after running Super Grub (I guess) the drive assignments were different. That was when I realized sda/hd0 was the correct location.

Thank you very much!

Consider this thread SOLVED. However that can be done.

---

### Post by ggaaron on 2008-08-22
Nice to hear that you managed to get this to work=)

---

### Post by 73ckn797 on 2008-08-22
I believe I mentioned earlier that I play around and do figure things out. I am not afraid to try. After all, my important data is backed-up so if I have to reload or monkey around, that is what I have to do.

---

### Post by drumstyx on 2009-01-11
i know this post has been around forever, but did the 32 bit OS solve your problem? cause i may have similar problems...but i'm not sure if it's from the 64 bit OS

---

