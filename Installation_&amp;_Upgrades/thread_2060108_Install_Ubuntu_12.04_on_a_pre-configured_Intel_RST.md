---
title: "Install Ubuntu 12.04 on a pre-configured Intel RST SSD"
date: 2012-09-19
forum: Installation &amp; Upgrades
---

### Post by kfox86 on 2012-09-19
I just purchased a Dell XPS 8500 that ships with 2TB of mechanical HDD + 32 GB of SSD preconfigured to use Intel RST. It seems like RST isn't supported in linux so I'd like to take advantage of the 32GB SSD and install Ubuntu on it rather than use it as a cache for windows. From what I understand these are the steps I need to take:

1. Disable Intel RST from the RST GUI in windows
2. Set both HDD and SSD to non-RAID mode (AHCI)
3. Install Ubuntu on the SSD (all of ubuntu including GRUB)
4. Install Win 7 on the HDD (will unplug the SSD so that Win 7 doesn't mess with the SSD)
5. Add an virtual entry in GRUB to be able to dual boot into Win 7.

End result should be, Ubuntu in the SSD completely silo-ed from Win 7 in the HDD and the ability to boot into either from GRUB.

Could someone confirm this will/will not work and if it won't let me know what steps I'm missing or if I'm just mis-understanding the whole thing.

---

### Post by darkod on 2012-09-19
After step 2, add step 2a: Remove dmraid (meta raid) data from both disks. It will remain there since Intel RST configures them in some sort of weird raid.

Boot the ubuntu cd in live mode first, and in terminal:
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

Except for this added step, what you described should work just fine.

---

### Post by oldfred on 2012-09-19
Some that have done the same thing. As Darko says your procedure should work.

 Intel Smart Response Technology & Dell XPS
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

---

### Post by kfox86 on 2012-09-19
[removed duplicate post]

---

### Post by kfox86 on 2012-09-19
darkod, oldfred Thank you for confirming. I've been researching the correct way to do this for 2 days now after someone else on StackExchange superuser said that I probably wouldn't be able to use the pre-configured SSD SRT as a regular SSD to boot Ubuntu. But theoretically I couldn't figure out why not (unless some special hardware wiring since this box is supposed to come pre-configured).

[EDIT] My box just got delivered so I'm going to go through the process tonight. I'll post my result here.

---

### Post by kfox86 on 2012-09-20
UPDATE: I went through the steps mentioned above, additionally, I dmraid -E -r /dev/sdb. I was able to install ubuntu no problem, and GRUB magically picked up the windows boot loader from sda (so I skipped the virtual mapping part for GRUB). Do also have to dmraid /dev/sda? 

Also when I opened up the computer I noticed that the SDD was actually attached to the HDD and only had ONE SATA and power cable for both. I've never seen this configuration. Is this a hybrid drive?

---

### Post by darkod on 2012-09-20
If it works you don't need to dmraid /dev/sda, although it shouldn't delete any data if you do.

I mentioned doing it on both disks as a precaution since I don't know the exact setup of Intel RST.

---

### Post by kfox86 on 2012-09-20
Thanks darkod! Windows boots fine, but since it is on AHCI mode now I just wondering if it was good practice to have the RAID meta data removed from HDD as well. I'll play around with it once my Ubuntu is stable enough.

Do you have any ideas about what that HDD+SSD combination might be? I was expecting two different drives, but found one that was attached to another and only one SATA and power plugs for both of them. I'm wondering if the SSD's performance is negatively impacted since it is "sharing" the bandwidth (cable) with the mechanical drive.

---

### Post by darkod on 2012-09-20
Unfortunately I have no idea why the disk is made like that. Yes, that might be a hybrid disk (never seen one of those).

As for speed impact, you are right in having doubts, but again, I have no idea what and how big the impact would be. The logic says that there should be an impact when sharing the same SATA data cable, but who knows.

Mechanical HDD can't fill much of the data cable anyway, so there might be enough bandwidth in the cable left for the SSD to fire up.

---

### Post by kfox86 on 2012-09-20
Yea I'll do some more digging when I get home and can actually find the brand and model no. of this weird drive. As for the speed, SATA III has 6Gbits/s = 750MB/s bandwidth and if I assume the HDD's speed is 150MB/s and SSD 540MB/s that's still only 690MB/s so I guess they won't use up the entire bandwidth, although in reality there may be some performance degradation. I ordered a 128GB SSD so I'll post some bench marks once I get everything up and running on the new SSD. Thanks!

---

### Post by oldfred on 2012-09-20
I have not seen how they do these shared drives, but I doubt that the daisy chain of the SATA port matter much.

From my system

SSD speed
fred@fred-Precise:~$ sudo hdparm -t /dev/sdd4
/dev/sdd4:
 Timing buffered disk reads: 626 MB in  3.01 seconds = 208.20 MB/sec
Older 160GB rotating drive.
/dev/sdb4:
 Timing buffered disk reads: 212 MB in  3.01 seconds =  70.46 MB/sec

That was bytes and SATA is in bits. and there is overhead so you never get what they say.
SATA II - 3.0 Gbit/s
SATA revision 3.0 (SATA 6 Gbit/s)

My SSD is a slow one on a SATA2 port.  Some new high speed one's may be stated to be twice as fast, but how read is done also changes results.

Do not know enough of inner workings on whether those make a difference also.

---

