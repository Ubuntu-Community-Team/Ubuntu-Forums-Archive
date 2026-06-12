---
title: "Fresh Installation prob: udevd-event[1477]"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by hannah187 on 2008-05-12
Hi
I just bought a brand new Laptop. Toshiba Satellite Pro L300: Model PSLB1A. It came with Vista Basic install so what can I do. Well what every good man will do. Erase vista and install Ubuntu. That's exactly what I did. Did a fresh install of Hardy (32bit) from my alternate CD (this Cd is good as I had made many installations with this CD). The laptop failed to boot. Following is the error message I am getting.

udevd-event[1477]: run_program: '/sbin/modprobe' abnormal exit

the blinking cursor is sitting after:

(initramfs)

any guidence please

---

### Post by housam on 2008-05-12
Reformat the HDD manually using the Gparted tool ( on the live CD - or download the newer version and burn it to a cd to make it bootable) and then create the needed partitions for installing Ubuntu. during the installation process choose the manual way and assign the partitions manually.

---

### Post by hannah187 on 2008-05-12
> **housam said:**
> Reformat the HDD manually using the Gparted tool ( on the live CD - or download the newer version and burn it to a cd to make it bootable) and then create the needed partitions for installing Ubuntu. during the installation process choose the manual way and assign the partitions manually.

Interesting that you mentioned that. That’s exactly what I have done. Let me explain.

This Laptop came along Vista basic pre installed. So I started the computer with my 7.10 Live CD. Started gparted at the terminal. This is what I did with gparted.


Create 2 NTFS partition. 1 Swap and 4 ext3 partition (120GB HDD). Installed WinXp on the first NTFS partition and then tried installing Ubuntu 8.04 with my alternate CD. While installing the only thing it could not find is the Network Device. And then finished installing. 

When I now start my laptop and boot 8.04 I get the error as mentioned at the beginning of this post. WinXP is however working fine. 

BTW: I had to change SATA AHCI to Compatibility in order to install XP (in BIOS). I need to keep in this mode otherwise XP won’t boot up.

---

### Post by ndstate on 2008-05-13
Hello,

I am getting a similar error on my new Toshiba A305

```
udevd-event[1567]: run_program: '/sbin/modprobe' abnormal exit

```

Any solutions?

---

### Post by hannah187 on 2008-05-14
Hi all,

There is not much to report but posting to get some help from more knowledgeable members in this board. Please help me. I am reasonably sound with computer and can follow instructions. I am just fairly new in Linux world. Have done extensive search on this error but google returned nothing. I can post the screen shot (need to take with my Digital Camera) if that helps however the error is mentioned in detail on the first post.

Kind regards and thanks

---

### Post by hannah187 on 2008-05-19
I have now done a bit more serach and have some additional infos. 

After it starts to boot up this is where it ends:

udevd-event[1479]: run_program: '/sbin/modprobe' abnormal exit

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)

(initramfs)

when I press Control+ALT+F1 followoing is the output:


Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/078806ea-f880-46c0-8f81-4aa5b124cee7 does not exist.
Dropping to a shell!


I have started this laptop with 7.10 Desktop Live CD. Took a screen short with gparted as atatched. Also had run the following commands at the terminal when the computer is booted with the live CD (7.10 Live CD: Linux version 2.6.22-14-generic (buildd@palmer)). 

lsusb
lspci
lspci -vvnn
dmesg

Please see the output as atatched.

Kind regards

---

### Post by fmjrey on 2008-06-21
I have exactly the same issue (except the error number: 1479 instead of 1477) trying to install Ubuntu 8.04 on a Toshiba L300D-115. The live CD first gave me this error. Using the alternate CD I managed to get it installed (using manual partitioning) but then had this message when booting on the newly installed Ubuntu
Pointers anyone?

---

### Post by fmjrey on 2008-06-21
I actually managed to get around this problem on a Toshiba L300D-115 with these steps:
[LIST=1]
[*]disable the Realtek LAN interface in the BIOS to boot with Ubuntu.
[*]get the Realtek RTL8187B Wireless interface to work using a workaround explained [here]("http://linux.toshiba-dme.co.jp/linux/eng/pc/sat_PSPD0_report.htm").
[*]connect to my wireless network after removing WEP/WPA (makes the wlan driver freeze the computer otherwise)
[*]get the latest updates for 8.04, especially the new -19 kernel
[*]reboot the machine with the new kernel and the Realtek RTL8102E should be working
[/LIST]
phew!

---

### Post by Storyman on 2008-07-23
I had the same problem with a Toshiba Satellite A305-S6829 using a ship-it disc from Ubuntu.  I downloaded the latest version (8.04.1) from Ubuntu and used that for the install, and that did the trick,it's installing now.  Not to the compatibility issues yet, but at least I got past Busy Box.

---

