---
title: "Boot-repair pastebin"
date: 2024-12-02
forum: Installation &amp; Upgrades
---

### Post by cliverlong2 on 2024-12-02
Hi

I am pasting on this old forum because being a new user at Level 0 I have "access denied" to create a post on the new Discourse system - even though there is are admin messages saying new users should be able to post on "Support and Help"

The issues to discuss.

1. I have problems booting from a Linux disk on  Mac Pro 5,1 with OCLP 2.0.2 installed.  The boot process was working but "something happened" (TM) and I could no longer boot form the Linux disk on the Mac Pro 5,1. OCLP support states this is not an OCLP problem - but a Linux problem. (see below)

2. I placed the Ubuntu SSD in a USB caddy, plugged it into a PC and that booted into the Ubuntu system no problem

3. I ran Ubuntu boot-repair on the PC and it generated a pastebin diagnosis (follows). [https://paste.ubuntu.com/p/MKR8CZ9jks/](https://paste.ubuntu.com/p/MKR8CZ9jks/) 
I can see that boot repair has detected the Windows 10 installation on the PC. All other drives are data storage such as Windows storage space to "lump together" some old hard drives.


**Objective:**

To make the Ubuntu Linux disk bootable on the Mac Pro

[B]

Original boot problem on Mac Pro 5,1[/B]


[COLOR=#000000][FONT=&quot]The error messages I now get when I select the Ubuntu Linux 22.04 drive from the OCLP boot picker are [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Could not read /EFI/ : Invalid parameter [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Error: could not find boot options: Invalid parameters start_image() returned Invalid Parameter [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]OC: Boot failed – Invalid parameter [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]OCB: StartImage failed – Invalid Parameter[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]The error messages I now get when I select the Ubuntu Linux 22.04 drive from the OCLP boot picker are [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Could not read /EFI/ : Invalid parameter [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Error: could not find boot options: Invalid parameters start_image() returned Invalid Parameter [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]OC: Boot failed – Invalid parameter [/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]OCB: StartImage failed – Invalid Parameter[/FONT][/COLOR]

---

### Post by oldfred on 2024-12-02
I do not know Mac, and what I have seen, it seems every generation has somewhat different issues.
Ubuntu is more for newer systems, you may want a lighter weight flavor.
I found Kubuntu on an external SSD worked well with an old Laptop PC with very limited RAM and slow HDD.

You ran Boot-Repair on a different computer in BIOS mode. Mac needs UEFI boot.
But older coreduo may be unique also.

Report looks correct. But it wants to run BIOS fixes which you do not want as you want UEFI.
Does Lenovo boot in UEFI mode. If so rerun report, but it still may not show issues as may be related to UEFI settings in your Mac.

Many posts with Mac use rEFInd as a solution.
I have used rEFInd on my PC as emergency boot. I have tiny flash drive that had no other use. But can recommend rEFInd.

[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/) &
[https://askubuntu.com/questions/908677/want-to-view-contents-of-boot-efi-in-xubuntu-dont-have-permissions](https://askubuntu.com/questions/908677/want-to-view-contents-of-boot-efi-in-xubuntu-dont-have-permissions)

Older threads, may have some suggestions:
 MacBook Pro 8,2: howto for dual boot Ubuntu/MacOS EFI with rEFInd
[http://ubuntuforums.org/showthread.php?t=2157775](http://ubuntuforums.org/showthread.php?t=2157775)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

---

