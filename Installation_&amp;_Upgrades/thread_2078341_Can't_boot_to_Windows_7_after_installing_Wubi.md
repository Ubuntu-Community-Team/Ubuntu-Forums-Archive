---
title: "Can't boot to Windows 7 after installing Wubi"
date: 2012-10-30
forum: Installation &amp; Upgrades
---

### Post by brightwork on 2012-10-30
Hey all,

I've run into a problem after installing Lubuntu 12.10 via Wubi.  On startup, the Windows boot manager loads as expected with both Windows 7 and Lubuntu as options, but if I choose Windows 7, it loads as far as the black "Starting Windows" screen with the animated Windows graphic and then pretty soon I get a BSOD and the computer automatically reboots.  

Here is my boot info: [http://paste.ubuntu.com/1318784/](http://paste.ubuntu.com/1318784/)

I tried running Boot-repair in Lubuntu, but the recommended repair didn't work.  I also tried Startup Repair using the Windows 7 Repair Disk and it just says that it cannot automatically repair it.

If I boot into Lubuntu (choosing Lubuntu in the Windows boot manager and then again in the subsequent GRUB menu), I can access the files that are part of the Windows partition (shown under /host in Lubuntu file manager) with no problem.

I've found a few threads here regarding similar issues, but I haven't found a solution yet.  Can someone give me some help getting Windows to boot properly?


Many thanks,

Scott

---

### Post by bcbc on 2012-10-31
> **brightwork said:**
> Hey all,

I've run into a problem after installing Lubuntu 12.10 via Wubi.  On startup, the Windows boot manager loads as expected with both Windows 7 and Lubuntu as options, but if I choose Windows 7, it loads as far as the black "Starting Windows" screen with the animated Windows graphic and then pretty soon I get a BSOD and the computer automatically reboots.  

Here is my boot info: [http://paste.ubuntu.com/1318784/](http://paste.ubuntu.com/1318784/)

I tried running Boot-repair in Lubuntu, but the recommended repair didn't work.  I also tried Startup Repair using the Windows 7 Repair Disk and it just says that it cannot automatically repair it.

If I boot into Lubuntu (choosing Lubuntu in the Windows boot manager and then again in the subsequent GRUB menu), I can access the files that are part of the Windows partition (shown under /host in Lubuntu file manager) with no problem.

I've found a few threads here regarding similar issues, but I haven't found a solution yet.  Can someone give me some help getting Windows to boot properly?


Many thanks,

Scott
Have you booted to a Windows repair prompt and run chkdsk?:
```
C:
chkdsk /r
```

I noticed that boot-repair, although it unnecessarily replace the windows bootloader (shouldn't have caused any issue though), it also ran fsck on the root.disk and seemed to find a number of issues - so maybe there is some filesystem corruption causing the BSODs and also the Windows automatic repair failure.

---

### Post by brightwork on 2012-10-31
> **bcbc said:**
> Have you booted to a Windows repair prompt and run chkdsk?:
```
C:
chkdsk /r
```I noticed that boot-repair, although it unnecessarily replace the windows bootloader (shouldn't have caused any issue though), it also ran fsck on the root.disk and seemed to find a number of issues - so maybe there is some filesystem corruption causing the BSODs and also the Windows automatic repair failure.

bcbc,

Thanks for your response.  I ran chkdsk using the repair disk as you suggested and no errors were found.  Is there any other way to see if there might be some corrupt files causing this issue?

Also, it does seem like something's up with Lubuntu, although I don't know if it's related.  I can't write files to the Lubuntu partition when logged in -- although I can write files to the Windows partition accessed under /host in Lubuntu.

Thanks,
Scott

---

### Post by bcbc on 2012-10-31
It's hard to speculate on what might be causing your problem. It's certainly not a typical problem that we see with Wubi use. The booinfoscript identifies certain system information that helps many situations, but not all. The fact that the root.disk has some corruption may be unrelated to the Windows BSODs, but Wubi corruption (more common) tends to be on the NTFS file system (that chkdsk would pick up), not the ext4 filesystem on the virtual disk.

Please can you provide the output of this while booting Lubuntu? (just to see the disk space available):
```
df -h
```

---

### Post by brightwork on 2012-10-31
> **bcbc said:**
> It's hard to speculate on what might be causing your problem. It's certainly not a typical problem that we see with Wubi use. The booinfoscript identifies certain system information that helps many situations, but not all. The fact that the root.disk has some corruption may be unrelated to the Windows BSODs, but Wubi corruption (more common) tends to be on the NTFS file system (that chkdsk would pick up), not the ext4 filesystem on the virtual disk.

Please can you provide the output of this while booting Lubuntu? (just to see the disk space available):
```
df -h
```

It looks like there is plenty of space.  Here's the results: 
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       12G  4.1G  6.8G  38% /
udev            736M  4.0K  736M   1% /dev
tmpfs           298M  840K  298M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            745M     0  745M   0% /run/shm
none            100M  8.0K  100M   1% /run/user
/dev/sda2       148G  140G  7.7G  95% /host
/dev/sr0        505M  505M     0 100% /media/scott/CD_ROM
/dev/mmcblk0p1  7.4G  682M  6.8G  10% /media/scott/6333-3063

```

---

### Post by bcbc on 2012-10-31
There's plenty on the lubuntu virtual disk, but not really on the windows /host. One known reason for BSODs is a lack of space, and you only have 7.7G (5%) remaining. I've read that Windows needs a fair amount to run (not sure how much but it seems that it's more than Ubuntu)

That's a bit of a guess (I don't know exactly how much Windows needs) and doesn't explain why the windows repair disk didn't find anything to repair, but maybe if you can copy some data to a backup device, or eliminate unnecessary data, then you can see whether it resolves the issue. 

At the least, it's a starting point for some investigation as to what might be the problem.

---

### Post by brightwork on 2012-10-31
Could this possibly have anything to do with Lubuntu maybe disabling ACPI during the Wubi installation or something?  I did see an old thread where someone had to repair Windows after a wubi install because of this.

---

### Post by bcbc on 2012-10-31
> **brightwork said:**
> Could this possibly have anything to do with Lubuntu maybe disabling ACPI during the Wubi installation or something?  I did see an old thread where someone had to repair Windows after a wubi install because of this.
I've never heard of this, and also don't see how it is possible to permanently disable ACPI. I've heard of people setting the sata mode to AHCI in the BIOS (and that this can prevent Windows booting), but you'd remember if you did that.

---

### Post by oldfred on 2012-10-31
I have seen it posted that Windows really likes 30% free, starts to slow at 20% free and at 10% free is noticeably slow and just about impossible  to use. There is no space to run that needs space like defrag. You only have 5% free. Time to houseclean.

---

### Post by brightwork on 2012-10-31
I've increased the free space on the Windows partition to 13.6 gb and Windows still won't start and Windows Startup Repair still can't fix the problem so I don't think it's a space issue.  I've had my drive down to 3 or 4 gigs free when working on videos and Windows would still at least start.

Something tells me it definitely has something to do with the Wubi install though, because Lubuntu is not behaving properly either.  For instance, I can't start the Chromium browser (I'm using Firefox right now).  It says something about not being able to open it as root, but I'm just logged in with the user name I created during the wubi install.  I also can't write any files to the Lubuntu partition.  Is there any kind of "safe mode" that Lubuntu will sometimes boot into when something's wrong that might explain this?

---

### Post by bcbc on 2012-11-01
It sounds more like some corruption in your home directory that's causing chromium problems. If it were lubuntu then firefox probably wouldn't work either.

I did notice this in the boot-repair log:
> [7590:7590:435029705:ERROR:chrome_browser_main_extra_parts_gtk.cc(51)] Startup refusing to run as root.

Maybe that's something you want to ask YannUbuntu (the author of boot-repair). I'm not familiar with how boot-repair works or why it needs to run the browser.

I'm really not sure how to help though. It's not a typical Wubi problem and I doubt it's specific to Lubuntu either...

---

### Post by Moose on 2012-11-01
I have never had a problem like that.. Must be an older problem that was suddenly brought to light when you installed it maybe?

---

