---
title: "Please help to separate dual boot hard drives after the fact"
date: 2013-07-13
forum: Installation &amp; Upgrades
---

### Post by Luxx on 2013-07-13
I never expected this to be a problem. I have separated drives in a dual boot before and didn't have an issue, but maybe that was because it was GRUB legacy and WIndows, or Lilo. Now I have two hard drives that boot with GRUB2 and I can't seem to separate them, as in take one out of the computer and put it in a separate computer.

I have tried installing GRUB to the other drive several times, and sometimes it works. I can unplug the first drive and boot into the second alone, but then the first drive won't boot when it's plugged in and on it's own. 

It kind of bothers me that GRUB2 assumes that if an OS is installed on a second hdd, that hdd is meant to live in that computer with the first one forever. Whose thinking was this? Most Linux distros allow a hdd to be taken out of one computer and put in another one, even with different architechture, and it just works. So why does GRUB2 behave as though multiple drives in a computer must be mated for life? Makes no sense. Also, what about RAID? What if one drive fails and you need to boot with another drive? Things change, break, etc. It seems to me independent boot records on each drive just makes sense.

How can I get each drive to boot on it's own without wiping out the other drive's boot record?

Limitations:
I do not have a CD/DVD burner.
I do not have a USB stick that can be made bootable.
There is no "LIVE" boot disk, unless an ISO can be mounted from one of the installed drives, which may be a possibility.
I am not installing a "NEW" OS. GRUB preferences cannot be selected from the intitial installation options.\

Currrently, Ultimate Edition is on /dev/sda & Ubuntu12.04 is on /dev/sdb, but since reinstalling GRUB to sdb, sdb is the one I am booting from.
I am not afraid of the command line or researching something further to understand how it works. I have looked through the GRUB2 manual several times and I am not finding a solution. I could be missing something. There was a GUI option I tried, which helped clean up the GRUB menu list, but did not help with independent boot. I tried some of the dual boot soltutions I found on the internet, including in these forums, but they didn't help for my particular setup. With my last attempt I did get a grub rescue prompt and was able to locate partitions. etc. but wasn't able to get beyond that. I found two articles describing how to get to boot from there. but a step was missing or I didn't understand something in those. Grub rescue may be a place to start.

Much gratitude to anyone who can help me resolve this. Thanks.

---

### Post by windows2003 on 2013-07-13
Hi, 
I not understand the question!
You have 2HD's into one notebook and you don't want that you need to chose by grub or other bootloader, and sometimes you want to put a 3 hd into it with other OS???

I do this, but when you install just put for installation only 1 HD into computer install you linux distro and then after install you can put a second HD ( who was allready installed with other OS)into it. But then you need to go into the BIOS from your pc and go to the tab "MAIN" and there activate Boot menu option. When you start PC, you will probally need to press F12 then there comes a menu from the bios and he let you chose wich HD you want to start! 
I never use the bootloader from linux or microsoft to let me chose what I want to run, always use mine Bios and this works perfect! If you use the software bootloaders, and you begin to mix with other HD with other Operating systems, then you ask one of this days for trouble...!

---

### Post by Luxx on 2013-07-13
I only have 2 hard drives. Each hard drive has an Ubuntu-based operating system that uses GRUB2 as it's boot loader. 
It is a custom built desktop computer, not a notebook.
The drives already have operating systems installed and I do not want to change them or add any more. I just want each one to boot separately from the other. 

The BIOS menu does not help.  If I choose the drive that does not have grub loaded on it, it wll not boot. 
I have installed grub on both drives, but when I install grub on one drive it removes it from the other.
I want grub to STAY on both drives.

I can boot the drive that does not have it's own grub menu from the drive that does, but this is not independent and will only work if I let the computer boot from the dominant drive and select the other drive from that drive's grub menu, so both drives have to be plugged in for the non-dominant drive to boot at all.

Again, I need them to each be able to boot ALONE because I am taking one hard drive out to put it in another computer.

---

### Post by windows2003 on 2013-07-13
<I have installed grub on both drives, but when I install grub on one drive it removes it from the other.> => I think this is normal, you need to unplug the other HD, so that every hd has is own bootloader and don't know about other hard-disk.
Then try first start them 1 by 1, but still one unplugged! If this works, then you can plug them back both in, and then you start with bootmenu from BIOS, not the bootmenu grub who let choose you what you want to start!

This should work or there is something else...annyway this works here on mine computers like that.

---

### Post by Luxx on 2013-07-13
That is the theory, and that's what I'm trying to do, but it's not working.

When logged into /dev/sda I install grub to /dev/sdb, shut down, remove /dev/sda, and reboot with just /dev/sdb plugged in and it boots fine. I update grub, and all should be well.

But then I plug in /dev/sda and remove /dev/sdb and /dev/sda will no longer boot at all. This is the drive that WAS booting in the first place.
The last time I tried it I got a grub-rescue prompt, which seemed to be an improvement from previous attempts, but I can't get past grub_rescue.

I understand that this is "normal" behavior, but it escapes me WHY this would be the default behavior when previous bootloaders more easly allowed individual boot from multiple drives and there is still a need to be able to do so.

Selecting from the BIOS menu does not help in this scenario. Each drive needs to have it's own bootloader. I can choose the drive in the BIOS menu as long as both drives are plugged in, but as things are right now, /dev/sda is still booting from /dev/sdb's grub. It cannot boot on it's own. So, if I put it in another computer by itself, which is the goal here, it will not boot.

---

### Post by ajgreeny on 2013-07-13
You need to boot to sda and run ```
sudo grub-install /dev/sda
sudo update-grub
``` then boot to sdb and run ```
sudo grub-install /dev/sdb
sudo update-grub
```
That will ensure that sda uses the grub configuration from sda and sdb uses the configuration from sdb.

Your problem results from what you said here "When logged into /dev/sda I install grub to /dev/sdb" which means that the grub bootloader on sdb is dependent on the configuration on sda, so of course, when you separate the drives no configuration is present, and grub rescue appears.

---

### Post by Luxx on 2013-07-30
Oh my goodness... I had read on one of the tutorials online that you should never try to install GRUB on the drive you are using.

Of course once I did it the way you suggested, it's all working fine.

---

