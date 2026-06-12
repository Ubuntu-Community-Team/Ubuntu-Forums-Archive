---
title: "grub boot loader failed to install"
date: 2016-05-01
forum: Installation &amp; Upgrades
---

### Post by grahamadgo on 2016-05-01
Hi I have just tried to install Lubuntu 15.10 on a 3yr old laptop, and am getting the message " the 'grub-efi-amd64-signed' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot. "

Followed by the message saying that the installer has crashed and the integrated bug reporting tool will collect data etc.

The the screen freezes.

What's the best plan of action, or could it just be that the hard drive has had its day?  

Cheers

Graham

---

### Post by oldfred on 2016-05-01
Lets see if this shows anything:

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by grahamadgo on 2016-05-01
Hi, thanks for the links, the URL from boot-repair is [http://paste.ubuntu.com/16180962/](http://paste.ubuntu.com/16180962/)
thanks

---

### Post by Bucky Ball on 2016-05-01
Although this is off-topic, may be worth mentioning. 15.10 support ends in just under two months. You may be better served installing 16.04 LTS, a long-term support release which is recently released and is supported until 2021. 

So, strange, you seem to have 15.10 installed but on sdb, your second drive and only have the EFI partition on sda. Did you use 'Something Else' and do that intentionally? Anyhow, you're in good hands with oldfred so I'll leave you to it. Good luck.

---

### Post by grahamadgo on 2016-05-01
Hi bucky ball. thanks for the info I used the 15.10 iso that i downloaded a whike ago, didnt realise that a LTS had come out since. I'll have to do that later as I only have 2 USB's - the one that I am using now and a 1GB one with gparted on. I have a history of messing them up so i cant put bootable iso's on them a second time so daren't try 16.04 just yet.

Regarding the 'something else' option, Its very possible I selected that as I tried several times to install and did click on that  Unfortunately trying the 'trial nd error' method

---

### Post by Dennis N on 2016-05-01
At first glance, looks like your only EFI system partition for grub is sdb1 (see line 71 of your summary), but Ubuntu's installer in UEFI mode won't install grub  there - it always goes to the first sata drive (sda) which appears to be an FAT32-formatted flash drive and doesn't have an EFI system partition to use.

So that may be the problem.

---

### Post by grahamadgo on 2016-05-01
Hi denis,  thanks for the reply.

Sorry, you lost me with the description. my technical knowledge is pretty basic. Areyou saying that the main partition is in the wrong format?  The USB flash drive is the live USB that I used to install (and am currently using under the 'try lubuntu without installing' 

cheers Graham

---

### Post by mc4man on 2016-05-01
I see this exact error recently when trying to install 14.04.4 & actually today when trying to install ubuntu-studio 16.04.
I both cases set the bootloader to install to sdb which is my internal ssd & currently has 16.04 ubuntu & 14.04.3

I'm thinking it's either an issue with an unetbootin created disk or some flaw in Ubuntu in general. I wonder why it wants to install the signed grub-efi package when I'm not using secure boot & have no need for it  (the 'regular' grub-efi is what's being used..

In the case of ubuntu-studio the install hung on that error so I just force restarted & was surprised to boot up ok, my previous 16.04 was still first listed in grub & ubuntu-studio was shown, (3rd listed) & I could pick it & log in, ect. Obviously without the prior installs then a boot up wouldn't work.

Maybe try a different method to create your install usb other than unetbootin

---

### Post by oldfred on 2016-05-01
I have had issues where on my desktops, if drives are not in SATA port order, a flash drive will move into the vacant drive.
If you left SATA0 open, then flash may become sda and grub only installs to sda. If you can change SATA port order in system, check that drives start with SATA0, SATA1 etc with no vacant connections.

---

### Post by Bucky Ball on 2016-05-02
> **grahamadgo said:**
> i cant put bootable iso's on them a second time ...

You mean you have issues when you do that? You need to wipe the drive and format as FAT32 before creating any install USB. You're problem could be that your not and attempting to create an installer on a USB which already has data on it.

---

### Post by grahamadgo on 2016-05-02
Hi All, thanks for the replies. 

Mc4man -thanks for the feedback.  I have tried booting from a disc that I know is good and was created through k3b  some time ago. (zorin 11) This disc was used to boot to both hard drives of my main pc.  The install seemed to work fine, However when It comes to restarting it cant fire up. There is a lot of error info on startup which doesn't mean a lot to me but the continuous repetition of the word "error" is rarely a good sign.  [IMG]  Apologies for the size of the image[[IMG]http://i1065.photobucket.com/albums/u396/grahamadgo/2016-05-02%2003.06.29_zpsenygggpb.jpg[/IMG]]("http://s1065.photobucket.com/user/grahamadgo/media/2016-05-02%2003.06.29_zpsenygggpb.jpg.html")[/IMG]
 also did a further boot-repair to which the result was [http://paste.ubuntu.com/16187036](http://paste.ubuntu.com/16187036) although this was also run whilst the laptop was running from the live USB

Oldfred - thanks for info. Sorry, but don't know what that means

Bucky Ball - thanks, wasn't aware of that.

---

### Post by oldfred on 2016-05-02
Is error with flash drive plugged in or with it out.
It says error is on sda, and in Summary Report flash drive is sda.

You also booted flash drive in UEFI boot mode. But drive sdb is MBR(msdos) partitioned which would be for BIOS boot. Any only shows Zorin install.
Drive should be gpt partitioned for UEFI installs. And first (or near beginning of drive) should be the ESP - efi system partition.

Grub only installs to sda, so as long as flash drive is promoted to sda, you will have issues installing grub. If it does install to sda, then you will  have to  manually copy /EFI/ubuntu to the ESP on sdb. And you just about have to partition in advance as any auto install option will not create that.

---

### Post by grahamadgo on 2016-05-02
hi oldfred,

The flash drive was plugged in on both of the boot reports.

I have re-booted using a disc drive with no flash drives plugged in. I also changed it from UEFI to bios before installling. I did however use the same Zorin disc as previously used, with the thinking that it has proved itself ok on other installations.

the installation appeared to be ok and the 'installation complete/ reboot now message' came up. and remove the installation media' which i did. From there though, on booting it brings up the Zorin start logo but then appears to freeze as it tries to start. Particularly on a line saying  'Starting light display manager'

[http://paste2.org/MV843XPK](http://paste2.org/MV843XPK)

Thanks again for your input, and bearing with my limited knowledge :)

---

### Post by oldfred on 2016-05-02
It looks like a normal BIOS install of a Linux system. But do not know Zorin.

What video card/chip?
Since only one system installed you may have to hold shift key from BIOS until grub menu comes up. Otherwise grub normally just jumps to booting and that could be the issue.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by grahamadgo on 2016-05-03
Hi

The processor is a AMD C-70 APU with Radeon HD Graphics x2
Graphics  Gallium 0.4 on AMD PALM (DRM 2.43.0,LLVM 3.6.2)

I managed to replace quiet splash with nomodeset but it still failed to boot.

However I did install Ubuntu as a full install to see if that made any difference, It also failed to boot and coudn't even open the grub menu. After this though I installed Zorin again alongside Ubuntu and reduced the size of Ubuntu. This works!  My reasoning was trial and error and I have no idea why it works.   I will give it a few days to check that it is going to continue to boot and if so will mark the thread as solved.  Many thanks for your help and my knowledge is improved by everyones imput so thanks to all for that.

[http://paste2.org/4cBUWBbc](http://paste2.org/4cBUWBbc)

Cheers
Graham

---

### Post by matteo-dagord on 2016-09-25
Hi, I want to share my experience.
I had the same problem trying to install Mint 17.3 on a laptop where I previously installed other distros (completely removing Windows).
Same problem with Xubuntu 14.4, Ubuntu 15 and other ISOs.
I tried for hours, erasing entrie hard disk, switching to legacy boot, then manually installing grub, then using boot-repair etc. with no luck at all: I still had the same error message.
Eventually, I found out that my live usbpen was corruped and I used another one: it worked like a charm!

---

### Post by oldrocker99 on 2016-10-18
Let me add that, after hosing my system with an experiment, :( I tried ~10 times with a USB (two different ones) and always, GRUB failed to install. I then burnt a DVD and it worked first time. Slower, yeah, but it worked.

Both USB drives were verified first.

---

### Post by bak&#305;r on 2016-12-20
Did you have or created an EFI partition? If there are no other OSes using UEFI, you may need to make one. Allocation of about 256MB is enough. Choose EFI during the partitioning step.

---

