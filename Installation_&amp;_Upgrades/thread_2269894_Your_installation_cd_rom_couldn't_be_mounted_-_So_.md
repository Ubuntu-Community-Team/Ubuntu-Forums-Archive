---
title: "Your installation cd rom couldn't be mounted - So many install issues"
date: 2015-03-18
forum: Installation &amp; Upgrades
---

### Post by Ub3rZ4cH on 2015-03-18
Hello everyone,

Okay let me start with where I am now to cut a long story short, I am trying to install any kind of ubuntu I have tried xubuntu, ubuntu normal, and ideally the one which I actually want to install which is ubuntu server, now I went out and bought a SATA DVD drive and burnt the ISO to a disc and it boots just fine, but when It gets to the step
checking media and other hardware it throws the same error I have been getting with a USB stick and with frugal installs the lot.

Okay so long version being first thing I tried before I bought the DVD drive was a simple bootable USB stick using universal usb installer (tried unetbootin too but I will get to that), and well it boots just fine and it gets passed the stage of detecting cd rom and other hardware, I am able to get to the partition stage but when I boot from USB it somehow disables the sata HDD I have plugged in and so I can only find my mem stick and thats where I am booting from, It does say to unmount partitions because of course the mem stick is being used but I have tried both answering YES and NO to that question and it still can not find my hard drive.

The hard drive shows up just fine in BIOS and the boot order was USB then HDD, and when I switch it and try getting the F11/F12 boot menu the mem stick is not there, so the only choice is to change to the mem stick to boot first, but then like I said the HDD is not there. Okay so I figured ah well I will try a live cd, still same issue, I even tried to list the devices and check in gparted etc no HDD just the USB drive.

So after hours upon hours I tried to install it on a different PC, I plugged the HDD into my other pc and it booted the USB stick fine and installed fine, and booted the OS, but because I removed the HDD to the other pc GRUB messed around, even when I tried various different ways of installing grub it just refused to start up on the pc I actually want the server on. I have tried editing the grub using grub command line, I have tried to edit the boot config with E, which for some reason has the mem stick (hd1,msdos1) when it needs to be (hd0,msdos1), I tried editing that and it still didnt work, dont even know if it saved.

So I then tried hours on hours to try fix grub, even downloaded a grub fixer which boots some flavour of linux with XFCE on and a GUI program to fix the grub, but again it couldnt detect the other HDD with the ubuntu OS on it. Eventually I tried a PXE boot and I realized the motherboard didnt support network boot so that came to a dead end.

So after a few days of trying to get this to work I gave up and bought a DVD drive (ancient things I know) not owned one in at least 5-6 years, and got by installing operating systems with a USB stick and failing that I have even installed easily with PXE or frugal installs, this time the pc isnt having it.... I boot from the CD rom freshly burnt and it boots fine chose the language and everything then it says basically the disc isnt inserted which I the same issue I had with a frugal install, now I know from experience the frugal install has done this before I have even had this issue with a mem stick I just go into command line and mount the mem stick as /cdrom, but as I am literally using the CD rom now I am completely lost.

So long story short this motherboard is being a complete b***h and I really need something to start with to get a decent linux machine up from it. So I am stuck at the error saying the CD rom cant be mounted, I have tried to eject the disc and re-insert it, I have even tried something to do with IDE=nodma. I have searched for hours and hours all over the internet on all aspects of all the problems I have come across, and I figured using a DVD would be best because I can see the HDD this time but now its a problem with the damn install media!

PS. even tried wubi and for some reason even that fails to work.

---

### Post by Bashing-om on 2015-03-18
Ub3rZ4cH; Yukkie ..

If nothing else "E" for effort.
Let's get the prelims established , get a firm foundation to work from:
1. Verified that the .iso file is valid ?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

2. What is the firmware on the main board ? Bios or UEFI ?

3. Is secure boot an issue ?

4. SSD drive(s) ? hybrid ? ISRT ?.. is meta data for raid an issue ?

The 1st step after these factors are known is to get the liveDVD to boot in "try ubuntu" mode to the GUI desktop.

[INDENT][INDENT]hardware, getting to smart for our own good
[/INDENT][/INDENT]

---

### Post by Ub3rZ4cH on 2015-03-18
> **Bashing-om said:**
> Ub3rZ4cH; Yukkie ..

If nothing else "E" for effort.
Let's get the prelims established , get a firm foundation to work from:
1. Verified that the .iso file is valid ?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

2. What is the firmware on the main board ? Bios or UEFI ?

3. Is secure boot an issue ?

4. SSD drive(s) ? hybrid ? ISRT ?.. is meta data for raid an issue ?

The 1st step after these factors are known is to get the liveDVD to boot in "try ubuntu" mode to the GUI desktop.[INDENT][INDENT]hardware, getting to smart for our own good
[/INDENT]
[/INDENT]



Okay here goes lol;

**1. MD5 checks out okay:**

[IMG]https://lh5.googleusercontent.com/-A0NGtS2cit4/VQoZkkmAX3I/AAAAAAAAEwM/oK39Pyyw-6A/w509-h445-no/md5.png[/IMG]

2. BIOS only UEFI when I try frugal with Windows 8 which isnt supported but still boots but gives same error about finding the install media

3. No secure boot

4. Standard old SATA HDD tried with 3 other HDDS

5. I can boot a live CD just fine, but trouble is I want ubuntu server... but when I got the live CD working It was with a USB stick and so with that I could not see the HDD
but I can try using a live CD disc to see if the HDD is there then, maybe install inside ubuntu but again I idealy want ubuntu server, only got the DVD drive tonight (GMT here 1am lol). I will try a live CD in a moment give me a second.... I will update the thread.

cheers for trying to help.


**UPDATE: **okay so interesting things the DVD rom tries to boot but gets to an error I think I got with the USB stick too at one point, it just falls to busybox, and says (initramfs) unable to find a medium containing a live file system that last part after initframs is new. but previously like I said the F11/F12 boot menu never use to show the HDD with the USB stick but with the CD inserted it does now show both the CD drive and the HDD, but doesnt boot, and I compared the MD5 too which were fine.

---

### Post by Bashing-om on 2015-03-18
Ub3rZ4cH; Humm ....

Pause for cause, please clarify :
> 
only UEFI when I try frugal with Windows 8 

as Win8 is UEFI .. and secure boot is standard.
So long as secure boot is enabled, will not be able to boot anything else .

And that is about the end of my knowledge of UEFI. IF Win8 is a factor, we must match the ubuntu install to how Windows 8 is installed (UEFI). secure boot turned off.

I am sure others here can advise better. But sure looks a secure boot issue - 
Perplexing though " I can boot a live CD just fine, but trouble is I want ubuntu server "  HUH ? IF you can boot the "normal" desktop ubuntu, I can think of no reason that the server edition will not boot ; less perhaps the server install is looking for a wired connection, and the wired connection does not exist ?

[INDENT][INDENT]if I only knew
[/INDENT][/INDENT]

---

### Post by Ub3rZ4cH on 2015-03-18
> **Bashing-om said:**
> Ub3rZ4cH; Humm ....

Pause for cause, please clarify :

as Win8 is UEFI .. and secure boot is standard.
So long as secure boot is enabled, will not be able to boot anything else .

And that is about the end of my knowledge of UEFI. IF Win8 is a factor, we must match the ubuntu install to how Windows 8 is installed (UEFI). secure boot turned off.

I am sure others here can advise better. But sure looks a secure boot issue - 
Perplexing though " I can boot a live CD just fine, but trouble is I want ubuntu server "  HUH ? IF you can boot the "normal" desktop ubuntu, I can think of no reason that the server edition will not boot ; less perhaps the server install is looking for a wired connection, and the wired connection does not exist ?
[INDENT][INDENT]if I only knew
[/INDENT]
[/INDENT]


Okay no let me reiterate. Windows 8 was only when I tried a frugal install, the HDD im currently using has ubuntu server on it but was installed with another machine so the grub is buggered and I cant boot it, I want to just wipe it again and re install... so there is no secure boot or uefi.

I can only boot the live cd with a USB drive... live cd not literally meaning a CD meaning a USB drive. but ubuntu server does not have a live cd to "try it out" as its normally headless without a GUI. its nothing to do with network as the setup does not even get to the stage of configuring TCP or DHCP.... It says that the CD rom can not mount (when trying to install ubuntu server) but when trying to boot a live cd of ubuntu desktop it fails and goes to busybox.

---

