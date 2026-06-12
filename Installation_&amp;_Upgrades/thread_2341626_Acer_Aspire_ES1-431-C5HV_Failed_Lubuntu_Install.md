---
title: "Acer Aspire ES1-431-C5HV Failed Lubuntu Install"
date: 2016-10-30
forum: Installation &amp; Upgrades
---

### Post by gotabowl on 2016-10-30
I bought the Acer laptop mentioned in the title a couple days ago. It had Windows 10 Home on it which is kind of dumb. It only has 2gb of ram and a Celeron N3160. It also has UEFI which I haven't dealt with before. I tried to do the Rufus USB stick way and it got right up to the Grub 2.02 part and it fails there and declares that it'll send a message that it failed. Is there anything I did wrong? I did use the AMD64 whixh I thought I was supposed to use that one because of the UEFI. Maybe I should've used the x86 version. Probably an earlier version of Lubuntu that wasn't all crazy about UEFI. 

I had a laptop with minimal issues that had Manjaro installed on it for about 6 years and then it just failed slowly . I'd like to get to the problem and revenge all of the fallen laptops and electronics. Here's a link to the laptop I bought just a couple days ago.

[http://www.villman.com/Product-Detail/Acer_ES1-431-C5HV](http://www.villman.com/Product-Detail/Acer_ES1-431-C5HV)

Acer doesn't have a link right off of Google.

---

### Post by Bucky Ball on 2016-10-30
*Thread moved to **Installation & Upgrades**.*

You should be using Lubuntu 16.04 LTS downloaded [from here]("http://lubuntu.net/") if you're not already. If your machine is running UEFI you need the 64bit version. Are you intending to keep Windows? If not, then you don't need UEFI at all if you don't want it.

Did you choose the UEFI option on the USB when you installed? You need to boot to Win and switch off hibernation, boot to the BIOS and switch off faststart, secureboot, and select to boot the USB from the entry with [EFI] next to it.

Have you a plan for how you're going to go about this after that? Does your bootable USB work fine if you choose 'Try Ubuntu' from the options?

It's a bit unclear as to where you got to. You have actually installed it or are trying to? Please try and give all details for quicker support. ;)

---

### Post by gotabowl on 2016-10-30
Sorry I was just really tired and bummed out.

I don't intend to keep Windows at all. It's gone with a half version of the newest download of 16.10 64bit Lubuntu with the torrent. I did check it in Windows to see if the download was downloaded correctly.

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

Well I did boot into the BIOS and saw that there was UEFI and an option for Legacy but from what I've just currently read Legacy isn't the way to go as one of the major options will get through or I'm just not disabling something right.

I did read about the Fast Start and Secure Boot in the BIOS. Do I have to create the password in the BIOS to access the Secure Boot so I can disable it and proceed?

The bootable USB made with Rufus and 16.10 Lubuntu 64bit works fine when I went for just the basic install with nuking everything beforehand. It just got to installing Grub 2.02 and just wrecked. Nothing on the terminal other than that. The live version also works fine. No problems having it do anything. I let my wife's daughter check it out and there were no problems or questions or things that were of concern. I tried two times with the same deal.
Previous to powering on I set the boot order as USB drive _ which it saw a the top, DVD drive, HDD, saved and exited. Powered down.USB is in the laptop. Power on laptop. Lubuntu is seen by the laptop. I went into live mode the first time to see if it was ok because I knew I haven't tread this water yet and wanted to see what was up with Lubuntu and the laptop and if they'd play nice in live mode. They did for an hour, wifi is fine, sound is fine, internet is fine, display is just peachy. Time for clicking the Install Lubuntu icon. The installer wanted to know about HDD settings and what I'd like to do, nuke everything from before now and install Lubuntu 16.10, no encryption, no 3rd party, no home encryption, yes to download updates while it's installing. It goes fine and hangs at the Grub 2.02 install part which I know is near the end before it wants to reboot or send you back to live mode. After hanging it gave a sad message that told me it failed and it's scooping up all of the related information which it sent off to Canonical I guess then opened up Firefox and took me to the Ubuntu forums. I turned off the computer. Powered it back on. I went straight into install Lubuntu. No internet this second time so no updates downloading while installing and no 3rd party installs as well. Same as before without the internet. Same thing, hangs on Grub 2.02 and tells me it's sorry and I believe it went into live mode. I turned the laptop off and went to sleep kind of bummed that I have no idea what I'm doing half the time with computers.

I've had  minimal experience with about 30 or so distros along the way and I've never had UEFI or had the pleasure of having to deal with it. Windows 10 just shouldn't be on a laptop with a Celeron N3160 and 2gb of RAM. Just doesn't seem fair when Windows 10 hogs up 60% of the RAM and about 50-60% of the CPU at idle. While Lubuntu in Live mode gets 1% CPU and like 3% RAM. It's just nonsense.

---

### Post by puntar on 2016-10-30
I also tried for entire day to install Lubuntu (x386) on Asus MeeGo (1GB ram, 8GB SSD ) and on Acer Aspire 5100 (1GB ram 100GB HDD) to no avail.

Both machines have the old bios no uefi! MeeGo do not even have the option for "fast boot"

In both cases installation stopped that grub2 bootlader failed to install! 

I could not do anything after that. Cursor moved as normal, I could choose different partition /dev/sda or /dev/sda1 but click on continue on any option just did not do anything!

I've tried desktop and alternate versions of 32 bit Lubuntu 16.10.

With alternate version installer at least inform me that filesystem cannot be created. I tried with ext2, ext3 and ext4 again to no avail. On both machines!. What I find puzzling is that filesystem was already created???

I even tried using gparted to manually do the partitions but even that did not help. Installer just failed with Grub no matter what.

On Acer I did try with multi booting from USB and leaving HDD as 1st option in bios. Still it did not help!

On the other hand Linux Mint had no problems  installing on Acer Aspire on 1st try.

---

### Post by gotabowl on 2016-10-30
It's kind of a bummer how this difference in the non standard between them makes it really difficult to install Linux. I'll try again later today with some DVDs and or CDs with what Bucky Ball suggested. If anything was the problem I'll try Lubuntu, then Manjaro, then etc. 

I'll report back when I can definitively say that the problem has been resolved.

---

### Post by Bucky Ball on 2016-10-30
sda is not a partition, it a disk. sda1, if its there, should be an empty, EXT4 partition.

Boot the Lubuntu CD, go for an install. Are you making it as far as the partitioning section? If so, choose 'Something Else' and create the partitions then. You need blank space to create EXT4 partitions and a /swap partition with. 

Where are you trying to install grub? During 'Something Else' you will be given the option. *That* should be going to sda.

Are you following one of the many how-tos on how to install Lubuntu? If so, please post a link.

---

### Post by gotabowl on 2016-10-31
Holy guacamole.

I tried turning off Secure Boot. Not any different. Now I'm trying with UEFI turned off like you suggested and I'm trying Legacy Boot.

---

### Post by gotabowl on 2016-10-31
Sorry, an error occurred and it was not possible to install the bootloader at the specified location. 

How would you like to proceed?

There isn't a way to proceed because my only option is /dev/sda which is the 500gb internal laptop HDD. So epic fail. Never had this much fail. Maybe I should just burn a CD/DVD.

---

### Post by oldfred on 2016-10-31
If you have UEFI, you should already have the ESP - efi system partition from Windows.
But if installing in BIOS boot mode to a gpt partitioned drive you have to add a bios_grub partition for grub to install correctly.
Better to use UEFI.

But all new Acers with UEFI have a unique requirement of setting a UEFI password & enabling 'trust' from UEFI on the ubuntu/grub .efi files in the ESP.
Also make sure you have newest UEFI from Acer. Some older threads say to downgrade to older version, but then newer threads say newest UEFI from Acer works.

 Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757) 
      
 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[URL="http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392"]http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392
[/URL]
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 
      
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 
    
Lots of general info on UEFI installs in link below in my signature.

---

