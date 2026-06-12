---
title: "error: invalid environment block, not booting"
date: 2018-03-16
forum: Installation &amp; Upgrades
---

### Post by damga on 2018-03-16
I installed Ubuntu alongside Windows 10 for the first time, it worked and after it finished I was able to reboot. I then rebooted and booted into windows, rebooted again and tried to boot into Ubuntu again. Then I got the error message "error: invalid environment block. Press any key to continue..." After pressing any key I get a different screen with some stuff and "(initramfs)" while being able to type (see imgur album). 

I still had the USB I used to install it and so I booted using that and tried to use boot repair. After doing so and rebooting, the option to boot into Windows was gone from grub. I also tried to remove the "recordfail" line after pressing E in grub, but that didn't work either. 
The boot-repair pastebin(I emailed the email that was in the boot-repair message aswell): 
[http://paste.ubuntu.com/p/nWcbq4dwzF/](http://paste.ubuntu.com/p/nWcbq4dwzF/)
[https://imgur.com/a/kCwqc](https://imgur.com/a/kCwqc)

Hopefully someone can help me fix this, if there's any information needed I'll try to provide it.
Thanks in advance

---

### Post by oldfred on 2018-03-20
Not seeming much.

Is drive set to AHCI in BIOS, not RAID, nor IDE.

there is this at line 910:
```
 Could not detect USEDPERCENT of sda2 ().
/dev/sda2      114522640 -12888824 127411464    - /mnt/boot-sav/sda2 


```
Often the Linux NTFS driver cannot read NTFS if Windows 8 or 10 has fast start up on. Or it may need chkdsk.

 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

