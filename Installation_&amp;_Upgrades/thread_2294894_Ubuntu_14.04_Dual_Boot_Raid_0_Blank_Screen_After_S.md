---
title: "Ubuntu 14.04 Dual Boot Raid 0 Blank Screen After Startup"
date: 2015-09-14
forum: Installation &amp; Upgrades
---

### Post by Daniel_Penfound on 2015-09-14
For a couple days now I've been looking around online for an answer to my problems. Here's the issue right now:
I burned the 14.04 image onto a disc. Rebooted computer, started up PC with the DVD as the boot option. A few moments later, the Ubuntu loading screen appears (just the Ubuntu logo with the five loading dots). It sits like that for a little bit, then goes to a black screen. After a few seconds it then goes to a grey screen with a grey bar at the top. The mouse pointer is on the screens (all 3 monitors are a mirror image), and then after a few moment all the monitors turn black, and receive a No Input Signal.

As suggested in a thread I saw, I pushed F6 during the Ubuntu Loading Screen, and just read a bunch of text as it scrolled by. One of the items that stood out was this:
[   91.636015] systemd-udevd[1705]: conflicting device node '/dev/mapper/isw_bacgegeagd_Volume1p1' found, link to '/dev/dm-2' will not be created

I am unsure how to proceed at this point. Here are some specs about my PC:

Windows 8.1
2 SSD's in Raid 0 setup
3-Monitor Setup off of a NVIDA GeForce GTX 750 Ti (I tried plugging in a VGA cable into the slot on my integrated Intel Graphics card, but no luck there either)
Intel i7 4790k

I need to do a Dual Boot setup. If there's any other information I should post, just let me know. I don't know where to go from here, and I'm needing Ubuntu installed to work with my Computer Science Projects.

Thanks, 
Dan

---

### Post by oldfred on 2015-09-14
You have two unrelated issues that you have to work around. RAID & nVidia. Black screen means you need nomodeset on boot. If UEFI you add to grub line, if BIOS press any key then f6. Also after install when you boot until you install proprietary nVidia driver.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Originally Ubuntu had an alternative installer for RAID & LVM on desktops. Standard desktop installer did not have any RAID nor LVM drivers, only server version. But last version with alternative installer with 12.04, and when 12.10 can out they suggested using server installer, or installing 12.04 & upgrading. They said eventually they would add LVM & RAID support to desktop installer. LVM has been added and RAID install works with newer versions, but often grub does not install correctly. Grub then needs repairs with correct drivers installed to get grub to install.

I do not know RAID as there are many different types. Post what RAID type you are using "FakeRAID" or BIOS, hardware and model, or software?

You do know RAID 0 is only for speed as if either drive fails you lose all data.
       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[URL="http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup"]http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup
[/URL]
 Maxwell 750 - kernel 3.15 or newer required
[http://ubuntuforums.org/showthread.php?t=2292419](http://ubuntuforums.org/showthread.php?t=2292419)
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)
[http://ubuntuforums.org/showthread.php?t=2265505](http://ubuntuforums.org/showthread.php?t=2265505)
Usually better to use PPA.
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)

Ubuntu or Ubuntu developers have started their own PPA which may eventually be incorporated into installer so correct nVidia driver may be installed as part of Ubuntu install.
       
 Ubuntu Launches Its "Fresh" Proprietary Driver PPA
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
sudo apt-add-repository ppa:graphics-drivers/ppa.
[URL="http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup"]
[/URL]

---

