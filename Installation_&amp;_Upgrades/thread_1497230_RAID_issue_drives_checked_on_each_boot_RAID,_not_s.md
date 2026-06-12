---
title: "RAID issue: drives checked on each boot RAID, not shown in GParted"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by joepiebuntu on 2010-05-30
My setup is that sda and sdb are part of a RAID 1 (mirror) setup on an Intel ICH10R, sdc is a data disc and sdd is the startup/boot/root disc. 

This setup worked like a charm in 9.04 and 9.10.

I just installed 10.04 on a (new) partition. Installing went fine, but after rebooting (and every subsequent reboot) I get the following messages during startup:

```

udevd-work[186]: inotify_add_watch(6, /dev/sda, 10) failed: no such file or directory
udevd-work[186]: inotify_add_watch(6, /dev/sdb, 10) failed: no such file or directory

```

The system displays the 'error' message and then continues to load. Shortly thereafter it starts to check the disc(s). This check take quite some time.

After all is done, I am able to login. dmraid -s does show the RAID setup, so it could say no problem. But, GParted does not show the RAID (which it did on 9.10) and Places show all drives three times (I imagine sda, sdb and the RAID version). 

I got the feeling this might be the same as [http://ubuntuforums.org/showthread.php?t=1469862](http://ubuntuforums.org/showthread.php?t=1469862), but am not sure. Anyhow, I don't see a solution there yet, and I do think it is worrying.
For now I am reverting to 9.10 (while keeping 10.04 on the other partition), as I am afraid it might break my RAID or damage the data on the drives...

Can anybody tell me what this might be?

---

### Post by KingOfFright on 2010-05-30
Hi, I remember I got the same messages as you(I'm using raid0), I hit a sutck problem, how about you?
[http://ubuntuforums.org/showthread.php?t=1497241](http://ubuntuforums.org/showthread.php?t=1497241)

---

### Post by darkod on 2010-05-30
Only thing I can think of is installing with the alternate image, so it sees the RAID right away. Maybe it will help.

---

### Post by joepiebuntu on 2010-05-31
@KingOfFright: 
10.04 itself is not installed on the RAID0. The RAID0 is only a 'data' partition. I don't have issues with shutting down, it's only during startup that the drives are being checked every time.

@darkod: 
With 9.04, 9.10 I didn't need the alternate versions. In this case I used the Live CD to install. The system does see the RAID right away I think, because when I do dmraid -s it shows the RAID setup as active?!
Still, thanks for the tip and I'll try the alternate. 

In the mean time: is there anyone else who has this problem as well? That is, that with a RAID0 setup (which is not the drive 10.04 is installed on), the drives are being checked during each boot?

---

### Post by Jeroensum on 2010-06-01
Possibly during setup Ubunty mistakenly added entries in /etc/fstab for each drive? Since they shows up in Places it looks like the system has or has tried, to mount them, which could in theory explain the drivecheck at the beginning since Ubuntu can read a linux softraid drive but the mount manager doesn't know how to handle it and possibly marks the drive as having problems. If there are entries in /etc/fstab regarding the drives, remove those and reboot.

---

### Post by joepiebuntu on 2010-06-07
Just an update of where I am now: I (re)installed 10.04 on the (as before on a non-RAID disc) using the alternate image. After install finished I held my breath on the first restart...

And all looked OK! No udev messages and no checking of the discs.
So, I looks like using the Alternate ISO did the trick.

Did a few restarts and all OK. Just until yesterday I did get the udev and inotify_add_watch messages, but no checking of the discs.

So, I think my problem is (for now ;) )solved by using the alternate ISO's. 

@Jeroensum: I checked the fstab before (re)installing, but did not see anything 'strange' there (no indication of multiple drives). But (re)installing also solved this problem.

---

### Post by spleach on 2010-09-29
I see the issue is 'solved' by installing with the alternative image, but that's not an option I want to take. I don't recall seeing an alternative image in the install options either, having installed from boot with an Ubuntu 10.04 64bit DVD. My system is configured similarly to joepiebuntu, and I get almost identical symptoms too.
One difference is that I don't have /dev/sda and /dev/sdb (my RAID0 drives, not partitions) in Places.

Relevant parts of my setup is as follows:-
/dev/sdc1 - A 600GB partition with Ubuntu installed. On a 2TB HDD.

/dev/sda & /dev/sdb are 300GB drives with a BIOS configured (Intel ICH0) RAID0 over them. Comprises of 3 partitions:-
/dev/mapper/isw_....Volume01 105MB Windows Bootloader.
/dev/mapper/isw_..._Volume02 342GB Windows 7
/dev/mapper/isw_..._Volume03 258GB Windows Virtual HD on ext4 for use with VMWare virtualbox.

/etc/fstab is properly configured with UUID numbers referring to the correct partitions. Just double checked it with the commands:-
```
cat /etc/fstab
ls -l /dev/disk/by-uuid/
ls -l /dev/disk/by-label/
```There's also no mention of /dev/sda or /dev/sdb with these commands, but...
```

> ls -l /dev/disk/by-path/
#### CUT IRRELEVANT LINES
lrwxrwxrwx 1 root root  9 2010-09-29 17:31 pci-0000:00:1f.2-scsi-0:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root  9 2010-09-29 17:31 pci-0000:00:1f.2-scsi-1:0:0:0 -> ../../sdb
lrwxrwxrwx 1 root root  9 2010-09-29 17:31 pci-0000:00:1f.2-scsi-2:0:0:0 -> ../../sdc
#### CUT IRRELEVANT LINES
> ls -l /dev/disk/by-id
...
lrwxrwxrwx 1 root root  9 2010-09-29 17:31 ata-WDC_WD3000HLFS-01G6U1_WD-WXD0CB9D3574 -> ../../sda
lrwxrwxrwx 1 root root  9 2010-09-29 17:31 ata-WDC_WD3000HLFS-01G6U1_WD-WXL1C10C8246 -> ../../sdb
...

```The only other place I can see referring to /dev/sda & /dev/sdb is the System Disk Utility.

In case it's not clear, I get the same problem as @joepiebuntu:
> after rebooting (and every subsequent reboot) I get the following messages during startup:

     ```

     udevd-work[186]: inotify_add_watch(6, /dev/sda, 10) failed: no such file or directory
    udevd-work[186]: inotify_add_watch(6, /dev/sdb, 10) failed: no such file or directory

```
The system displays the 'error' message and then continues to load.  Shortly thereafter it starts to check the disc(s). This check take quite  some time.
If anyone could shed light on how to fix this, it'd be much appreciated!

---

### Post by ronparent on 2010-09-29
I haven't checked it, but it seems that dmraid doesn't install automatically if the install or upgrade itself is not to the raid. Once dmraid is installed you should have no trouble accessing any of your raid partitions. I hope I'm getting the sense of your inquire. Since the thread is old, you might be better off stating your question in a new thread?

edit: I don't believe the original issue of the raid partitions not showing in gparted  applies any longer with the release of 10.04.1.

---

### Post by spleach on 2010-10-02
Thanks for the reply. I must not have been clear before, because I can access the RAID no problem. I've got dmraid and don't remember installing it myself. I don't however have gparted installed, and have no reason to change my partitions.
I'll put this into a new thread as I've just done some investigating with quite a lot of code output that could aid the solution...
Cheers!

Started a new thread for this @ [http://ubuntuforums.org/showthread.php?p=9916069](http://ubuntuforums.org/showthread.php?p=9916069)

---

