---
title: "Unable to install XP after Ubuntu - Hal.dll error"
date: 2012-07-14
forum: Installation &amp; Upgrades
---

### Post by rizz23 on 2012-07-14
Hi, I am having the "famous" hal.dll problem and I'm unable to solve it like I've read in other threads. Hope you can help me, because it's driving me crazy.

I have a netbook with Ubuntu 12.04 and must install Win Xp for some stupid work reason.

I created a bootable usb pen with the wintoflash tool.

Now i get the hal.dll missing error each time i try to start from the pendrive.
Even in text mode I get a blue page fatal error.

I understand that I should modify my boot.ini file in the pendrive and I tried all the solutions shown in the blog. With no luck\.
Here is my disk config: "win" is the empty partition where I want to install XP.

[http://imageshack.us/photo/my-images/833/screenshotfrom201207141.png/](http://imageshack.us/photo/my-images/833/screenshotfrom201207141.png/)

Please help

---

### Post by dino99 on 2012-07-14
is the first primary partition already used ? (xp needs to get the first :mad: (bill madness)

---

### Post by oldfred on 2012-07-14
Not sure if it is just that you do not have boot flag on sda4 or an issue in the installer?

But Windows only installs to a primary NTFS partition with the boot flag. It looks like you have sda4 formated NTFS but no boot flag. You can use gparted or Disk Utility - Edit partition to set boot flag.

---

### Post by rizz23 on 2012-07-14
Thanks, I'll try that. What should I have in the boot.ini file?

---

### Post by rizz23 on 2012-07-14
Done the flag, but it didn't work.

I guess it's all in the boot.ini file

Mine now has:
[HTML][Boot Loader]
Timeout=10
Default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[Operating Systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="2. GUI Mode Setup Windows XP, Continue Setup + Start XP" /FASTDETECT

C:\SETUPLDR.bs="1. TXT Mode Setup Windows XP, Never unplug USB-Drive Until After Logon"[/HTML]

I'm getting two options: 
1. gui mode setup
2. text setup

in case 1. I get a generic message error: windows cannot start because of a computer disk hardware configuration problem etc
in case I choose 2. I get the hal.dll missing error

---

### Post by oldfred on 2012-07-14
Is that the boot.ini on your flash drive?

rdisk should be drive number, but BIOS usually tells system booting that boot drive is the first or 0. So that may be ok. 

partition should be the partition but first is 1 and you have 2. Did you install to a second partition on the flash drive. If not try 1.

If the boot.ini from your hard drive then partition is 4.

While most installs of Windows are to sda1 or the first drive and first partition, it does not have to be. Windows can install to any primary partition. And second installs can be to a logical partition but still have to have boot files in a primary partition. And often Windows installs to second drives install boot files on the first drive depending on BIOS settings. So often best to install first to sda1, but does not have to be.

---

### Post by rizz23 on 2012-07-14
Ok, i set in the bios boot order
1. local hd
2. usb

I'm starting to boot from usb not hd (the partition is completely empty: there I want to install winXp)

so, now i set my boot.ini like this

[HTML][Boot Loader]
Timeout=10
Default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
[Operating Systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="2. GUI Mode Setup Windows XP, Continue Setup + Start XP" /FASTDETECT

C:\SETUPLDR.bs="1. TXT Mode Setup Windows XP, Never unplug USB-Drive Until After Logon"[/HTML]

I'll let you know, thanks again

---

### Post by rizz23 on 2012-07-14
Not working, neither with rdisk(0)partition(1).

On the pendrive I have only one partition, so it should be right.

I have no clue on how to solve this... 

It can't be that hard to install xp after Ubuntu on a netbook, it's insane

---

### Post by oldfred on 2012-07-14
I have not installed XP for 6 years and that was from a CD.

But I have these links:
Copy Windows XP to usb
Please note this tutorial works on all computers not just the Asus EEE PC.
[http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html](http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html)
USB install of XP
[http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html](http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html)

---

### Post by rizz23 on 2012-07-14
Thanks, I think that will work.

I need to find a win xp pc to prepare the usb: it looks doable but, again, complicated.

Thanks again

---

### Post by sandyd on 2012-07-14
[https://help.ubuntu.com/community/RecoveringWindows](https://help.ubuntu.com/community/RecoveringWindows)

Ignore the part about a wubi install, the instructions should be fine :)

---

