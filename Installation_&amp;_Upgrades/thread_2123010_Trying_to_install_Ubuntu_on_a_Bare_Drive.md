---
title: "Trying to install Ubuntu on a Bare Drive"
date: 2013-03-06
forum: Installation &amp; Upgrades
---

### Post by NanaHaru on 2013-03-06
Good afternoon Ubuntu Community,

I finally after a bit of saving, was able to purchase a new computer. I was hoping to install UBUNTU on this computer as it is the best OS for rendering and the things I need it for. The whole point being I didn't want to dual boot anymore, and just have two separate computers. Problem: I put together the computer, turned it on, tried booting it from a LiveCD, but it just goes to a black screen where I can type. I'm not amazing with computers, so I'm sure I'm missing technical terms. However, I have tried using a LiveCD as well as a LiveUSB. Neither work. So here are my specs, and I really hope someone can help me. 


Motherboard: ASRock Z77 Extreme 4
Processor: Intel i7 Ivy Brige
Graphics Card: NVIDIA EVGA GTX 680 FTW
RAM: Vengeance 8Gb
HDD: Seagate 1Tb

Those are the only things I could think of that would affect the OS... I'm probably wrong though. Another possible problem that I've heard of is that my Motherboard works UEFI... I've tried looking up on various faqs and help pages... But I can't seem to figure anything out on my own. So I turn to you, O great and awesome community of Ubuntu, Please help~? Thanks again for the help in advanced~!!!

---

### Post by ibjsb4 on 2013-03-06
I don't UEFI, but this may help you out.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by NanaHaru on 2013-03-06
I tried following both of those guides. I did everything it asked... I can't seem to get it to run. I was under the impression that all the Hardware is compatible and no where could I find that they "were not" compatible. I'm downloading the 32bit system right now, just to check and see if that will run, and then later I can upgrade to 64bit. Another idea I had is, would it be possible to use a different computer to install Ubuntu onto my HDD and then just plug it into my new computer and run it?

---

### Post by arpanaut on 2013-03-06
Have you tried to change the kernel options  for booting the live cd/usb?
See here: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

scroll down a bit to see how to set nomodeset for the live cd etc.
Many times necessary to get things to boot to the live session.

If you get things installed you may need to do this from grub on first boot,
then you can get the proper drivers installed to the system.
That is included in that link too.

Good Luck.

---

### Post by oldfred on 2013-03-07
+1 on arpanaut's suggestion of nomodeset.

With nVidia I have to use nomodeset on every boot of a live install and on first boot after install until I get nVidia drivers installed.

If you have an UEFI system you have to use 64 bit as only the 64 bit version of 12.10 and the new 12.04.2 have the newest UEFI.

And with 12.10 I also had to install headers to get the nVidia driver to install correctly.
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

After install do this as very first thing:

 # You may need headers first - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

If you have UEFI/BIOS you can install in either UEFI mode or BIOS mode. But if dual booting with Windows you have to install in the same mode Windows is in or you cannot easily dual boot.

      
 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

---

