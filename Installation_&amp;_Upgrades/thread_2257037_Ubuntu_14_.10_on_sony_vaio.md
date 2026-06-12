---
title: "Ubuntu 14 .10 on sony vaio"
date: 2014-12-16
forum: Installation &amp; Upgrades
---

### Post by Allisterguy on 2014-12-16
Hi
following my success with  installing 14.10 on my new os less pc. I would like to install 14.10 on my wife,s vaio which has windows 8 and she refuses to use it ( suprise, suprise)
I have a few questions if anyone cand help that would be great.
The installation must be from usb as there is no dvd drive.
I have a latest Linux voice disc with 14.10 and Kubuntu, Xubuntu and Lubuntu on it

Q.1. Can I copy and of the programs to a stick and use that , lots of big 8g + sticks or should they all be downloaded?
Q.2. If down load an installer for windows 8 can I do that on my 14.10 pc and save it to the stick or must it be downloaded on  windows in the vaio?
Q.3. Can anyone give me a link for the downloader as I seem to get loads of unwanted offers of programs.

I am using ubuntu,s guide for the installation but the above are the questions I am unsure about
any advice greatly appreciated
Allister

---

### Post by oldfred on 2014-12-16
Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

There is a bug on the Ubuntu usb-creator with some versions.

 Release notes & install issues:
[https://wiki.ubuntu.com/UtopicUnicorn/ReleaseNotes#Boot.2C_installation_and_post-install](https://wiki.ubuntu.com/UtopicUnicorn/ReleaseNotes#Boot.2C_installation_and_post-install)
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801)

I would keep Windows 8 for now on your wife's computer. But use Windows disk tools to shrink it, leaving at least 30% free space or else it will become very slow. Reboot immediately so it can run chkdsk and update itself to its new size.

Make full backup of Windows & efi partition. Even if you do not think you will ever want Windows some later find one program or game they have to have and only runs in Windows. Or later want to sell system and have to have Windows installed.

      
 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

How you boot installer is how it will install, so you want to boot in UEFI mode.

 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

But Sony will not let you boot Ubuntu directly, it modifies UEFI to only boot Windows entry. So we have to do work arounds. If you totally erase Windows you can rename grub or shim entry to read Windows but boot grub  see (D: ).  Or you copy grub & shim into /EFI/Boot and in Sony's UEFI boot menu choose to boot hard drive (see a1 ).
      
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

More info & links in the link below in my signature.

---

