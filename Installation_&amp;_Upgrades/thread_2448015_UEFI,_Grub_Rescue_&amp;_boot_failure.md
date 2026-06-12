---
title: "UEFI, Grub Rescue &amp; boot failure"
date: 2020-07-30
forum: Installation &amp; Upgrades
---

### Post by spencer2 on 2020-07-30
So, I did a regular old update like 2 days ago & then when I rebooted, it went into the grub_rescue boot. I had a specific missing calloc file.

I've kind of worked through some of it (I think) but am now stuck with the BIOS boot order sort of out of whack. I don't know why any of this happened: & sort of most specifically right now, I don't know why the BIOS settings that I had are now not working. I keep booting directly into windows (which was not the case before the grub rescue the other day).

This is happening on an Acer F15 laptop: I'd almost not mind the clean reinstall of the new Ubuntu 20 LTS; but I'd strongly prefer not losing some files on my current install.

My bios are in uefi (not legacy); the windows boot loader is way down the order list in the boot sequence; so not sure why Ubuntu isn't popping up first.

Help please.

---

### Post by spencer2 on 2020-07-30
Might this be part of what I'm experiencing?

[https://ubuntu.com/blog/mitigating-boothole-theres-a-hole-in-the-boot-cve-2020-10713-and-related-vulnerabilities](https://ubuntu.com/blog/mitigating-boothole-theres-a-hole-in-the-boot-cve-2020-10713-and-related-vulnerabilities)

---

### Post by oldfred on 2020-07-30
Not at all related, unless you invited a hacker into your house and gave him root access to your system.

Often Windows updates, which you may not even see, are the issue.
Windows updates will reset boot order to make it first in boot order. Just as when grub installs it makes grub/ubuntu first in boot order.

You also may have had an Acer UEFI update which can reset some settings back to defaults. I have to keep a list and after every UEFI update check that settings have not changed. Several normally do.

Did your Acer require setting "trust"? Many older ones did, but it seems now not all of the newest do need that setting. 
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
Acer Aspire A515-54G Newer Acer -  CTRL S on the main Tab in BIOS to get the option to change SATA to AHCI
[https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected](https://askubuntu.com/questions/1211911/cannot-install-ubuntu-on-acer-aspire-a515-54g-laptop-hard-drive-not-detected)
Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 

If not UEFI settings, run this:
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by spencer2 on 2020-07-30
I did run the boot repair & this is the link to my report

[http://paste.ubuntu.com/p/3qZDrsY7dP/](http://paste.ubuntu.com/p/3qZDrsY7dP/)

Honestly, I'm not completely clear on what the report needs me to do first. I'm also a little unclear about the UEFI lock. Do I need to set a supervisor password? I feel like I've not had the "Password on Boot" in BIOS enabled (its current disabled). UEFI is the boot mode & Secure boot is enabled, but I don't know how to turn it off. I can only switch between uefi & legacy.

Thank you for your help & I appreciate additional tips. Thank you again

---

### Post by spencer2 on 2020-07-30
I turned off the UEFI (entered legacy) & rebooted: I'm back into the grub rescue prompt. It says:

error: File '/boot/grub/i386-pc/normal.mod' not found

---

### Post by oldfred on 2020-07-30
You do not want legacy/BIOS/CSM boot mode. Only use UEFI or UEFI with Secure Boot.

> 
Windows is hibernated, refused to mount.
Looks like Windows updates turned it back on, if you had it off before.
Grub only boots working Windows and Fast start up sets hibernation flag preventing Linux NTFS driver from mounting read/write. It only can be forced into a read only mode, but all default mounts are read/write.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Error on normal not found is typically from trying to boot in wrong boot mode. But you only get that when you have a grub that was installed in BIOS mode in MBR that now is not valid. You do not need to really do anything, just never try to boot in BIOS mode.

> Boot0000* Unknown Device: 
You show two unknown & one with Ubuntu. Not sure then how you got Ubuntu entry in UEFI.
The unknown is typical for the ubuntu entry from Acer before you set "trust". 
See links above on how to do trust with Acer.

---

### Post by spencer2 on 2020-07-31
I do have my ubuntu booting up now: thank you for your help. It is greatly appreciated.

---

