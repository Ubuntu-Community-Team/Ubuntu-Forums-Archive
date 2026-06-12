---
title: "retooling an SSD cache drive as a boot drive - ASUS S46C"
date: 2014-11-26
forum: Installation &amp; Upgrades
---

### Post by pei-ollllo on 2014-11-26
Hi folks and yes to let you know, this is my first post.

I'm looking for a cheap Ultrabook for non-work based travel.  I spotted a used [FONT=Arial][COLOR=#333333]ASUS S46C for sale.  It has a 500GB HD and an 24Gb SSD.   The SSD is used by the MB as a cache drive.  [/COLOR][/FONT][FONT=Arial][COLOR=#333333]Ultimately, I would want Ubuntu 14.04 (or Kubuntu for a change) on this device.  Dual booting is not essential but 'might' be done just for a technicality, see below.

[/COLOR][/FONT]I'm new to SSD caching and most of what I can find relates to the Intel SRT version but I'm assuming Asus's version is much the same.  It 'appears' to be a function of the chipset/BIOS and software in the current Windows 8 OS is only present to enable & tweak the caching feature, although I have not verified that.

So the first obvious question for anyone who may be familiar with the scenario.....

1. Once enabled, will the caching functionality continue to function after booting into a Linux environment or are there further hooks into the OS?  (If so and Ubuntu did not have a breakdown from it, I would consider leaving it as is and do a dual boot only to retain the Windows tweak tool.)

2. If native Asus SSD caching is not friendly with the Linux kernal, then I'm wondering about two other options.[INDENT]a.) If SSD caching is disabled via the Windows tool, is there any reason I could not blow away all partitions and use the SSD strictly as a Boot drive for Ubuntu. (/home /tmp and swap would go to the HD.  Anything else get written to a lot?)
or
b.) I've never used it but could bcache be utilized in a similar fashion to replicate the Asus version SSD caching in a more Linux friendly way?[/INDENT]

Any shared experience or even predictions would be appreciated before I contact the owner of the used device.  I don't want to have even a small SSD siting there going to waste.

[FONT=Arial][COLOR=#333333]Thanks all,[/COLOR][/FONT]

[COLOR=#333333][FONT=Arial]Murph[/FONT]

[FONT=Arial][Edit][/FONT]
[FONT=Arial]For anyone actually interested in my oddball question.....I found this thread on enabling caching in a very similar hardware platform using Flashcache.  He appears to be using it to just selectively cache his /Home folder but it provides some anecdotal evidence that it can be done.  Although, I'm more interested in a scenario that improves boot times and/or general OS speed than improving access to data, it was still a good find. 
[http://ubuntuforums.org/showthread.php?t=2179297](http://ubuntuforums.org/showthread.php?t=2179297)

[/FONT][/COLOR][COLOR=#333333][FONT=Arial]I'd still appreciate further advice please.[/FONT][/COLOR]

---

### Post by oldfred on 2014-11-26
Most users turned off SRT and installed to hard drive and then turned it back on. It used to be that the Ubuntu installer did not work as SRT used RAID somehow, but now the installer seems to work, but the RAID may interfere with grub installing to MBR(BIOS) or efi(UEFI) correctly. With RAID grub expects to install to the root of the RAID not to a regular partition.

One or two users with larger SSDs like 32GB  and 8GB of RAM only used the 8GB for SRT. Then they used the rest of the SSD for the /(root) partition. And one or two did install / fully to the SSD and left SRT off. You probably still have to remove the RAID meta-data to get installer & grub to work correctly with the SSD.

       Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb


 Asus ASUS Zenbook Prime UX32VD  Windows vs Linux
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_zenbook_gfx&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_zenbook_gfx&num=1)
 ASUS Zenbook Prime UX32VD
[http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1)
[http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1)
[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)

---

### Post by pei-ollllo on 2014-11-27
Thank You OldFred.  
I truly appreciate the effort you put into that very informative answer!!  I now have a plan should I decide to buy the laptop once I see it.

---

### Post by oldfred on 2014-11-27
One user posted that he purchases a middle range system but with hard drive not SSD. But does not even boot Windows, removes hard drive and installs SSD.
He must regularly sell & upgrade as he then says he puts hard drive in and sells system with a "new" Windows install.

---

### Post by pei-ollllo on 2014-12-02
Seller has never replied to my inquiries so I assume the unit I was looking at is already sold.
Sorry, i won't be able to report back on my experience with the SSD.  Unless of course the next one I find has a similar drive mix.

---

