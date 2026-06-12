---
title: "Installed Ubuntu alongside Win7 but no grub?"
date: 2012-09-10
forum: Installation &amp; Upgrades
---

### Post by ftornell on 2012-09-10
Hi, just installed ubuntu 12.04 LTS on a computer with win7.
I did a separate partition for "/" and "swap" but now when I restarted the computer no grub menu is displayed, it just booting up win7...

How to fix?

---

### Post by OhThatSysOp on 2012-09-10
I dual boot WindowsXP and openSUSE. I still use ubuntu 12.04 on a D600 laptop.
Normally, when Windows boots, it puts its boot manager in the MBR, the space on the hard drive that is reserved for programs that know what they are doing.
the GRUB (or LILO) is actually on a partiton, and, therefore isn't considered worthy of booting to Windows. You can try putting the GRUB in the MBR, but I don't reccomend it.
In Windows, if you muck through control panel, you can find a setting activating the graphic boot manager.
I use XP, and I don't have a problem. I choose what to boot every time.
OpenSUSE is very easy to control. I turned off the GRUB boot and Windows did it for me.
Nice and easy.
I hope I helped you.
-OhThatSysOp

---

### Post by ftornell on 2012-09-10
Hi,
I have installed older versions of ubuntu alongside windows7 before but 12.04 seems to have a glitch on my system.

---

### Post by darkod on 2012-09-10
Do you have more than one disk? Grub2 might be on the other disk, so windows bootloader is booting windows directly because it can't boot linux.

Where did you select to install the bootloader during the ubuntu installation?

---

### Post by ftornell on 2012-09-11
> **darkod said:**
> Do you have more than one disk? Grub2 might be on the other disk, so windows bootloader is booting windows directly because it can't boot linux.

Where did you select to install the bootloader during the ubuntu installation?

Hi, I have three disks, so that might be the issue here.

First I choosed to install alongside win7 (the installer choosed to resize on of the other disks not the one with windows 7 as I was hoping for.

I re-ran the installation and did go for manual partitioning, choosing the "/" and "swap" partition on the same physical disk as Windows 7.

How can I reinstall grub then on the same disk sda as both win and linux is on...?

---

### Post by darkod on 2012-09-11
Use the ubuntu cd in live mode and follow these instructions:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by ftornell on 2012-09-11
This is what I should go for? (with my disks ofcource)

How to restore the Ubuntu grub bootloader (9.10 and beyond)

First you need to find out what your drives are called. You can do this by going to a terminal and typing:

Code:
```
sudo fdisk -l
```
From that you need to find the device name of your Ubuntu drive, something like “/dev/sda5&#8243;.

So, still in the terminal, type:
Code:
```
sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
```

And then, to reinstall the grub:
Code:
```
sudo grub-install --root-directory=/media/sda5 /dev/sda
```

---

### Post by darkod on 2012-09-11
Yes.

Instead of sda5 use your root partition and in the last command leave it as /dev/sda since that's where you want grub2 installed.

---

### Post by ftornell on 2012-09-11
so this is might be it...

```
sudo grub-install --root-directory=/boot /dev/sda
```

---

### Post by darkod on 2012-09-11
I don't understand the last post. You still haven't done this?

No, it's not --root-directory=/boot as in your last post. Where did you see that in the instructions?

The previous post was correct except that you need to replace sda5 with your root partition.

Do you know which one is your root partition? And whether or not you have separate /boot partition?

---

### Post by ftornell on 2012-09-11
got it, thx!

---

