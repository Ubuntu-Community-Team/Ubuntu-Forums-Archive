---
title: "cannot open root"
date: 2015-11-12
forum: Installation &amp; Upgrades
---

### Post by adrian73 on 2015-11-12
Hello everyone. I have a music server that is using linux system. I try to start it but I get this error:

VFS:Cannot open root device "<NULL>" or unknown-block(8,1)
Please append a correct "root="boot option;here are the available partitions:
Kernel panic-not syncing:VPS:Unable to mount root fs on unknown-block(8,1)


extlinux.conf is:

TIMEOUT 10
DEFAULT vmlinuz root= /dev/sda1
APPEND rootwait raid=noautodetect clocksource=tsc ro idebus=66

fdisk -l is:

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32      410623      205296   83  Linux
/dev/sdb2          410624      469503       29440   83  Linux


some other informations about my boot:[http://paste.ubuntu.com/13236935/](http://paste.ubuntu.com/13236935/)

I tried boot repair but didn't work. Any suggestions?

---

### Post by oldos2er on 2015-11-12
What version of Ubuntu are you running?

---

### Post by yancek on 2015-11-12
Are you actually running Ubuntu or one of its derivatives?
You have syslinux installed to the MBR of sda and as you can see at the top of the boot repair output, it's second stage cannot be found so something definitely changed here.  If you are using Ubuntu, is there any particular reason you do not use Grub2?  Obviously sysinux can be used but it's certainly not the default.

Your post shows two partitions on sdb but the boot repair only shows one but does show two partitions on sda?
Has this server ever worked?  Or is it a new install?  If it was running then some changes must have been made to the syslinux bootloader, intentionally or accidentally.  Did you make any changes just before this happening?

---

### Post by adrian73 on 2015-11-13
[COLOR=#222222][FONT=Verdana]Thank you for your answer. I will try to be short. This is a server with a Linux custom kernel wrote on a 1gb ide flash. Also it has 2 sata ports were you can add 2 hdd with maximum 2TB. Sometime ago I spoke with a friend to modify this kerne[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]l [/FONT][/COLOR][COLOR=#222222][FONT=Verdana]to accept more then 2TB. I don't know how [/FONT][/COLOR][COLOR=#222222][FONT=Verdana]he [/FONT][/COLOR][COLOR=#222222][FONT=Verdana]did it but I can put a 8TB hdd on it. For some reason the server made an update,when I start it I get some errors. Unfortunately it doesn't have a video card and I can't see what's happening. I clone that ideflash [/FONT][/COLOR][COLOR=#222222][FONT=Verdana](withdd command)[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]and put in the pc. It boot[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]s [/FONT][/COLOR][COLOR=#222222][FONT=Verdana]but I get the error described above. Anyway I find that, that update re-wrote the kernel and I can't use hdd more then 2TB. At this moment I am using ubuntu 14.04 (3 months) [/FONT][/COLOR][COLOR=#222222][FONT=Verdana]on the pc[/FONT][/COLOR][COLOR=#222222][FONT=Verdana].I found that the custom kernel is using fdisk. I know that I need to"replace it " with  [/FONT][/COLOR][COLOR=#222222][FONT=Verdana]gnu [/FONT][/COLOR][COLOR=#222222][FONT=Verdana]parted.[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]A [/FONT][/COLOR][COLOR=#222222][FONT=Verdana]few commands on ubuntu terminal [/FONT][/COLOR][COLOR=#222222][FONT=Verdana]a can handle, b[/FONT][/COLOR][COLOR=#222222][FONT=Verdana]uthow can I use the commands for that custom terminal?How can I modify a custom kernel? I have many executable files on that files but I can't open from ubuntu. [/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]That boot file that I share is only with the flash connected to pc, not my main hdd were ubuntu is installed.[/FONT][/COLOR]

[COLOR=#222222][FONT=Verdana]I like ubuntu for it's speed but is so hard to learn it.[/FONT][/COLOR]

---

