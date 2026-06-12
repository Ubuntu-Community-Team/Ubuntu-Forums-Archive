---
title: "Failing to Boot Ubuntu from USB3 on Toshiba Ultrabook Z935"
date: 2012-12-28
forum: Installation &amp; Upgrades
---

### Post by Michellle on 2012-12-28
Hi everyone,

Sorry for the amateur-ish question... but I would be very grateful for some help!!

I am trying to boot Ubuntu 12.10 from USB3 on my Toshiba Ultrabook Z935 in order to install it alongside Windows 8. But I can't get it to boot from the usb! :-(

Naturally, the first thing I did was change the boot order in the BIOS so the USB memory is first. But when it didn't make a difference, I started researching what the problem could be and I've tried everything I came across and I still can't get it to boot. 

I disabled the secure boot, and after a few other changes in the bios, I finally disabled the USB legacy emulation. The latter resulted in "preparing automatic repair" on the Toshiba startup screen and nothing else. All other changes kept booting me into windows. I read a few different things, but so far nothing is working for me. 

Thanks so much,
Michelle

---

### Post by oldfred on 2012-12-28
Welcome to the forums.

With Windows 8 you do have to turn off secure boot and really need to turn off any fast boot or quick boot type settings. 

Once secure boot is off you should then in UEFI menu have the option to boot the flash drive.

But flash drive does have to be bootable or Ubuntu has to be installed to it not just the ISO copied to it.

I know on older systems some has issues booting from USB3 ports. Do you have any USB2 ports? New UEFI should work.

Also some have had issues with certain flash drives or different USB creators. Some have just used a different flash drive, or used a different USB creator or downloaded it again as first download was not ok. Did you check md5sum?

       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

    
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
   
Standard instructions are in link above for installing to flash drive from Windows. Other alternatives.
       [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by Michellle on 2012-12-28
Thanks OldFred!

I do have USB2 and neither USB2 nor USB3 made a difference. On another blog, someone who successfully installed Ubuntu on their Z930 said that USB2 doesn't work and that I have to use USB3. ([http://yltechblog.blogspot.com/2012/09/installing-ubuntu-1204-to-toshiba-z930.html](http://yltechblog.blogspot.com/2012/09/installing-ubuntu-1204-to-toshiba-z930.html)) Unfortunately, I didn't get the answers I was looking for. 

The USB stick I am using is bootable and has been used to install Ubuntu on another machine. And md5sum has been checked. 

Still nothing... :-(

Michelle

---

### Post by oldfred on 2012-12-28
Is your install the 64 bit version of 12.10. That is the only one that supports secure boot with Windows 8.

Or do you get past boot and have video type issues.

Is this a Ultrabook with the small SSD? That complicates it, but several have posted how to do it. Some prefer Ubuntu and just install its / (root) to the SSD, other install to the hard drive. But you have to turn the Intel SRT off and maybe remove the RAID settings.

Standard UEFI installs, best to review first.
       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)


Then Intel SRT, basically the same for all vendors:
       
  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it. 
  > You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.From 2011, so now older
[http://tobestool.net/using-intels-rst-with-linux/](http://tobestool.net/using-intels-rst-with-linux/)

---

### Post by Michellle on 2012-12-30
It seems the USB is carrying the 32 bit version although I thought it was 64. Installation on old machine vs new machine confusion. I will try with the 64 bit version. Hopefully, this is the problem and we'll be OK. 

I'll keep you posted! 

Thanks for now!

Michelle

---

### Post by Michellle on 2012-12-30
Thank you OldFred! 

The 32bit installation was the problem!! 

We finally booted successfully! LOL 

Michelle

---

### Post by oldfred on 2012-12-30
Glad  that worked. :)

---

