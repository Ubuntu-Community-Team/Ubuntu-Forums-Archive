---
title: "Dual boot w/external drive"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by bundtcake on 2007-06-29
I'm using a Toshiba laptop w/ Windows XP Prof - I loaded Ubuntu 7.04 on an external drive and all seems well except I can't  boot into Windows without the external drive (w/Ubuntu) connected.

I suspect GRUB is planted in the Master Boot Record on the laptop hard drive as I really didn't know all of what I was doing in setting things up with Ubuntu.

In booting the laptop without the Ubuntu external drive connected, I get this message:

"GRUB Loading stage 1.5.
GRUB loading, please wait ...
Error 21"

With the external drive connected, I have an OS list to choose from to boot into - all works as expected.

In looking at the Windows "boot.ini" file, this came up:

"Boot Loader Settings
--------------------
timeout: 30
default: multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
 
Boot Entries
------------
Boot entry ID:   1
Friendly Name:   "Microsoft Windows XP Professional"
Path:            multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
OS Load Options: /noexecute=optin /fastdetect"

I successfully (?) changed the bootcfg default to "Windows XP Professional" and rebooted (without the Ubuntu drive connected) - still got the GRUB error.

This is the edited "boot.ini" file:

"[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect"

I appreciate any thoughts anyone can offer!

---

### Post by logos34 on 2007-06-29
Yes, grub overwrote the windows bootloader.  All you have to do is restore it using the windows setup cd. 
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654) 
Basically you just hit 'R' to enter recovery console and then do fixmbr or fixboot.

Or use [SuperGrub CD]("http://supergrub.forjamari.linex.org/").  This can also write Grub to the MBR of the external USB drive.  You want to set the external drive as the first hard disk in the BIOS boot priority so that it defaults to windows if the drive is disconnected/off.  However, in doing so the usb drive will become '(hd0)'--where it was (hd1) before--which means you will have to access  menu.lst and device.map in /boot/grub directory, changing all instance of 'root (hd1,x)' to '(hd0,x)' so that you can boot Ubuntu.  See [this link]("http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands") for editing your windows entry so that it boots on a non-first hard disk.

---

