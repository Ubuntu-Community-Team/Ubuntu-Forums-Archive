---
title: "Moving Ubuntu from old to new computer - Easy or not?"
date: 2019-01-24
forum: Installation &amp; Upgrades
---

### Post by josephmmorgan on 2019-01-24
My laptop of 10 years finally fried, and a new one is coming in.  The drives were good, so I can still boot up what amounts to be my old laptop via a SATA/USB connector dangling off of an old desktop.  When the new computer comes in, I want to simply move the apps and home over.  I found this article written back in 2010:

[http://eggsonbread.com/2010/01/28/move-ubuntu-to-another-computer-in-3-simple-steps](http://eggsonbread.com/2010/01/28/move-ubuntu-to-another-computer-in-3-simple-steps)

Old laptop was an Asus GS73SW running 2 500GB Sata drives & 16GB RAM w/1080 17" screen.  It was running 18.04.  Dang good machine BTW.

New  laptop is a Dell Precision 7730.  It will have 2 512GB SSD's w/64GB  RAM w/4K 17" screen.  It will come with 16.04, and I plan to upgrade it  to 18.04 immediately before doing anything else.

Clearly the two aren't the same in any way.  Newer everything. 

Is this really all it takes?

---

### Post by oldfred on 2019-01-24
All you settings & files are in /home, so you also need to copy that over.
If you had saved any system wide customizations like grub settings, those may be in /etc. But hardware based settings you do not want, so best not to copy all of /etc to new system.

It really should be just restoring from your backup. And if you have old drive, then you can find something you missed. But when hardware fails, your backup is your only recourse.

Dell often has some custom drivers. I remember back with 12.04 they needed Sputnik. But by 14.04 all of Sputnik for those systems was included in kernel, drivers & support software. And Sputnik has been updated, but do not know current status.
       Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)
Dell XPS 13 Developer Edition New Kaby Lake 16.04  Sputnik 
[http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml](http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml)
5th Generation Sputnik
[https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/](https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/)
New Haswell Sputnik - Dell orbits Linux a third time with revamped Sputnik notebooks
[http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/](http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/)

Update:
Just saw this, so the drivers for Dell & 18.04 are available somewhere.
       Dell XPS 13 9380 Developer Edition Now Available, Shipping With Ubuntu 18.04 LTS
[https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-13-9380-Developer](https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-13-9380-Developer)

---

### Post by josephmmorgan on 2019-01-24
Great info, thanks.   Ubuntu seems to handle major hardware changes just fine on bootup.  As I stated, I'm running right now booted up off of my Asus drive dangled off of a USB port of an HP Pavillion desktop.  Everything runs (albiet much slower because of 1/2 the CPU and 1/2 the memory).  

So I'll play it safe and fully backup the new Dell exactly as it arrives before upgrading it to 18.04, and certainly before copying over everything.  The good news is, I have the entirety of my old Asus (drive/apps/files) right here.  I really have nothing to lose.

---

### Post by oldfred on 2019-01-24
Note also that older systems are probably BIOS/MBR, only systems in last 5 years since Windows 8 was released have UEFI hardware.

All new systems are UEFI with gpt partitioning.

---

### Post by josephmmorgan on 2019-01-24
OK.  Now that's a good point to make being both of these computers (the ASUS and the HP I'm booting from) are pretty darned old.

So, would this be a good test.  As soon as I get the Dell, before doing anything, dangle the ASUS HD off the DELL and boot directly from it???  Considering the differences you mention, would that work at all?

---

### Post by oldfred on 2019-01-24
With UEFI there are really three boot modes. Not sure what Dell uses for pre-installed Ubuntu.
Windows defaults to UEFI with Secure Boot on but will boot with Secure boot off.
And UEFI has legacy support for BIOS boot.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

With Windows systems you normally turn off UEFI Secure Boot. And many systems just call it "Windows" or "Other", but fine print somewhere will say to use Other for Windows 7 as it does not support UEFI Secure Boot. Windows 7 can be installed in UEFI or BIOS boot mode,depending on how installer is booted.
Same with Ubuntu, how you boot install media UEFI or BIOS is then how it installs.
Or with new systems you always want to boot in UEFI boot mode.
      
 Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Even if new Dell, you may need UEFI update and SSD firmware update. But if Ubuntu installed, it may have those updates, as that is often a issues on the Dell Windows systems. But best to check.

Dell is now one that will let you update UEFI & firmware from Ubuntu.
       
 UEFI/BIOS updates brand model list  for Dell with (uefi >= 0.6.2 & dell >= 0.7.3) 
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
fwupx64.efi
[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)
fwupdmgr get-devices
fwupdmgr get-updates

---

### Post by josephmmorgan on 2019-01-24
The good news is (and I hope this is true), the Dell has never had Windows on it (and won't ever) and also will not need dual boot.  It should come pure 16.04 Linux.  Thanks for all the references.  They might come in handy.

---

### Post by oldfred on 2019-01-24
Hard drives have become so large, that I do not know what to do with all the space.
I was upgrading with every 6 month release, but my wife complained about all the changes, so I keep my main working install as the most current LTS version. But to see changes, I install each release to see changes.

So then in testing or trying out interim release, I want my data, so I keep a larger data partition and use smaller / (root) partitions of 25 or 30GB.
So my Haswell system has 14.04, 16.04 & 18.04, plus now 19.04 for testing. I really prefer new clean installs. I was originally going to alternate / , but have enough space that I, have not overwritten all the old test  / partitions.

---

