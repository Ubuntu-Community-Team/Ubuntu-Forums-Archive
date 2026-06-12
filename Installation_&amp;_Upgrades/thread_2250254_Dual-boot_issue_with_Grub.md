---
title: "Dual-boot issue with Grub"
date: 2014-10-27
forum: Installation &amp; Upgrades
---

### Post by massimo-mangiola-13 on 2014-10-27
I am new to Ubuntu, so don't be surprised if I don't understand something that should be obvious. 

I've decided to install Ubuntu 14.10 alongside Windows 8.1 (dual-boot) on both my desktop and laptop. On my desktop, it worked perfectly; I made the live USB, installed it, everything's okay.

With my laptop, however, it doesn't seem to cooperate. The first problem is that it didn't recognize that I have Windows 8.1, only giving me the option to erase everything or 'something else'. So, I made a new partition for Ubuntu (with the swap area) so I can have both. I installed it, and when it finished I went into BIOS to switch the boot settings back to normal. After a reboot, it just went straight to Windows, not showing Grub. I don't know why; I used the same USB to install for both my desktop and laptop, yet my laptop gives me trouble. I've tried reinstalling Ubuntu, nothing changed. Heck, I even made a new live USB, which also changed nothing. I am trying to install the 64-bit version, so can that be an issue?

Is my problem connected to Ubuntu not recognizing Windows? If yes, how can I make Ubuntu recognize it? If no, do I have to do something to the partitions? Sorry if I'm not detailed enough, once again I am new to this. 

Note: I've tried using the Boot-Repair ISO, but whenever I boot it, it just gives me a black screen. Any help on that would be appreciated.

Thanks in advance.

EDIT: I have quite a few partitions, (all backups and recovery partitions, they were there when I got the laptop), so that could be part of the problem. I don't even know what certain ones are for (I have a 300 megabyte partition with absolutely nothing on it. Is it okay that I get rid of the other ones? I already backup my drive regularly, so I don't necessarily need them.

---

### Post by yancek on 2014-10-27
If your windows 8 was pre-installed it is probably using UEFI/GPT to boot and you need to install Ubuntu using UEFI/GPT.  Did you do that on both the Desktop and laptop?  Using the 64bit version should not be an issue.  If you have windows 8 I expect your hardware is 64bit capable.  It may help if you have a Fast boot option in the BIOS to disable it.  You could try running the boot repair script without making any changes, but just to get its output to post here.  Instructions on using from the Ubuntu installation medium are at the link below.

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

