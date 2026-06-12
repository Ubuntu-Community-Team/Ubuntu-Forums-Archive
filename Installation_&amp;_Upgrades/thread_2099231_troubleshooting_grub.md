---
title: "troubleshooting grub"
date: 2012-12-29
forum: Installation &amp; Upgrades
---

### Post by Drone4four on 2012-12-29
Now I can’t load Windows 7 (/dev/sdb2) because the Windows XP partition (/dev/sda2) that hosted the Windows loader became corrupted.  Actually, every partition on /dev/sda is now toast.  When I select the Windows Loader I get this:
```

error: no such device: 9464AC0864ABEAE6
error: no such partition

```

How do I re-configure grub2 to load Windows 7?  

Boot-repair generated [this]("http://paste.ubuntu.com/1474855/") pastebin file.

---

### Post by fantab on 2012-12-29
So you have two HDD, /dev/sda and /dev/sdb? 

What did you have on /dev/sda other than WIN XP?
You have Win7 and Ubuntu on /dev/sdb?
Where did you install Grub2 originally? on /dev/sda or /dev/sdb?
Can you boot into Ubuntu?

You may have to install Grub on /dev/sdb using Ubuntu LiveCD and then from BIOS change the HDD boot order to boot /dev/sdb first.
Also using Ubuntu LiveCD- Disk Utility check the Smart Status of your /dev/sda...

---

### Post by NikTh on 2012-12-29
Hi ,

as you can see from the report of boot-repair (boot info summary) the /dev/sda1 is corrupted and cannot be mounted. Probably this is your problem.

I'm not sure but I think that boot-repair offers the option to repair the filesystem of a partition. 

See the "Other Options" and search for it. 

If you cannot find it , you can do this manually from a Live CD of Ubuntu. 
Open a terminal and apply the commands 
```
sudo mke2fs -n /dev/sda1
```see the numbers where SuperBlocks are stored .. the first number maybe is 32768 (if is another number , use another number - the first available)  , use this number  to try to fix the errors. 
```
sudo e2fsck -y -b 32768 /dev/sda1
```after above command finish .. then run again the [Recommended Repair] from boot-repair program and reboot.

Thanks

---

### Post by darkod on 2012-12-29
In this situation there is no way to make grub2 boot win7 because you are missing the win7 boot files (they were on the XP partition as you said yourself). Grub2 only detects the boot files and passes on the process to them. With the boot files missing, no way to boot win7.

What you can try is the win7 repair process using the win7 install dvd. First use Gparted in ubuntu and set a boot flag on sdb2. Windows depends on the boot flag.

After that boot the computer with the win7 dvd and use the Repair This Computer option. There are two ways, letting it do it automatically, or manually, which ever you prefer. Note that you might need to run the auto repair few times before it's done, that's how windows repair works. Also note that it might delete grub2 from /dev/sda if it decides to put the windows bootloader there. But restoring grub2 is eays, just have the 12.10 live cd at hand.

Apart from the win7 boot files issue, you can see that you are using grub2 in some sort of embedded situation. I have no idea why, or how you installed it. I would reinstall it again without the embedded file, so that it runs as it should by default. But that is my preference, you can keep using it like this if you prefer and if it's working.

---

### Post by Drone4four on 2012-12-29
@**fantab**:  I think your questions have been answered either in my pastebin file or by the other posters.


@**NikTh**: I couldn't find an option in boot-repair to fix a corrupted disk, but there is an option in GParted to do this.  I ran that utility but it was not successful.  Before that I also resorted to a guide written for Ubuntu users that I found using Google.  This guide was indended to help people use forensic software to fix corrupted disks.  That was a big mistake b/c it corruped the other 3 or 4 partitions which were otherwise fine.  As for the e2fsck and mke2fs commands, I'm not sure what they'll do so I don't want to try them.  I suppose I could read the man pages, but first I am going to do what **darkod** advises  b/c I know exactly what he suggests.  I have already set the bootable falg to /dev/sdb2 using fdisk.  I am about to boot my live Windows 7 disk and use the "Repair this Computer" option.  After that I will load my Ubuntu live DVD to run boot-repair.  Whether I succeed or fail, I will report back here.  

Cheers...

---

### Post by Drone4four on 2012-12-30
When I booted the only Windows 7 installation disk I had, it went directly to the &#8216;Collecting Info&#8217; screen and asked me to check the License Terms.  There was no opportunity for me to click repair or install.  So I pirated another Windows 7 iso.  I booted it, and this time it gave me the option to repair, but when I selected the partition to be fixed, it gave me an error message saying that the Windows 7 disk is incompatible with the O/S installed on the partition.  Ugh...so I just formatted the drive. 

/me mumbles curse words to himself about how pathetic Microsoft's operating systems are.

Now Windows 7 and Ubuntu 12.10 are accessible through Grub.

---

