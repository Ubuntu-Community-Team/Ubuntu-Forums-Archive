---
title: "Ubuntu 14.04 + Windows 8.1 Grub not showing (Boot-repair didn't work)"
date: 2017-01-23
forum: Installation &amp; Upgrades
---

### Post by glaux2 on 2017-01-23
Have been using Ubuntu 14.04 + Windows 8.1 for a quite a while now and everything was ok. Yesterday I decided to clean up my ubuntu system with Ubuntu Cleaner Computer Janitor. I did already several times on this same system with no problems. So I've cleaned everything I was offered. There were no signs of problems during this process. Then I rebooted to Ubuntu again and this first reboot was also alright. Then in the evening I rebooted to Windows and at the night time there supposed to be my scheduled (Acronis) system backups running. So this morning I see my windows system freezed, I reboot and I don't see any Grab loader, just Windows system loading and no choice. 

So I've downloaded `boot-repair-cd` and created boot usb-drive. Booted from it successfully and run through all the process of *Recommended repair*. There also seemed to be no problems with that but nothing has changed after it. Still only Windows loading with no choice.

[So here is my log]("http://paste.ubuntu.com/23850068/")

---

### Post by ajgreeny on 2017-01-23
Did Windows do any other major updates at the time it was running?  I do not use Windows any more but I believe any updates involving the Windows bootloader system can overwrite grub meaning Ubuntu will no longer boot.

See **Boot-Repair** in my signature below and follow the instructions there only to run the Boot-Info-Script.	 **Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by yancek on 2017-01-23
My understanding is that some windows updates will turn on fastboot which can cause problems.  You don't mention doing any updates but just a backup from windows with windows software which failed (frozen).  Are you booting from the second/smaller drive?  Is the first drive just data?

---

### Post by glaux2 on 2017-01-23
hi guys,

I've found this in the end of my log file
> For example you can boot into Windows, [COLOR=#AA22FF]**then **[/COLOR][COLOR=#AA22FF]type [/COLOR]the following [COLOR=#AA22FF]command [/COLOR]in an admin [COLOR=#AA22FF]command [/COLOR]prompt:
bcdedit /set [COLOR=#666666]{[/COLOR]bootmgr[COLOR=#666666]}[/COLOR] path [COLOR=#BB6622]**\E**[/COLOR]FI[COLOR=#BB6622]**\u**[/COLOR]buntu[COLOR=#BB6622]**\s**[/COLOR]himx64.efi

So I've tried it and it worked. 
But I'm still curious what have happened and how I can prevent it from happening again...

> Did Windows do any other major updates at the time it was running?

No, I handle all the Windows updates myself, there are no automatic updates.

> Are you booting from the second/smaller drive? Is the first drive just data?

I don't understand the question. I have two drives. One is for both Win and Ubuntu and the second one it for data. But the second one have nothing to do with my situation I guess.

---

### Post by ajgreeny on 2017-01-23
Great news! 
Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by yancek on 2017-01-23
> I don't understand the question. I have two drives. One is for both Win  and Ubuntu and the second one it for data. But the second one have  nothing to do with my situation I guess. 		

If for some reason the larger drive had been set to first  boot priority, you would not have been able to boot.  Just wanted to verify that was not the case.  Glad you got it working.

---

