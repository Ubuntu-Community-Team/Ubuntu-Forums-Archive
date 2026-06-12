---
title: "Help Installing LUbuntu 16.04 on XPS 13 (UEFI)"
date: 2016-11-22
forum: Installation &amp; Upgrades
---

### Post by drcrick on 2016-11-22
Hello, i'm new to the forum, I use Linux on my old desktop, but for the first time i want it on my Laptop.
Since my laptop is new i´ve been reading it has the UEFI boot which is the one that allows the (almost) instant boot, i would like to know if Ubuntu can boot in this mode (has fastboot) and instant wake-up. Since i´m totally ignorant about linux but i´m willing to learn, i would like to install it on my Dell XPS 13, but i'm not sure what should i change in the BIOS settings for Ubuntu to run properly and without the GRUB. I just want plain Ubuntu.

I would really appreciate if you explain to a totally new person on the subject.

Thanks!

[I have the i5 Skylake FHD model]

---

### Post by RobGoss on 2016-11-22
Hello and welcome, give us a little information on the hardware you're running on this machine 

Are you wanting to dual boot Windows and Ubuntu?

With the new UEFI feature on most of the new computers these days it makes installing Ubuntu a bit harder but not to worry we've surpass this and are still able to complete just about any installation 

Keep in mind when you install Ubuntu what ever MODE Windows is installed Ubuntu has to be installed in the same fashion meaning the same mode

Example: Windows is installed in UEFI mode that means Ubuntu needs to be installed in the same way UEFI

This reference page should be helpful
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You should also turn off Fast startup and secure boot, as well when when you proceed with this instalation

---

### Post by oldfred on 2016-11-22
I would turn off the fast boot while configuring system. YOu may turn it back on later if desired.
My motherboard has a setting for delay of fast boot so I have time to press a key to get into UEFI and make changes. Most systems will also do a normal boot from a full power down or cold boot.

The fast UEFI boot skips all checks for hardware or software reconfiguration. And that is often the case that normally system is the same. But then if you are making changes they are not seen. Also it can be so quick that you do not have time to press the keys to get into UEFI to have to recheck for new hardware. Assumption is that from Windows you can reboot into UEFI. And now grub has menu item to boot into UEFI, but if neither works, some users get locked out, until cold boot.

Dell develops sputnik which has updates for Dell hardware drivers that are needed for Linux/Ubuntu. Usually those later get incorporated into the full distribution, so you probably need the newer version of Ubuntu and may need to add other drivers.

 Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9) 

        Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers)
Dell XPS 8900 i7-6700 pcie_aspm=off (also: Asus X555UB)
[http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive](http://askubuntu.com/questions/760257/ubuntu-16-04-failed-clean-install-on-new-hard-drive)
Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
XPS 13 9350 Windows reinstall & discussion of RAID vs. AHCI
[https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/](https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241)

---

### Post by drcrick on 2016-11-22
I finally installed from an USB drive, i read i had to switch RAID to AHCI and it would work. Actually is working fine with all the updates already installed, now i'm having a bit of a confusion about intel drivers, since i would like to install the ones that would work better for games (since i play DOTA2) but it seems i have many options. I downloaded an intel update tool for linux (2.0.2) but it fails to update the drivers since i'm lacking the kernel 4.7 that works with skylake, any idea about this?...

Everything else is working i left the UEFI booting mode and erased Win10, i didnt turned off the fastboot and it seems to work fine with it.

Thanks!

Any suggestions on getting Vulkan to work on ubuntu 16.04 with Intel HD520?

---

