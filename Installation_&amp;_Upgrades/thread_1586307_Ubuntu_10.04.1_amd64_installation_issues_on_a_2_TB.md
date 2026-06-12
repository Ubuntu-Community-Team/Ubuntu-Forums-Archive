---
title: "Ubuntu 10.04.1 amd64 installation issues on a 2 TB hard drive"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by larcif on 2010-10-01
I want to install Ubuntu 10.04.1 AMD64 on a new Athlon II X4 635 with 4 GB RAM.

At first, I had a working installation using the alternate installer from a USB stick, using a 500 GB disk with encrypted LVM.

Then I wanted to use a 2 TB disk instead, but after installing exactly the way I did before, the system didn't boot. After letting me enter the encryption key, the boot process didn't continue. Switching to text mode revealed that the kernel went into a kernel panic, after some message I interpreted as a problem locating some device (stupidly, I forgot to write it down).

Next thing I tried was an installation using an older 10.4 x86 alternate install CD, without encryption and using only a 20 GB LVM. Installation took a lot longer than I would have expected (don't know how long exactly, but at least 1.5 hours), but at least it went through and worked afterwards. So it seems it's either the installation from USB, or amd64, or the encryption, or the LVM or partition size - or a combination of these factors - causing the problems...
  
Now I burnt the 10.04.1 amd64 installer to a DVD, suspecting that maybe with the USB stick present at installation time, there might be a mixup with device names later or something like that. This installation is running right now, and has been for over THREE HOURS - now being at 33% in the section "Select and install software". Surely this must indicate some underlying problem... I have never seen an installation taking that long yet.

When I switch to another virtual console and poke around a bit, the system seems perfectly responsive, as you would expect from a quadcore machine. I can't even hear the hard drive work. It seems as though the installer worked in slow motion.

Are there any known problems concerning volume size, disk size, maybe in conjunction with amd64? I'm at a loss to explain this.

EDIT: Just discovered hdparm on the installer system:

```
~ # hdparm -t /dev/sda

/dev/sda:
 Timing buffered disk reads:    4 MB in  7.49 seconds = 546.59 kB/sec
```

What's going on there? Why is hard disk access that slow? Can I do something about that?

---

### Post by psusi on 2010-10-01
I wonder if the disk is failing.  Fire up the livecd and open the disk utility and take a look at the SMART values for any alarming statistics.  You might also run a full disk check, but for a 2tb drive that will probably take a good 10 hours or so.

You might also check dmesg to see if the kernel is throwing any errors.

---

### Post by srs5694 on 2010-10-01
What kind of disk is it (brand and model)? Some disks, mostly from Western Digital, now use "Advanced Format" technology that requires special care in partitioning. For details, see [this article](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) I wrote on the topic for IBM developerWorks. If this is the problem, the solution is fairly simple, although you may have to pre-partition the disk using suitable software rather than let the installer do it automatically.

---

### Post by psusi on 2010-10-01
10.04 and later already handle that, and even if not, does not explain THAT much of a slow down.

---

### Post by srs5694 on 2010-10-01
> **psusi said:**
> 10.04 and later already handle that, and even if not, does not explain THAT much of a slow down.

10.04 and later may partition correctly for such disks, but the original post is unclear about how the disk was partitioned. It might have been done outside of the installer. It could also be that the "XP compatibility" jumper was set, which would mess everything up.

That said, you're right that the extent of the problem is extreme. I didn't pay much attention to the hdparm results when I posted my first reply, and those results are very bad -- on the order of 100 times worse than they should be. hdparm also isn't likely to be affected by partition alignment, particularly not when used on the main drive.

Overall, then, I'd say that it's still worth checking this issue, but it's not a very likely cause.

Your suggestions to check the SMART status and dmesg output are good ones.

---

### Post by larcif on 2010-10-02
Thanks for your answers. In fact, this is a Western Digital disk:

```
=== START OF INFORMATION SECTION ===
Device Model:     WDC WD20EARS-00S8B1
Serial Number:    WD-WCAVY2539624
Firmware Version: 80.00A80
User Capacity:    2,000,398,934,016 bytes
```Can't image it having something to do with the partitioning issues you mentioned, since I had the installer handle that, and more importantly had it handle it on the previous machine without any of the current problems.

There are no jumpers set on the disk, compatibility or otherwise.

I'm pretty sure too though it has something to do with the disk. I remember running an extended SMART test some weeks ago with no errors turning up. Short tests were scheduled daily and never showed any problems as of yet.

BUT: At the first few installation attempts dmesg didn't show anything interesting. At the latest one though, again with the 10.4 x86 CD, only this time trying to use not only 20 GB but the whole 2 TB, the ext4 creation failed (this never happened before), and  the following lines repeat themselves in dmesg:

```
sd 2:0:0:0: [sda] CDB: Read(10): 28 00 00 07 b9 88 00 00 08 00
end_request I/O error, dev sda, sector 506248
sd 2:0:0:0: [sda] Unhandled error code
sd 2:0:0:0: [sda] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
```I checked smartctl -A, which shows me 78 reallocated sectors now. Must have happened pretty recently. I started  another extended test before leaving for work today, hopefully it's going to  be done when I'm back home.

---

### Post by larcif on 2010-10-02
HDD indeed has an error...

```
=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       20%      1927         3414691456
```

I hope that's all there is to that problem :)

---

### Post by psusi on 2010-10-02
Oh oh.  Time to RMA.

---

### Post by larcif on 2010-10-02
Yep - shouldn't be a problem though, the disk is less than 6 months old.

When i have a new disk, I'll report whether I had any more problems with my setup.

---

### Post by psusi on 2010-10-02
Hrm.. is this a WD20EARS drive?  It seems like they hare having some significant reliability problems.  I got a WD15EARS and it passed the tests fine, then I shut down the computer, came back in the morning and it wouldn't even detect the drive.  Got it replaced and haven't had any problems with the new one yet, but I'm keeping a close eye on the smart numbers and testing it from time to time.

---

### Post by larcif on 2010-10-02
WD20EARS, yes. Didn't notice any problems with it up to now, at least there was no corruption in my data yet. However I still immediately replace a drive when it starts to reallocate sectors, things tend to go downward from there...

---

