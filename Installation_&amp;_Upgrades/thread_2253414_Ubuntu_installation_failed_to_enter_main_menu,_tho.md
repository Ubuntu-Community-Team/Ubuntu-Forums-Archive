---
title: "Ubuntu installation failed to enter main menu, though windows 7 works fine"
date: 2014-11-19
forum: Installation &amp; Upgrades
---

### Post by ykdang on 2014-11-19
I have a big trouble with my computer. I installed a dual system, ubuntu on HDD2 and windows 7 on HDD1, and used for a long time. Two days ago when I used ubuntu the computer was dead and no longer can enter ubuntu, even from safe mode. But I still can use windows 7 flawlessly. Since most of my work needs ubuntu, I tried to wipe out HDD2 and reinstall. However, all the efforts failed. 
The very strange thing is that every time I use the installation disk, either Ubuntu 14 or old Ubuntu 10, the system only starts for a short while (like 2 minutes) and then the whole system is turned off and reboot. I also tried other disk like CloneZilla but it also failed at beginning. I tried to do a surface check of HDD2 where ubuntu was installed, but no error was found. I tried to swith the SATA port for the two HDDs and no use. I replaced the RAMs from other computers but no help. Overall, I ran out of options but I still cannot let ubuntu to enter the installation menu. I think it shouldn't be a hardware problem since so far the computer gaves no trouble when running windows 7. But why all the disks I used OK before can no longer take me through the installation? 
Do anybody have ideas? Thanks!

---

### Post by irv on 2014-11-19
First, are you installing from a DVD or a USB? Check your BIOS and see if it sees both HDs. If it doesn't you might have to reformat and partition it. That would be a good place to start.

---

### Post by Tom 6 on 2014-11-19
Hi :)  
It sounds like your cd/dvd-drive has gone wonky.  They don't last forever, sadly.  Luckily you can install Ubuntu from a usb-stick so you can bypass the cd/dvd-drive.  Instructions are on the Ubuntu download site.  

Also it sounds like you have been installing Ubuntu inside Windows.  It is better to plug the usb-stick in before you start switching the machine on at all.  With a bit of luck it will boot into Ubuntu from the usb-stick.  You get to a dialogue box with 2 big buttons on it.  First few times trty the "Try Ubuntu" instead of the "install" option.  It should get you to a fairly normal desktop except that it has an icon that lets you install Ubuntu while getting on with other things at the same time.  

The chances are that you need to edit your Bios.  There are guides on how to get into your Bios.  They usually look very ancient, like pre-Win95, and that can be scary but just be sensible and you should be fine.  Most instructions tend to be good and there is an excellent one in the "Community Documentation"  
Regards from 
Tom :)

---

### Post by Impavidus on 2014-11-19
If a previously working system suddenly fails and you can't boot from a live disk, a hardware problem seems likely. Widows accesses the hardware differently than Linux, so it may not use the hardware that causes a problem to Linux. Have you tried with RAM in only one of the slots? Have you tried connecting the Linux HDD to a different computer to check it/make backups? I don't think the HDD is the problem, as that wouldn't explain why the live disk doesn't work.

---

### Post by Mark Phelps on 2014-11-19
You say that the system shuts down in 2 minutes, even running from the installation disks.  Is that 2 minutes after booting the disks? Or, is that 2 minutes after starting the installation FROM the disks?

---

