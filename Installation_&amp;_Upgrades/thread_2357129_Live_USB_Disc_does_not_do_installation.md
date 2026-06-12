---
title: "Live USB Disc does not do installation"
date: 2017-03-30
forum: Installation &amp; Upgrades
---

### Post by xenon3 on 2017-03-30
I made a Live USB Disc with PenDriveLinux on a 29 Gb external hard disc, I also made 2 Live USB Stick that way. All do not give:

-Check drive for errors
-Try UBUNTU before installing
-Installer

PS: I get the menu, so there cannot be anything wrong with the USB port

first cryptic errors in kind of terminal screen, then after a couple of minutes the UBUNTU busy screen, goes on forever, never the GUI or Installer Wizard.

1 year ago I made also a Live USB Stick the same way, was working fine, these 3 ones above I made from a fresh copy 14.04.03 i386, so they were freshly made, so they cannot be corrupted

---

### Post by sudodus on 2017-03-30
- Have you checked the [md5sum](https://help.ubuntu.com/community/UbuntuHashes) of the iso file?

- Have you tried one of these drives in another computer?

- Have you tried another tool to create a USB boot drive from the iso file?

- Cloning is a reliable method to create a USB boot drive from the iso file.
. In linux you can use [mkusb](https://help.ubuntu.com/community/mkusb) or 'Disks' alias gnome-disks.
. In Windows you can use [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

-o-

If you have problems also with a cloned USB boot drive, there is some other problem, either booting your computer, or later on in the process with some hardware driver, for example a driver for graphics or wifi.

- Please let us know more details about what is happening and

- please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Are you booting in BIOS mode or UEFI mode?

---

### Post by xenon3 on 2017-03-30
> **sudodus said:**
> 

A - Have you checked the [md5sum]("https://help.ubuntu.com/community/UbuntuHashes") of the iso file?

B - Have you tried one of these drives in another computer?

C - Have you tried another tool to create a USB boot drive from the iso file?

- Cloning is a reliable method to create a USB boot drive from the iso file.
. In linux you can use [mkusb]("https://help.ubuntu.com/community/mkusb") or 'Disks' alias gnome-disks.
. In Windows you can use [Win32 Disk Imager]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb")

-o-

If you have problems also with a cloned USB boot drive, there is some other problem, either booting your computer, or later on in the process with some hardware driver, for example a driver for graphics or wifi.

- Please let us know more details about what is happening and

- please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

D - Are you booting in BIOS mode or UEFI mode?



Letters see quote
     
A - No I dont know how to do that under Windows 8.1, please tell me

B - Yes to the same effect on computer X, with old USB Live Stick, that also I did try on target computer Y, that old Stick was fine a year ago on X, but not anymore, also did try it on Y did not work also, so I thought Stick corrupted, made 2 new USB Live Sticks and a USB Live Disc, did not work on Y and I cannot test on X anymore

C - No

D - I think its UEFI, let me check, I must then leave this Windows environment, but first finish this post reply

---

### Post by sudodus on 2017-03-30
A. You can use the separate Windows tool ***md5summer*** or do it with [***Win32 Disk Imager***](https://wiki.ubuntu.com/Win32DiskImager/iso2usb): 'MD5 Hash'

---

### Post by xenon3 on 2017-03-30
> **sudodus said:**
> A. You can use the separate Windows tool ***md5summer*** or do it with [***Win32 Disk Imager***]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb"): 'MD5 Hash'

I don't see how the md5summer is working

I checked with Win32 Disk Imager MD5 which was fine, thanks, however I think that app only clones image files and not iso files, there is no further functionality than several checksums for iso's (menu grey, not working).

BOOT OPTION IN BOOT MENU: USB Hitachi XXXXXXXXXXXXX (is my external hard disk connected to the special bootable USB poort)

One of the errors during "Try UBUNTU before installation" is: 13.048024] sd 6:0:0:0 [sde] No caching mode page found

All errors disappear quite fast, so I could only write this one down

> **sudodus said:**
> A. You can use the separate Windows tool ***md5summer*** or do it with [***Win32 Disk Imager***]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb"): 'MD5 Hash'

I got it now, there was power interuption on my external hard drive, and WIN32 Disk Imager see of course only the removable drives, so he saw nothing, therefore I had not the write option, now I could make the clone

HOWEVER: Same error same behavior with this Win32 Disk Imager clone (seems to be the installation disk (there is no menu)

System ACER/ RAM 2 Gb / BIOS build 2009

I don't know the other stuff, driver is unlikely MEDION 2011 and this ACER 2009 behaved the same, unlikely that two completely different computers would all have a driver issue, moreover the MEDION worked fine a year ago

---

### Post by sudodus on 2017-03-30
I think that the system ACER/ RAM 2 Gb / BIOS build 2009 boots in BIOS mode while the MEDION 2011 with Windows 8.1 probably boots in UEFI mode (at least if Windows 8.1 was installed by the manufacturer (otherwise, if upgraded from Window 7, it might boot in BIOS mode).

2 GB RAM is a bit lean for standard Ubuntu. That computer might work better, if you try an Ubuntu flavour with a lighter desktop environment,

- ultra-light ***Lubuntu***
- medium light ***Ubuntu MATE*** or ***Xubuntu***

There might be a problem to find a suitable driver for graphics or wifi. You can try to boot with a boot option, for example **nomodeset** according to the following link and links from it.

[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

---

### Post by xenon3 on 2017-03-30
> **sudodus said:**
> 

I think that the system ACER/ RAM 2 Gb / BIOS build 2009 boots in BIOS mode while the MEDION 2011 with Windows 8.1 probably boots in UEFI mode (at least if Windows 8.1 was installed by the manufacturer (otherwise, if upgraded from Window 7, it might boot in BIOS mode).



Does it only work with UEFI boot?

The MEDION, which is now broken by the way (cannibalized), said specific in boot menu: UEFI: ScanDisk (which was my LIVE USB Stick with the Ubuntu from the iso) I booted lots of times from this stick and finally did an UBUNTU installation with it. I had an encrypted installation with a fixed boot sector, so I could not update / upgrade, I thought maybe there was still disk space in boot sector for security updates, so I configured the software updater as such, but all kernel versions got corrupted I think by one failed update.

Anyways I tried to reinstall UBUNTU on the MEDION with this LIVE USB Stick, did not work, made new LIVE USB Stick did also not work, like something changed the workings of the USB ports (I have 2 USB ports that can be used for booting)

What can happen to USB ports? Are they both broken? Strange thing is you see the menu of the LIVE USB Stick.

---

### Post by erasthmux on 2017-03-30
This may or may not be relevant, but with boot issues it's worth a shot. I mean no offense...

Have you double checked whether or not your computer boots in UEFI mode or BIOS mode?

Are you sure what architecture you have? (I.e. 32bit or 64bit (x86_64))

---

### Post by oldfred on 2017-03-30
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr)

The 14.04.3 expired as an enablement stack version. You have to use newest 14.04 or very first one.

---

### Post by xenon3 on 2017-03-30
> **erasthmux said:**
> This may or may not be relevant, but with boot issues it's worth a shot. I mean no offense...

Have you double checked whether or not your computer boots in UEFI mode or BIOS mode?

Are you sure what architecture you have? (I.e. 32bit or 64bit (x86_64))

Oh I'm very honored your first post in this forum, and directly for me, many thanks. Please read posts carefully, I specific said the MEDION boots in UEFI mode [-X

> **oldfred said:**
> [https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr)

The 14.04.3 expired as an enablement stack version. You have to use newest 14.04 or very first one.

I'm a simple man, I don't understand. I can understand that on the ACER the installation does not work because of BIOS boot. But MEDION had UEFI boot and also did not work. Why would the old LIVE USB Stick not install on MEDION again?

I could also understand that maybe someone hacked my BIOS, because on the MEDION it was not password protected, and that someone hacked and made the bootable USB ports not working properly.

PS: ubuntu-14.04.3-desktop-i386.iso package

> **sudodus said:**
> 

[Boot options]("http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808")



I have the first screen but I do not get the second screen with the menu, after a TERMINAL like screen with errors (which lasts maybe a minute or so) I get the UBUNTU busy page which goes on forever

---

### Post by sudodus on 2017-03-30
@xenon3,

- Which screens, please describe what they look like! It will help finding where your boot is failing.

- Were you pressing a key at the first screen with the two small icons at the botton? That way you should arrive at the screen with 'Try Ubuntu', and at that screen you can enter boot options.

---

### Post by xenon3 on 2017-03-31
> **sudodus said:**
> @xenon3,

- Which screens, please describe what they look like! It will help finding where your boot is failing.

- Were you pressing a key at the first screen with the two small icons at the botton? That way you should arrive at the screen with 'Try Ubuntu', and at that screen you can enter boot options.

Thanks for your time, but I have been working on this now for 72 hours with almost no sleep, cannibalizing MEDION building the parts into ACER, then putting the parts back again rebuilding MEDION and ACER again etc. etc., all in order to figure out whether MEDION BIOS is hacked or the old LIVE USB Stick was corrupted, sounds weird he, but internet is my business, my work and my hobby, I admit it I'm addicted to internet, not that I do not have a life too, but internet comes first, when I don't have access to internet I panic, and work very hard to get it back.

I have still that Windows 8.1 installation on ACER, but the CPU cooling fan is sometimes singing, so that's why I did the cannibalizing and stuff, afraid fan is not working properly and CPU gets overheated, OK maybe not.

I rather have UBUNTU Linux because I don't trust Windows, I'm afraid it has backdoors and all other kinds of user hostile stuff build in it, get it? But now Windows 8.1 still feeds my addiction for the time being.

Moreover is it such a hassle to install a simple OS (UBUNTU)? Then I chose for the most simple solution and keep Windows 8.1 (and never upgrade to 10)

---

### Post by sudodus on 2017-03-31
We don't know yet, what is your problem. I *think* there are problems for Ubuntu to communicate with some hardware - Ubuntu cannot find a suitable driver. But there might be some other problem too. The computer that used to work might have some failing part. I don't think malware is causing your problems (possible but not likely).

-o-

It might even be a good idea to buy a refurbished professional class computer of a brand and model, that is known to work well with Ubuntu. It is a good way to get a lot of computing power for the money. For example, a Dell Latitude, HP Elitebook, or Lenovo computer that is 2-5 years old, and sold with 6-12 months guarantee.

-o-

I would recommend some sleep now. After that you are welcome back, and I will try to help you :-)

---

### Post by oldfred on 2017-03-31
UEFI systems have fast boot which is separate from Windows fast start up. That can prevent you from even pressing the UEFI one time boot key to get into booting flash drive. UEFI also has settings on USB boot. Turning on Secure Boot normally turns off USB boot as that is not secure & you have to separately allow USB boot or turn off Secure Boot. Updating UEFI from vendor resets UEFI settings to defaults, so you have to go back an redo all the changes you make.

Windows boots slow and to improve perception of faster boot it requires vendors to add hardware, and do configurations to reduce total boot time.
One change is that UEFI has the fast boot. BIOS & UEFI have to scan system to see what hardware you have and copy that data onto hard drive for operating sytem to use. But fast boot assumes no change to hardware and just immediately jumps to boot. And in most cases you have not changed hardware so it does save some time.

But when you do change hardware or want to get into UEFI/BIOS or even UEFI one time boot key, you do not even have time to press a key. Windows assumes you use its system to boot into UEFI, but when Windows does not work, then it is difficult.
Most set cold (full power down) as full UEFI boot, not fast boot. Some require removing battery and holding power switch so all power is drained.
Some small tablet type systems have a reset pin hole. I think all desktops do have jumper pins on motherboard.

My motherboard's Asus UEFI has fast boot settings for cold boot and warm boot and a number to sec to delay on fast boot. So I add 3 sec just to have time to press a key and have cold boot set as normal full boot, not fast boot.

---

### Post by xenon3 on 2017-06-07
Now I Know I think! I got 2 PCs with a lot of USB ports, 1 PC with one bootable USB port and 1 PC with 2 bootable USB ports, none did the (3) LIVE USB Sticks, also DVD r/w drivers did not work anymore, Now does one of these LIVE USB sticks work in a Packard Bell laptop of maybe 10 years old, could easily do the UBUNTU istallation. No problems so USB sticks not corrupt, also the DVD drive worked like a charm, needed that for LUBUNTU LIVE DVD, because normal UBUNTU is too heavy for that old laptop. 

I think someone has been in the BIOS of my 2 PCs and "rebuild" the drives, wanted to install UBUNTU, but I stuck with Windows 8.1 :(

---

