---
title: "Clone a persistent usb install to the actual drive"
date: 2019-04-08
forum: Installation &amp; Upgrades
---

### Post by olds97lss on 2019-04-08
I had created a persistent install of ubuntu on a thumb drive and have now bought another ssd to use in place of the original windows drive in my spare laptop. I have everything setup how I want it on the thumb drive and was curious if there was a way to clone that install over to the ssd without a lot of fuss so I don't have to go through and set everything up again.

The thumbdrive has ubuntu 18.04.2 on it. I used unetbootin to set it up and PDL-Casper-RW-Creator to create the persistent file. I had updated various things in the grub.cfg, txt.cfg and syslinux.cfg files in order for it to work and boot by default into the persistent option so I didn't have to pick anything when I rebooted remotely. Thos updates aren't necessary obviously with the install on the ssd. I don't intend on having it be dual boot or anything, just a straight up ubuntu laptop.

If there's a site or reference I can use, I'd appreciate any help. If not, then I'll spend a couple days remembering all the things I did.

Thanks!

---

### Post by C.S.Cameron on 2019-04-09
I have cloned a persistent flash drive to internal drive using 
```
dd if=/dev/sdx of=/dev/sdy
``` 
where sdx is persistent drive and sdy is internal drive larger than sdx.
Target drive will be completely overwritten.
Any persistent USB you try to boot from the computer will try to use the computers casper-rw file or partition and may not work.

---

### Post by C.S.Cameron on 2019-04-09
Another possibility is to do a fresh install to the internal drive and then copy, (rsync), the USB's home directory to the internal drive.
You then only need to reinstall the programs.

---

### Post by DuckHook on 2019-04-09
> **C.S.Cameron said:**
> Another possibility is to do a fresh install to the internal drive and then copy, (rsync), the USB's home directory to the internal drive.
You then only need to reinstall the programs.
+1

The better solution IMO. A cloned persistent would be half horse, half man. Good luck trying to troubleshoot something afterwards. A standard install is always preferable if only for the community help available alone.

---

### Post by olds97lss on 2019-04-10
Thanks for the help. I ended up just tinkering and doing an install from the persistent usb, which was just a fresh install. Then I installed a few of the apps and apparently corrupted something, then ended up redoing the install 2 more times. lol!

Then I thought I was smart and upgraded to kubuntu... did not care for it and redid the install a 3rd or 4th time since after reading many comments about "uninstalling kubuntu" was potentially problematic down the line...

So now I have a working install of ubuntu 18.04 all updated and with 3 users on it, an admin, my user and a test user where I can install stuff and destroy the user if it gets jacked up again. I was hoping I could use Macrium to clone the drive as a stable backup, then found it's not usable on linux and ran across some other options that are a bit beyond my ability to use effectively. So, if it dies... it dies and I reinstall. Or I go the long way, pull the drive, put it in a sled on my windows machine and clone it that way.

I use macrium monthly to clone my home computers to back up drives I keep in a fire safe as I run SSD's in everything. Then if something happens, I swap the drive and I'm back to a working PC while I order a replacement SSD. Had one of my intel 240GB's die on me after a years worth of use a couple months ago. I was not diligent with my cloning and had to go back 6 months. The drive would lock up any windows machine I tried to access it from, even via an external sled. Which is when I started tinkering with ubuntu on a usb in the first place. For some reason, ubuntu 18.04 didn't have issue with the drive and I was able to recover all my data.

---

### Post by DuckHook on 2019-04-15
I don't know why I am not receiving e-mail notices about replies, but did not see this until now&#8230;

If you wish to experiment on the OS, it makes no sense to keep reinstalling it after gumming it up. A third user is not going to stop OS corruption either. Better to use a VM (with a known good snapshot) to tinker. Breakage is easy to fix simply by rolling back to the snapshot.

---

### Post by olds97lss on 2019-04-15
> **DuckHook said:**
> I don't know why I am not receiving e-mail notices about replies, but did not see this until now…

If you wish to experiment on the OS, it makes no sense to keep reinstalling it after gumming it up. A third user is not going to stop OS corruption either. Better to use a VM (with a known good snapshot) to tinker. Breakage is easy to fix simply by rolling back to the snapshot.

In the end, I wanted it as the OS on an older laptop. When it got corrupted, the admin user I had created still worked fine, it was only the secondary user I was using that seemed to get messed up. If I booted and logged in as the other user, it started up ok, but if I used the damaged user, it would flash the screen a few times, then take me back to the user select screen.

It's been fine so far and I don't intend on tinkering with it much. I just use that laptop for internet really vs using my phone when in the living room. If I want to tinker with things again, I'll either put in a different drive or play around with the usb persistent install.

---

