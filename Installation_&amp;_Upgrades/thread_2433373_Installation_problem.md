---
title: "Installation problem"
date: 2019-12-18
forum: Installation &amp; Upgrades
---

### Post by paapu on 2019-12-18
Dear All,

Failed to install ubuntu 18.04.3 or 19.10 to Lenovo Yoga S740 laptop.
Problem is that when I try to install Ubuntu  it does not see the hard drive doing ubuntu installation using usb stick.

With 18.04.3 usb installation, after selection of keyboard, language and updates, the problem is with the screen has top left: "Installation type", upper box is empty, lower has /dev/sda
When clicking install now, it complains about "No root filesystem is defined"
Pressing "+" crashes the installer.

I tried various boot-option combinations with no success.

Is the laptop just too new?

Sorry for my previous post, I did not know it was prohibited to ask people who know answer to my question. 

Terveisin, Markus

---

### Post by QIII on 2019-12-18
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2431097](https://ubuntuforums.org/showthread.php?t=2431097)

Please do not horn in on other users' threads, particularly with unrelated issues.  It is not fair to the OP and is not likely to get you the help you need.

---

### Post by paapu on 2019-12-18
Dear Qlli,
Could you rename this thread to something a bit more informative, I did not manage that.
Markus

---

### Post by yancek on 2019-12-18
> Problem is that when I try to install Ubuntu  it does not see the hard drive doing ubuntu installation using usb stick. 

Which means the drive is new, is unformatted  and has no operating system on it, is that correct?  If not, you need  to post that information.

On the Installation Type screen, you need to set the mount  point for root which is the " / " forward slash symbol.  That is why you get the error  "No root filesystem is defined".  The link below is a tutorial on installing Ubuntu and about half way down the page, there are several images showing this option when you have the "Create partition" window.

[https://www.linuxtechi.com/ubuntu-18-04-lts-desktop-installation-guide-screenshots/](https://www.linuxtechi.com/ubuntu-18-04-lts-desktop-installation-guide-screenshots/)

---

### Post by paapu on 2019-12-18
Sorry,
It has windows 10 which is working fine. 
I'd like to make it dual boot (or just ubuntu if that's too hard).
Tervesin, Markus

---

### Post by oldfred on 2019-12-18
Many, even new, need UEFI update & SSD firmware update.
You need to turn off bitlocker & Windows fast start up.
In UEFI you may want to turn off UEFI Secure boot, and need to change to AHCI for drives. If dual booting with Windows you need to add AHCI drivers first or Windows will not boot with AHCI setting.

You probably need the newest version of Ubuntu to have latest kernel & drivers.
If willing to experiment, you can try the 20.04 which will not be released until April 2020, but is getting daily updates and has even newer kernel. You should plan on re-install (but do not have to) as it will have a lot of updates before April and log files & history will be larger than normal. Note that it may also have short term breakage as some update may not work. I have it installed but use 18.04LTS and only use LTS versions as main working install.

---

### Post by paapu on 2019-12-18
Dear Oldfred,

I'm very willing to try out things to settle this problem, it is first time since 90's I have failed to install linux...

>Many, even new, need UEFI update & SSD firmware update.
Not done. I try to google this...
>In UEFI you may want to turn off UEFI Secure boot,
Done earlier.
> and need to change to AHCI for drives. If dual booting with Windows you need to add AHCI drivers first or >Windows will not boot with AHCI setting.
Done earlier so that AHCI was set on , machine did not work at all, so took windows back with a backup-usb, and now it has AHCI. Did not update any AHCI drivers, but maybe windows was able to figure that out.

Additionally I changed something to legacy, can't remember what it was..

So please give some guidance how to proceed, where to get 20.04 for instance...

terveisin, Markus

---

### Post by oldfred on 2019-12-18
See if version here is any newer than the one you have. Says 13 Nov 2019
[https://pcsupport.lenovo.com/us/en/products/laptops-and-netbooks/yoga-series/yoga-s740-14iil/downloads/driver-list/component?name=BIOS%2FUEFI](https://pcsupport.lenovo.com/us/en/products/laptops-and-netbooks/yoga-series/yoga-s740-14iil/downloads/driver-list/component?name=BIOS%2FUEFI)

Do not turn on any Legacy settings. That is the old BIOS/CSM/Legacy. And all new Windows pre-installed are UEFI. And you want Ubuntu installed in UEFI boot mode, also.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off. 

If interested in 20.04.
[http://cdimage.ubuntu.com/ubuntu/daily-live/current/](http://cdimage.ubuntu.com/ubuntu/daily-live/current/)
or which will start download.
[http://cdimage.ubuntu.com/ubuntu/daily-live/current/focal-desktop-amd64.iso](http://cdimage.ubuntu.com/ubuntu/daily-live/current/focal-desktop-amd64.iso)

But I have not done a full download for a while. I use zsync which compares .iso file with online file and only downloads differences. When changing, for example from 19.10 to 20.04, I make a copy of 19.10's ISO and rename to 20.04's ISO. Daily download file name will be different than final release. But when I zsync daily from last day or two before release, it is 100% the same.

If you rename 19.04 iso, and are in the folder with the ISO. 
       [noparse]
zsync http://cdimage.ubuntu.com/ubuntu/daily-live/current/focal-desktop-amd64.iso.zsync [/noparse]

---

### Post by paapu on 2019-12-19
ok, I tried and failed again with ubuntu 19.10 usb on lenovo yoga S740 laptop

I put screenshots and contents of /var/log in 
> git@gitlab.com:paapu88/lenovos740.git

Hope someone can this better than I ...
(```
git clone git@gitlab.com:paapu88/lenovos740.git
```
all files are gzipped)

I'll try ubuntu20 later...

Terveisin, Markus

---

### Post by yancek on 2019-12-19
Did you update UEFI and SSD firmware as suggested above?
Did you verify that fastboot and anything related to hibernation in the windows power settings were turned off immediately prior to your attempt to install Ubuntu?  Windows turns them back on with some of its updates.  It does not ask if you want them on.  It does not inform you they will be turned on.  THese are the primary reasons you do not see windows partitions in the Installation type window of Ubuntu.  Did you get to the point where you select a partition to use or unallocated space and select a mount point for the / (root filesystem) as shown in the link I posted earlier?

---

### Post by paapu on 2019-12-19
Yes, I have tried all suggestions, additionally I found some "Change advance startup options" which has promising options (see 
[https://gitlab.com/paapu88/lenovos740/blob/master/biosImages/IMG_20191219_174430700.jpg]("https://gitlab.com/paapu88/lenovos740/blob/master/biosImages/IMG_20191219_174430700.jpg")
, tried options 7 and 8 but with no luck. Unfortunately lenovo S740 boots only about every third time from my ubuntu-usb stick, so not sure if it manages to put its safety options back...

Also tried ubuntu 20.04 but neither did it see the hard drive.

Markus

---

### Post by oldfred on 2019-12-19
You also have to have AHCI set for drives.

       Windows AHCI instructions
[https://askubuntu.com/questions/1148120/ubuntu-18-0x-not-detecting-windows-ssd-during-installation](https://askubuntu.com/questions/1148120/ubuntu-18-0x-not-detecting-windows-ssd-during-installation) & 
[https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on#963100](https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on#963100)
[https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/)
AHCI enable - May have to unlock bitlocker if used
[https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243](https://www.tenforums.com/drivers-hardware/15006-attn-ssd-owners-enabling-ahci-mode-after-windows-10-installation.html#post332243)
[https://www.tenforums.com/tutorials/22631-enable-ahci-windows-8-windows-10-after-installation.html](https://www.tenforums.com/tutorials/22631-enable-ahci-windows-8-windows-10-after-installation.html)
Install Windows with larger ESP.
[https://www.youtube.com/watch?v=2ZWu-O3mdzI&feature=youtu.be](https://www.youtube.com/watch?v=2ZWu-O3mdzI&feature=youtu.be)

---

### Post by paapu on 2019-12-20
Thanks,
I had done option 2 in [https://askubuntu.com/questions/1148...g-installation](https://askubuntu.com/questions/1148...g-installation)  earlier.
My disk looks now from windows side:[https://gitlab.com/paapu88/lenovos740/blob/master/biosImages/diskManagement.png]("https://gitlab.com/paapu88/lenovos740/blob/master/biosImages/diskManagement.png")

If I remember correctly, when first using ubuntu-install-usb-stick (having not yet set AHCI and other bios settings), I did see some disk where to install ubuntu, but it was only 16GB, so I thought (probably incorrectly) that is my usb-stick. Maybe all these problems had been avoided if I'd just installed there??? Perhaps I should get rid of AHCI and go back to factory settings. Opinions?

terveisin, Markus

---

### Post by yancek on 2019-12-20
The images you posted above show that your entire drive is occupied by several windows partitions meaning there is no place on the drive on which to install Ubuntu.  Best first step is to use a windows tool such as Disk Management to shrink the largest partition to create unallocated space for Ubuntu if you want to install it.  Also, make sure you have fastboot and hibernation off or the windows partitions will not be shown.

---

### Post by paapu on 2019-12-20
Hello,
Did shrink partition size with  Disk Management, the current situation is:
[https://gitlab.com/paapu88/lenovos740/blob/master/biosImages/diskManagement2.png]("https://gitlab.com/paapu88/lenovos740/blob/master/biosImages/diskManagement2.png")

The situation is unchanged, ubuntu 19.10 usb disk does not see any hard disk.

Fast boot is off (in BIOS settigs), and I could not find any options related to hibernate.

Maybe the Lenovo has figured out some new protection system?

---

### Post by oldfred on 2019-12-20
Some other Lenovo, issues often common across models by vendor. Bigger difference if AMD or Intel.

[https://askubuntu.com/questions/1161675/ubuntu-18-04-does-not-load-sdd-nvme-xpg-gammix-lenovo-gamer-legion-y530?noredirect=1#comment1935970_1161675](https://askubuntu.com/questions/1161675/ubuntu-18-04-does-not-load-sdd-nvme-xpg-gammix-lenovo-gamer-legion-y530?noredirect=1#comment1935970_1161675)
       Lenovo Legion Y520-15I  Installer does not detect SSD and HDD: Ubuntu 16.04 LTS
[https://ubuntuforums.org/showthread.php?t=2359208](https://ubuntuforums.org/showthread.php?t=2359208) 
            Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)

---

### Post by paapu on 2019-12-21
Thanks,
No success so far, I post my bios settings below, som maybe someone spots my mistake

Problem: ubunu usb installer does not see hard disk:
[https://gitlab.com/paapu88/lenovos740/blob/master/biosImages/noDisk.jpg]("https://gitlab.com/paapu88/lenovos740/blob/master/biosImages/noDisk.jpg")

Bios settings screens:
[https://gitlab.com/paapu88/lenovos740/blob/master/biosImages/1info.jpg]("https://gitlab.com/paapu88/lenovos740/blob/master/biosImages/1info.jpg")
[https://gitlab.com/paapu88/lenovos740/blob/master/biosImages/2aConfiguration.jpg]("https://gitlab.com/paapu88/lenovos740/blob/master/biosImages/2aConfiguration.jpg")
[https://gitlab.com/paapu88/lenovos740/blob/master/biosImages/2bConfiguration.jpg]("https://gitlab.com/paapu88/lenovos740/blob/master/biosImages/2bConfiguration.jpg")
[https://gitlab.com/paapu88/lenovos740/blob/master/biosImages/3aSecurity.jpg]("https://gitlab.com/paapu88/lenovos740/blob/master/biosImages/3aSecurity.jpg")
[https://gitlab.com/paapu88/lenovos740/blob/master/biosImages/3bSecurity.jpg]("https://gitlab.com/paapu88/lenovos740/blob/master/biosImages/3bSecurity.jpg")
[https://gitlab.com/paapu88/lenovos740/blob/master/biosImages/4boot.jpg]("https://gitlab.com/paapu88/lenovos740/blob/master/biosImages/4boot.jpg")
[https://gitlab.com/paapu88/lenovos740/blob/master/biosImages/5exit.jpg]("https://gitlab.com/paapu88/lenovos740/blob/master/biosImages/5exit.jpg")

I also tried with openSUSE-Tumbleweed, but also it failed to detect the hard disk.

---

### Post by westie457 on 2019-12-21
When I had a similar problem to yours (mine was on a 'miix 3' tablet) I had to turn off Bitlocker in Windows.

Advice here. [https://forums.lenovo.com/t5/ThinkPad-X-Series-Laptops/How-to-disable-Bitlocker/m-p/4010647#M83252](https://forums.lenovo.com/t5/ThinkPad-X-Series-Laptops/How-to-disable-Bitlocker/m-p/4010647#M83252)

After doing that was I then able to shrink a partition while still in Windows to make room for the installation to go ahead.
I also had some other issues that probably not applicable to your case.

---

### Post by paapu on 2019-12-21
Thanks, but bitlocker has been turned off (that was scary when it went in action) and also there is 100GB unallocated space on HD made by windows disk manager...

---

### Post by oldfred on 2019-12-21
I am not familar with OS Optimized Defaults.
It looks like it really is a UEFI Secure Boot setting?
[https://askubuntu.com/questions/1070217/should-i-enable-os-optimized-defaults-in-uefi-when-dual-booting-windows-and-ub](https://askubuntu.com/questions/1070217/should-i-enable-os-optimized-defaults-in-uefi-when-dual-booting-windows-and-ub)

---

### Post by yancek on 2019-12-21
Disabling and enabling hibernation is explained at the microsoft site below.

[https://support.microsoft.com/en-us/help/920730/how-to-disable-and-re-enable-hibernation-on-a-computer-that-is-running](https://support.microsoft.com/en-us/help/920730/how-to-disable-and-re-enable-hibernation-on-a-computer-that-is-running)

---

### Post by paapu on 2019-12-22
Thank's, switched hibernation off as instructed, but it did not help for seeing the hard drive. Trying next oldfreds uefi suggestions.

**Thanks to you all guys, especially oldfred.**
This message now comes happily from installed ubuntu 19.10 in Lenovo Yoga S740.
Problem was the boot settings (uefi etc).

I went trought all boot settings (got there by F2) and pressed at each screen F9 to get default settings back (it kept AHCI setting intack, however).
Only non default settings are now
1) secure boot off
2) file type AHCI

Additionally on windows side I did (do not know if all this was necessary, probably forgetting something, see previous post in this chain):
- bitlocker off
- hibernate off
- made non-allocated disk space by windows disk manager

To boot from ubuntu-usb had to tap F12. To avoid freezing during ubuntu installation did choose safe graphics mode.

So big thank's again!
 terveisin, Markus

---

### Post by jlakhlili on 2020-05-24
Hi!
I'm thinking to have Yoga S740 14. I'm using ubuntu 20.04 from Dell XPS 15 (because of thermal issues). 
Can you give me please your feedback about the Yoga laptop under Ubuntu, did you have other problems (with wifi, drivers, sound, etc..), what about the fan noise, the battery life?
Did you upgrade to 20.04?
Thanks!

---

### Post by jlakhlili on 2020-05-24
Hi [**[COLOR=#000000]paapu[/COLOR]**]("https://ubuntuforums.org/member.php?u=377978")!
I'm thinking to have Yoga S740 14. I'm using ubuntu 20.04 from Dell XPS 15 (because of thermal issues). 
Can you give me please your feedback about the Yoga laptop under Ubuntu, did you have other problems (with wifi, drivers, sound, etc..), what about the fan noise, the battery life?
Did you upgrade to 20.04?
Thanks!

---

