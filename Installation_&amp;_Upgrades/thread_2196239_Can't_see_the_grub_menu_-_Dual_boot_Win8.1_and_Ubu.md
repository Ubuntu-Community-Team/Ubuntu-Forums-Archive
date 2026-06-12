---
title: "Can't see the grub menu - Dual boot Win8.1 and Ubuntu 13.04"
date: 2013-12-28
forum: Installation &amp; Upgrades
---

### Post by devine.steve on 2013-12-28
I took my Toshiba laptop back and got a Samsung ATIV Book 4. I repartioned the drive using Windows disk utility and made a 300 G home for Ubuntu.
Did the install from my USB key and it put it on my new partition just fine. However when I boot up I never see the familiar menu choices. It just goes right into my Win8.1 OS. 
I booted back into the Live USB and ran boot-repair. Here is my boot info [http://paste.ubuntu.com/6652254/](http://paste.ubuntu.com/6652254/)
This is somehow related to UEFI.

---

### Post by oldfred on 2013-12-28
From UEFI/BIOS you now have two (three) boot choices. UEFI or BIOS/CSM/Legacy and UEFI can be either with or without secure boot.
You have Windows installed in UEFI mode, but installed Ubuntu in BIOS mode. The only way you can boot Ubuntu is to go into UEFI/BIOS turn off secure boot, turn off UEFI and turn on CSM/Legacy. Then to boot Windows you have to turn UEFI back on. Some auto switch and you can use f12 or what ever one time boot key your system has.
Better to install Ubuntu in UEFI mode and then you can dual boot from grub menu if you set (or maybe can set) ubuntu as default boot with UEFI on. Boot-Repair can convert your install to UEFI by uninstalling grub-pc(BIOS) and installing grub-efi (UEFI). But better to always boot live installer and all systems with UEFI and not use BIOS. Some need the CSM on for Intel i915 driver to work correctly even when booting in UEFI mode, if that combination of settings is allowed by your UEFI.

       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

See signature below for lots more info.

---

### Post by devine.steve on 2013-12-30
Well, it didn't work out quite the way I hoped. I first found out that I had the 32 bit OS so I got the 64 bit one. When I installed it it offered to "reinstall the Ubuntu OS" so I chose that. And it wiped out the Win 8.1 partition. Sigh. In retrospect I read somewhere that it might do that and that you should always select Something Else. I do have a backup but now I have to figure out how to get to it since I saved it on a network drive. Truth is I don't really want to use the Windows side but I like to keep it around for when I sell the laptop (or give it to a grandkid)

---

### Post by oldfred on 2013-12-30
You have to be at least the third or fourth user who has done that, that I have seen. First time or two I thought it was just a user error. But it really is an Ubuntu bug.

Not sure if one exists. But best to file one on reinstall erases entire drive not just Ubuntu as stated or some similar.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bugs?field.status:list=NEW](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bugs?field.status:list=NEW)

       bug reports info on how to do:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)
[http://www.ubuntu.com/community/report-problem](http://www.ubuntu.com/community/report-problem)

---

### Post by devine.steve on 2013-12-31
OK
Bug filed. #1265192

---

### Post by oldfred on 2013-12-31
Thanks, I will pass it along as with one report they often think it is just a user issue. I will have to see if any of the previous are still around if I can find the threads and get them to post.

---

