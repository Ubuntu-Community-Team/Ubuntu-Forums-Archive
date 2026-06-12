---
title: "Can't see patitions"
date: 2015-10-26
forum: Installation &amp; Upgrades
---

### Post by adrian73 on 2015-10-26
Hello everyone. I decided to install ubuntu 15 in duo boot with windows 10 on a sony vaio model 2013. After I start the installation from usb I can't see my partitions. All my partitions are GPT, security boot disable, fast boot disable. I also format the partition that I want it to install in ext4.If I go to "disks" I can see all the partitions. Why is so hard to install it? Thanks in advance.

---

### Post by yancek on 2015-10-26
Did you turn off hibernation in windows before booting the Ubuntu installation medium?  Did you do a full shutdown of windows?  Which option are you selecting in Ubuntu to install, the manual Something Else option would be the one you want.  Is windows 10 using UEFI?  If so, you need to install Ubuntu in UEFI.

---

### Post by TheFu on 2015-10-26
Welcome to the forums.

Which release?
Did you review the **release notes** for THAT release?
[http://ubuntuforums.org/showthread.php?t=2227580](http://ubuntuforums.org/showthread.php?t=2227580) shows the level of complexity some SONY hardware requires.

SONY computers have a history of being difficult. Websearch  with the exact SONY model to see if anyone has discovered the workaround. I don't think "vaio 2013" is specific enough.

General UEFI install [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by adrian73 on 2015-10-27
It's Sony Svt13124cxs. I followed the instructions from other sony laptop instalation but still not working.

I am installing ubuntu in UEFI mode because I get the screen that shows me "try ubuntu, install...". Any other suggestions?

[http://postimg.org/image/g6kgeb29h/](http://postimg.org/image/g6kgeb29h/)

[http://postimg.org/image/sljei5lo1/](http://postimg.org/image/sljei5lo1/)

---

### Post by TheFu on 2015-10-27
Oldfred normally has the best instructions here for UEFI stuff. Seek out those posts (do not PM unless asked) and review the links.

BTW, installing an OS isn't nearly as difficult as it used to be in the early 1990s, but sometimes the hardware just doesn't cooperate.  After all, Windows comes pre-installed on most things because it is very hard to get a system working - only a vendor with deep knowledge of their hardware and specific drivers gets everything working on most laptops.

---

### Post by Mark Phelps on 2015-10-28
> **adrian73 said:**
> After I start the installation from usb I can't see my partitions. Why is so hard to install it? Thanks in advance.

That's because Win10 enables Fast Startup by default -- and with this enabled, the Linux OS can not see the partitions, since it can't mount or open them.

There are two ways to disable FastStartup in Win10; (1) through the Control Panel, and (2) through an elevated command prompt.

Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup

Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F

In both cases, reboot Windows.

---

