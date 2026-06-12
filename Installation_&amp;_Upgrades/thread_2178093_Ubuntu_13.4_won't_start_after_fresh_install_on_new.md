---
title: "Ubuntu 13.4 won't start after fresh install on new system"
date: 2013-10-01
forum: Installation &amp; Upgrades
---

### Post by HuaiDan on 2013-10-01
Here's some background on [http://ubuntuforums.org/showthread.php?t=2177766]("This  thread")
It got closed because I opened another thread while trying to narrow down on the problem.
Basically, I've got a new Nvidia GTX660 card which tested true on 13.4 installed on another system, so I know it's possible to make the thing work.
I've also got a newer z87 mobo with an Intel i7, which hasn't tested true, at least not on Ubuntu. 
The first thing that happened is that I could not boot to the 13.4 Live CD. In order to get around that, I had to set up the DVD drive in BIOS as a UEFI device, which invokes a grub menu from the cd on boot. From the grub menu, I customize the commands with "vga=771", which allows it to boot from the Live CD
Because a "legacy" install didn't work before(goes to grub, freezes on GUI start, gives me a "low graphic mode" message before freezing if I'm lucky), and because the Live CD will only boot as a UEFI device, I figured my only option was to install Ubuntu to boot using grub-efi, which is what I did, following this instructional to the letter:
[https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI")
I installed, rebooted, got a grub rescue prompt, and per the instructional went to the CD again and ran the boot-repair from ppa:yannubuntu, selecting the option for an EFI partition. 
Rebooted again, grub rescue prompt again, error:no such device [some long hex number]
It's also worth mentioning that a SUSE install on the same machine booted right up, but the home directory of that install got wiped as I was trying to get Ubuntu to work.
13.10 beta worked for a bit, was really buggy, and stopped working as soon as I put in the proprietary Nvidia drivers.
Your helpful advice in getting me to the Raring desktop is much appreciated.


**I forgot to include, if I have the BIOS settings to boot to "UEFI Only", then no bootable drives are detected, except for the DVD if I have one in the drive. If I have it set to "UEFI and Legacy" then I get the situation described above. It seems I'm not configuring the install correctly for a UEFI boot,, but I'm not sure what I'm missing. That might be a start, to test whether or not I have such a configuration, but I'm not sure how. That's where I could use some advice.

***Ran boot-repair again, except this time I purged the grub files. Now the  BIOS will recognize a bootable device under "UEFI only", but it throws an error "Select proper boot device or insert boot media." It's the only bootable drive, so there's not much of a choice.

---

### Post by HuaiDan on 2013-10-02
Solved by installing openSUSE.
Seriously, first install,  first try, openSUSE 12.3 booted right up. I've been with Ubuntu since Intrepid, and I've never had this much trouble. Ubuntu, I want my Tuesday back!

---

