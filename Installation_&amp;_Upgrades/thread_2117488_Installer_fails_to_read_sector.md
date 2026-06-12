---
title: "Installer fails to read sector"
date: 2013-02-18
forum: Installation &amp; Upgrades
---

### Post by ivanp on 2013-02-18
Hi,

I'm trying to install Ubuntu 12.10 with dual boot along with a preinstalled win8 os in a dell inspiron 14z with uefi firmware.

I followed the simple instructions to make an efi install the uefi page, but after the Live CD has booted in uefi mode and I get the terminal-like menu and choose any of install / try ubuntu it fails showing a message wich reads:

Failure reading sector 0x5b500 from CD0

and then shows the kernel panic message in the picture attached.


Any idea what the problem might be?

Thanks in advance

---

### Post by oldfred on 2013-02-18
Sounds like defective download or bad write to DVD. Install is oversize so I do not think it fits on CD anymore. Most use flash drives now as they are reusable and faster than a CD/DVD.

       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by ivanp on 2013-02-19
Thanks for your help.

I've downloaded again and burnt a new DVD but got the exact same results.

---

### Post by oldfred on 2013-02-20
Did you verify md5sum? Write at slowest speed. But I think many with UEFI are finding flash works better.

       Dell XPS14
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)
 HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache) - Details
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)
Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)
No EFI boot on Dell Inspiron One 2330 UEFI/BIOS update solved issues:
[http://ubuntuforums.org/showthread.php?t=2086631](http://ubuntuforums.org/showthread.php?t=2086631)

---

### Post by manishiitg on 2013-04-30
is your hard disk working fine? have you run a system test?

---

