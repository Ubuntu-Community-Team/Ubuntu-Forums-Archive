---
title: "questions on adding partition for 20.04 root"
date: 2020-04-03
forum: Installation &amp; Upgrades
---

### Post by ray field on 2020-04-03
Getting ready to install 20.04 & need to be sure I plot everything correctly. 

Here is the partition info of my SSD:

```
Number  Start   End     Size    File system     Name              Flags
 5      1049kB  2097kB  1049kB                                    bios_grub
 1      2097kB  211MB   209MB   ext4
 2      211MB   43.2GB  42.9GB  linux-swap(v1)  Linux filesystem
 3      43.2GB  96.8GB  53.7GB  ext4            root
 4      96.8GB  2000GB  1904GB  ext4            home
```

The idea is to shrink the home partition by 50GB (/dev/sda4) and put 20.04 root there. Ideally, I'd rather use gparted to put the new 20.04 root *before* /home -- note I will be sharing /home between both 16.04 and 20.04 -- but does it matter? What's the best way to proceed?

I just booted to the thumbdrive of 16.04 to make a dry run: I noticed that when I "shrank" /home and then tried to "create" the new partition at the end of the drive, the only option was to make it a primary partition -- just curious why I was apparently unable to make it a logical partition.

Also, if I do resize /home a new partition, will the UUID of the current (16.04) root change? Guess if it does, I can simply go into the 16.04 fstab and change root to the new UUID, though I'd just as soon not bother.

And... can I tell 20.04 to use the same swap partition as 16.04 is now?

Any caveats?

---

### Post by CelticWarrior on 2020-04-03
The "bios_grub" partition means you have a legay installation in a GPT drive.
GPT drives have only partitions. Primary and logical is applicable to the old MBR ("msdos") partitioning.

Resizing a partition won't change the UUID.

Yes, the same swap can be used. However, 20.04 as some other previous releases use swapfile instead of a swap partition by default.

---

### Post by oldfred on 2020-04-03
Best not to share /home.
Only if totally upgrading and not using older system. Upgrades are supported, so any changes to configuration files in /home will automatically be done. But those changes may not be compatible with your old install. 
I had some issues with Firefox & Thunderbird profiles for first time in 15 years where update to 20.04 made it not work in my 18.04. I did have backup and restored that to another location. 

I do not have /home partition but use a smaller 25 or 30GB / (root) including /home and then have all my data in separate /mnt/data partition. But I have multiple installs and want to share data, but may want to test some changes in user settings, but not change main working install's settings.

Be sure to have good backups.

---

### Post by TheFu on 2020-04-03
+1 to what oldfred says.

if you do share /home with multiple different versions - either releases or DEs - please, please, use different userids to keep the configuration files separate.  Config files can't be forward AND backwards compatible.  That's a good way to break the GUi sessions.

if there is 1 swap partition, the new install should see it and use it just fine.  I&#8217;m not a fan of swap files for a number of reasons, especially on GPT disks.

/ larger than 25 is overkill.
if you need more storage, there are better techniques.  Sometimes i need more storage space in /var/lib/ for containers or VMs. When needed, I&#8217;ll add an LV/partition there.

---

### Post by Impavidus on 2020-04-04
A 42GB swap partition is overkill too, unless you have 40GB RAM and like to hibernate. Modern computers have so much RAM that swap is almost never used.

---

### Post by ray field on 2020-04-04
Thanks all, nice to see familiar faces. 

After giving it some thought, think I'll just back up 16.04 & then reformat and start 20.04 from scratch. On reflection, fact is when I've installed new LTSs alongside older ones (Lucid/Precise) to give myself a feeling of security, in practice I've seldom if ever booted back into the previous version. 

oldfred, I especially appreciate your noting that changes in configuration files in /home are automatic, didn't realize this. (As it happens, until recently I kept my data in another partition as well -- /usr/local/data -- but backing up with resilio-sync and other applications became cumbersome, so I piled everything back into my /home directory.) 

I really don't know how that swap partition got that big, probably too many zeroes when I created it.

---

### Post by TheFu on 2020-04-04
> **Impavidus said:**
> A 42GB swap partition is overkill too, unless you have 40GB RAM and like to hibernate. Modern computers have so much RAM that swap is almost never used.

There's a recent, long, discussion about swap in these forums with plenty of differing advice. I think any amount over 4.1G is likely more than needed regardless of RAM, but there are always exceptions. Looking at 3 systems here right now, 2 are using 2-4G of swap and one is using zero.  The 16G and 8G machines are using swap, but the 4G desktop is not, at least not at this instance.

---

