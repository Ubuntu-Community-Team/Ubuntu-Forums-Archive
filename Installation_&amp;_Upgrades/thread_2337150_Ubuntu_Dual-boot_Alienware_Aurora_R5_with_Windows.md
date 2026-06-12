---
title: "Ubuntu Dual-boot Alienware Aurora R5 with Windows"
date: 2016-09-15
forum: Installation &amp; Upgrades
---

### Post by praveenlovely on 2016-09-15
Hi,

I got a new computer from Dell Alienware which came with pre-loaded Windows10. 
I erased the HDD completely and installed with a fresh copy of Windows again (performed a clean installation by deleting the existed MSR and recovery partitions)
Now, I used Rufus to create a bootable USB drive using versions of Ubuntu including 14.04 and 16.04 but however, when I load the USB from the BIOS, I get the screen asking for either to Try Ubuntu or install ubuntu or Check disk or OEM blah blah.
I am selecting Install ubuntu and then screen goes black. No response. have to turn off the computer to boot again.
I tried different softwares like Unetbootin and also Rufus to create a bootable USB using the .iso.
My BIOS is at UEFI and the secure boot is disabled.

What could be the problem and how can i solve it?
Please help!

---

### Post by praveenlovely on 2016-09-16
Any replies? or suggestions?

---

### Post by Bucky Ball on 2016-09-16
If you're getting to 'Try Ubuntu' 'Install Ubuntu', you can safely stop wasting time downloading ISOs. It's not that (there is an option to 'Check for defects' when you boot the ISO and you can also check the MD5Sum to verify; safest and fastest way to get the ISO is via a torrent). 

If you installed Windows in UEFI mode, you must install Ubuntu the same way. 

What happens if you 'Try Ubuntu'? Black screen still? Ok, when you boot from the USB you'll get to a purple screen with an icon down the bottom. Hit a key and that should take you to 'Try Ubuntu' 'Install' etc, but with some options. Hit F6 and choose 'nomodeset'. Proceed with 'Try Ubuntu'.

It is not a good idea to try and install Ubuntu if it is already not working with 'Try Ubuntu'. If 'nomodeset' gets you to 'Try Ubuntu' fine, though, you are safe to click the 'Install Ubuntu' icon on the desktop there and install. We can figure out what video driver, if any, you are missing once installed and at a desktop.

Just one more thing: when at the partitioning section, choose 'Something Else', NOT 'install alongside Windows'. The latter option can be problematic.

---

### Post by skraps2 on 2016-09-16
I got the exact same computer a couple weeks ago and I have the exact same issue.  I'm almost thinking it has something to do with drivers for the GPU output.

---

### Post by oldfred on 2016-09-16
If getting black screen are you booting with Intel video from chip or with nVidia chip/card?
Different boot parameters may be needed, until you can boot your actual install and add the proprietary nVidia drivers. Since very new system you may also need a ppa to get newest drivers. Do not download from nVidia.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

After install:

 Ubuntu Launches Its "Fresh" Proprietary Driver PPA - August 2015
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa

---

### Post by taiwuchiang on 2016-11-08
You also need to disable the RAID in BIOS Setup.

---

