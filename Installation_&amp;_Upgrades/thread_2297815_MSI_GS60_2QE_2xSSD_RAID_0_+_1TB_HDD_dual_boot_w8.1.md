---
title: "MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem"
date: 2015-10-06
forum: Installation &amp; Upgrades
---

### Post by Valentn_Pedrosa_ on 2015-10-06
Hello everybody.

This is the first time I post here, so I will try to do my best :D.

I just bought a brand new MSI top tier laptop for work & game.
I need dual boot Ubuntu-Windows for my work, but I have lost all hope about that, so I'm just trying to find any solution that make possible both system to coexist (except VirtualBox and USB install).
Actually I asked for help on my college's free software office, but they couldn't help me.

So here's what I tried, nothing worked.


[LIST=1]
[*]UEFI 14.04.3 LTS Ubuntu installation -> Freezes on partitioning or installing, no output. (Tried on W10 & W8.1)
[*]UEFI 15.04 Ubuntu installation -> The same, freezing on partitioning or installation, without output (Tried on W10 & W8.1)
[*]Both of them via USB and CD (Tried on W10 & W8.1)
[*]Wubi install
[*]LEGACY 14.04.3 LTS Ubuntu installation -> Freezes with this output (Tried on W8.1):
[/LIST]

[ATTACH=CONFIG]264837[/ATTACH]

If there's a need of more information of the laptop I will provide ASAP.

Thank you very much.

---

### Post by oldfred on 2015-10-07
Wubi was last supported with 12.04. It does not work with UEFI/gpt partitioning.
       Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

If Windows is UEFI, best to install Ubuntu in UEFI boot mode.

I do not know RAID and that does complicate it.
Review of your model says this GeForce GTX 970M Maxwell which also complicates it.
Usually you can install & first boot with the nomodeset boot parameter, then add a ppa to be able to download the newest nVidia driver.

What CPU does your system have? Does it use dual video or just the nVidia chip?

You do know that RAID 0 is just for speed. That any failure of one drive and you lose all your data. Or you need really good backup procedures to another drive(s). 

 [http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

       
 
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

    If system is booting with Intel chip, then different boot parameters are requried. And if very new Skylake a special parameter is required.

If very new hardware, you may get system to work better with 15.10 even though only in beta. I normally would not suggest that as while in beta, it may have an update that breaks it, so do not totally rely on it until finalized.


  MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI Z170A GAMING PRO motherboard
[http://www.phoronix.com/scan.php?page=article&item=msi-z170a-gaming&num=1](http://www.phoronix.com/scan.php?page=article&item=msi-z170a-gaming&num=1)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)

---

### Post by Valentn_Pedrosa_ on 2015-10-07
Thank you very much for you response.
I tried the following things, with same installation freezing error at the end, no output:


[LIST]
[*]Installing 14.04.3 Ubuntu with nomodeset UEFI
[*]Installing 15.04 Ubuntu with nomodeset UEFI
[*]Installing 15.10 beta2 Ubuntu UEFI
[/LIST]

My laptop relevant hardware setup:


[LIST]
[*]i7 5700HQ (Broadwell)
[*]nVidia GTX 970M
[*]2x512GB SSD
[*]1TB HDD
[/LIST]

What else can I try?

---

### Post by oldfred on 2015-10-07
Do you know if it is booting with nVidia, or booting with Intel video?

Boot parameters if booting in low power mode.
       # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size

Some systems also need additional boot parameters, video plus one of these:
      
 Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

And post above mentions this:
libata.force=noncq

---

### Post by Valentn_Pedrosa_ on 2015-10-12
Hi again!

Thanks you I've achieved last night installing ubuntu 14.04.3 with following options:

nomodeset
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic video=1920x1080-24@60
video=VGA-1:1920x1080-24@60

Actually, ubuntu grub doesn't load (it loads as a purple blank screen), and I've to select OS on BIOS UEFI when swapping OS.
But the real problem now is the laptop is overheating.
When I start windows, fans are running smooth and even the second one (it has two) is stopped. 
But when I start Ubuntu, core temps start to get high until laptop powers off.
Does "acpi=0" option has something to do with this?

---

### Post by oldfred on 2015-10-12
I have seen several threads in forums on overheating but have not followed them. You can search forum for those.

What version of Ubuntu? And have you installed newest nVidia driver?

       Ubuntu Launches Its "Fresh" Proprietary Driver PPA
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
sudo apt-add-repository ppa:graphics-drivers/ppa

---

### Post by Valentn_Pedrosa_ on 2015-10-12
Thank you very much for everything, I will keep searching in other forums, for overheating and wifi problems.

---

### Post by noxo on 2015-11-17
I've exactly same MSI GS60 model (with Broadwell I7-[COLOR=#000000]5700HQ [/COLOR]and 970m) with one 128GB mSata SSD and 1TB HDD. And I've Ubuntu 15.10 
running now nicely (alongside with Windows 8.1), without extra boot parameters.

Main thing were to [disable "Intel SpeedStepping" in BIOS]("http://www.ygbae.com/blog/2015/8"). If it's not disabled computer seems to hang/restart randomly, I couldn't even finish 
the installation.

WIFI wasn't working after installation of 15.10. It was [supposed to be fixed]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1383184") after pulling latest updates using apt (apt-get update, apt-get upgrade),
but it was just partially working (list of APs were showing, joining to AP failed, can see firmware crashes in dmesg). 

So, here's how I fixed the broken WIFI:
- sudo apt-get update
- sudo apt-get upgrade (now you have partially working WIFI)
- replace board.bin and firmware-5.bin files in lib/firmware/ath10k/QCA6174/hw2.1 from this GIT repo [https://github.com/kvalo/ath10k-firmware/tree/master/QCA6174/hw2.1](https://github.com/kvalo/ath10k-firmware/tree/master/QCA6174/hw2.1) (wifi is now fully fixed)

To enable NVIDIA 970m GPU (with "oldish" v352 drivers):
- Add file /etc/modprobe.d/blacklist-nouveau.conf containing: "blacklist nouveau options nouveau modeset=0"
- sudo apt-get install nvidia-352 nvidia-prime
- sudo reboot

You can then switch between Intel HD / NVIDIA graphics by launching "nvidia-settings" (-> prime profiles) from console. (as I understood bumblebee/optirun is no longer recommended)

About installation, I was a bit afraid of UEFI installation, but Ubuntu wen't smoothly into that 1 TB drive, without messing preinstalled Windows 8.1. Here are the steps:
- Shrink 1 TB partition using Windows 8.1 Disk Management, and leave what ever you want as unused partition for Ubuntu
- Disable Secure Boot, Fast boot, and Speed Stepping in BIOS
- Boot to UBuntu install media (CD/USB), select Install or Try Ubuntu (on latter you can start installation from Desktop -> Install Ubuntu)
- Choose "Install Ubuntu alongside Windows 8.1"
- Confirm newly added partitions (it was pointing 1 TB drive for me automatically, e.g. sdb)
- Wait until install is complete & reboot
- Laptop will boot to Windows 8.1 by default, but you can boot to Ubuntu by pressing F11 and selection Ubuntu. You can change default OS, in BIOS -> BBS priorities

Maybe the thread topic can be marked now as SOLVED ;)

---

