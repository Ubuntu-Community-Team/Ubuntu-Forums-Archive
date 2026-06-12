---
title: "grub-pc - error: you need to load the linux kernel first"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by HankB on 2009-10-06
After noticing that my root partition was less than 1/3 used, I decided to split it up to provide an additional partition in which to install Karmic to allow further testing w/out abandoning my Jaunty install. Karmic installed and grub2 seems to have migrated the boot entries for Jaunty, but when I try to boot any jaunty entries, I get:

```
error: you need to load the kernel first
```

Disk is:
```
root@cypress:~# fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6f80c932

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     3074047     1536000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2         3084480   103677839    50296680    7  HPFS/NTFS
/dev/sda3       103677840   124150319    10236240    7  HPFS/NTFS
/dev/sda4       124150320   976768064   426308872+   5  Extended
/dev/sda5       124150383   126190574     1020096   83  Linux
/dev/sda6       126190638   167108129    20458746   83  Linux
/dev/sda7       187639263   195639569     4000153+  82  Linux swap / Solaris
/dev/sda8       195639633   976768064   390564216   83  Linux
/dev/sda9       167108193   187639199    10265503+  83  Linux

Partition table entries are not in disk order
root@cypress:~# 

```

Important partitions are:
/dev/sda5 => /boot for the Jaunty install
/dev/sda6 => / for the Jaunty install
/dev/sda8 => /home, hopefully shared between Jaunty and Karmic
/dev/sda9 => / for the Karmic install, was part of /dev/sda6 before I used gparted to shrink that and add /dev/sda9

A typical entry from the Jaunty /boot/grub/menu.lst to boot Jaunty is:
```
title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		9bdeb391-8fd9-48b1-9316-c4a00b7fa7a2
kernel		/vmlinuz-2.6.28-15-generic root=UUID=7f69072f-cea2-4ec3-bde9-81dd16744034 ro quiet splash 
initrd		/initrd.img-2.6.28-15-generic
quiet

```

The corresponding entry from the Karmic /boot/grub/grub.cfg is

```
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda6)" {
        insmod ext2
        set root=(hd0,6)
        search --no-floppy --fs-uuid --set 7f69072f-cea2-4ec3-bde9-81dd16744034
        linux /boot/vmlinuz-2.6.28-15-generic root=UUID=7f69072f-cea2-4ec3-bde9-81dd16744034 ro quiet splash
        initrd /boot/initrd.img-2.6.28-15-generic
}

```

So... Can this Jaunty installation be saved? I'm not quite ready to commit to Karmic. 

thanks,
hank

---

### Post by VMC on 2009-10-06
I think this entry is wrong:
"uuid 9bdeb391-8fd9-48b1-9316-c4a00b7fa7a2"
I think it should read:
"uuid [COLOR="Red"]9391[/COLOR]-8fd9-48b1-9316-c4a00b7fa7a2"

Output "sudo blkid" to be sure

---

### Post by kansasnoob on 2009-10-06
> **VMC said:**
> I think this entry is wrong:
"uuid 9bdeb391-8fd9-48b1-9316-c4a00b7fa7a2"
I think it should read:
"uuid [COLOR="Red"]9391[/COLOR]-8fd9-48b1-9316-c4a00b7fa7a2"

Output "sudo blkid" to be sure

I'm still learning Grub 2 so worthless to the OP, but thought I'd say:

If a partition table has ever been modified it's best to run:

```
sudo blkid -c /dev/null
```

rather than:

```
sudo blkid
```

I learned from ***coffeecat*** that you should include the -c /dev/null bit. If you run blkid without options it reads from its cache file. If you've run it before and any partition has changed you'll get erroneous results.

No kiddin'! 99% of the time it doesn't matter, but there's that 1%:)

---

### Post by HankB on 2009-10-06
> **VMC said:**
> I think this entry is wrong:
"uuid 9bdeb391-8fd9-48b1-9316-c4a00b7fa7a2"
I think it should read:
"uuid [COLOR="Red"]9391[/COLOR]-8fd9-48b1-9316-c4a00b7fa7a2"

Output "sudo blkid" to be sure


```
hbarta@cypress:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="5C0CDB8F0CDB6296" LABEL="SERVICEV003" TYPE="ntfs" 
/dev/sda2: UUID="C4F8DDE6F8DDD730" LABEL="SW_Preload" TYPE="ntfs" 
/dev/sda3: UUID="DE62E0C562E0A38D" LABEL="Lenovo" TYPE="ntfs" 
/dev/sda5: UUID="9bdeb391-8fd9-48b1-9316-c4a00b7fa7a2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="7f69072f-cea2-4ec3-bde9-81dd16744034" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="a8b4289b-34b4-4c92-a7b9-c0bd7f253cff" TYPE="swap" 
/dev/sda8: UUID="e186fa4e-a98c-49b9-b491-2205628c1f75" TYPE="ext3" 
/dev/sda9: UUID="836c9f55-820b-4760-b2cb-81af5b6fedfe" TYPE="ext4" 
hbarta@cypress:~$ 

```
So, are you saying that I need to change the entry for legacy grub config (which worked fine until I installed Karmic) and that will work when I next boot? Do I need to run update-grub to reflect that change in the grub2 config?

thanks,
hank

---

### Post by VMC on 2009-10-06
> **HankB said:**
> ```
hbarta@cypress:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="5C0CDB8F0CDB6296" LABEL="SERVICEV003" TYPE="ntfs" 
/dev/sda2: UUID="C4F8DDE6F8DDD730" LABEL="SW_Preload" TYPE="ntfs" 
/dev/sda3: UUID="DE62E0C562E0A38D" LABEL="Lenovo" TYPE="ntfs" 
/dev/sda5: UUID="9bdeb391-8fd9-48b1-9316-c4a00b7fa7a2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="7f69072f-cea2-4ec3-bde9-81dd16744034" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="a8b4289b-34b4-4c92-a7b9-c0bd7f253cff" TYPE="swap" 
/dev/sda8: UUID="e186fa4e-a98c-49b9-b491-2205628c1f75" TYPE="ext3" 
/dev/sda9: UUID="836c9f55-820b-4760-b2cb-81af5b6fedfe" TYPE="ext4" 
hbarta@cypress:~$ 

```
So, are you saying that I need to change the entry for legacy grub config (which worked fine until I installed Karmic) and that will work when I next boot? Do I need to run update-grub to reflect that change in the grub2 config?

thanks,
hank
Not at all. Now that I can see your blkid output. It looked weird at first. I couldn't determine if something added digits. Now I see its correct.

---

### Post by VMC on 2009-10-06
> **HankB said:**
> 
```
error: you need to load the linux kernel first
```
 This usually means something wrong with linux line.

Edit: Are you now running on grub2? If so you need to run "sudo update-grub" from karmic. Then see if it picks up jaunty correctly.

---

### Post by HankB on 2009-10-06
> **VMC said:**
> This usually means something wrong with linux line.

Edit: Are you now running on grub2? If so you need to run "sudo update-grub" from karmic. Then see if it picks up jaunty correctly.

Grub2 if that is what installs by default with Karmic.

I have tried running 'sudo update-grub' and it has not made a difference.

BTW, noticed that the actual error is "error: you need to load the kernel first" There is no actual mention of Linux

```
hbarta@cypress:~$ sudo update-grub
[sudo] password for hbarta: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-12-generic
Found initrd image: /boot/initrd.img-2.6.31-12-generic
Found linux image: /boot/vmlinuz-2.6.31-11-generic
Found initrd image: /boot/initrd.img-2.6.31-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Ubuntu 9.04 (9.04) on /dev/sda6
done
hbarta@cypress:~$ 
```

thanks,
hank

---

### Post by ranch hand on 2009-10-06
Boy, that menu entry looks good to me.

This one is from my custom entries and I know it works;
```

  	 	 	 	 	 	  menuentry "Jaunty 9.04, kernel 2.6.28-15-generic (on /dev/sda8)" {  
         set root=(hd0,8)  
         search --no-floppy --fs-uuid --set 79e9dc92-8346-44a9-b74a-97b4a76c560e  
         linux /boot/vmlinuz-2.6.28-15-generic root=UUID=79e9dc92-8346-44a9-b74a-97b4a76c560e ro quiet splash  
         initrd /boot/initrd.img-2.6.28-15-generic  
 } 


```
Really check all the spacing and numbers to make sure that they are right.


You might also save your file with a different name (the grub.cfg) so that you have an extra copy.  Rerun update-grub.  Reboot.  Rerun update-grub.  Compare files.  Some times it takes os-prober a few tries to catch all changes correctly.

---

### Post by VMC on 2009-10-06
> **HankB said:**
> 

BTW, noticed that the actual error is "error: you need to load the kernel first" There is no actual mention of Linux



When I said linux, I was referring to the line in grub that has the actual "linux" name in the beginning.

Ok, now that we have established that your using grub2 off of karmic. Use sudo to out put the menuentry for jaunty.

sudo vi /boot/grub/grub.cfg

Then look for you jaunty partition and output that back here.

It will look something like this (this ones mine):

```
menuentry "jaunty (/dev/sda7) (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 5d67fd00-0856-4ce1-b278-9acf3e926a5c
	gfxpayload=1024x768
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=5d67fd00-0856-4ce1-b278-9acf3e926a5c ro
	initrd /boot/initrd.img-2.6.28-15-generic
}
```

---

### Post by HankB on 2009-10-06
> **ranch hand said:**
> Boy, that menu entry looks good to me.

This one is from my custom entries and I know it works;
```

  	 	 	 	 	 	  menuentry "Jaunty 9.04, kernel 2.6.28-15-generic (on /dev/sda8)" {  
         set root=(hd0,8)  
         search --no-floppy --fs-uuid --set 79e9dc92-8346-44a9-b74a-97b4a76c560e  
         linux /boot/vmlinuz-2.6.28-15-generic root=UUID=79e9dc92-8346-44a9-b74a-97b4a76c560e ro quiet splash  
         initrd /boot/initrd.img-2.6.28-15-generic  
 } 


```
Really check all the spacing and numbers to make sure that they are right.


You might also save your file with a different name (the grub.cfg) so that you have an extra copy.  Rerun update-grub.  Reboot.  Rerun update-grub.  Compare files.  Some times it takes os-prober a few tries to catch all changes correctly.
The UUIDs match what blkid produces. This file is produced by update-grub on initial install of Karmic. If there are any errors, they must come from the template files or one of the programs. 

I've rerun update-grub several times with no change in output.

> **VMC said:**
> When I said linux, I was referring to the line in grub that has the actual "linux" name in the beginning.

Ok, now that we have established that your using grub2 off of karmic. Use sudo to out put the menuentry for jaunty.

sudo vi /boot/grub/grub.cfg

Then look for you jaunty partition and output that back here.

```
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda6)" {
        insmod ext2
        set root=(hd0,6)
        search --no-floppy --fs-uuid --set 7f69072f-cea2-4ec3-bde9-81dd16744034
        linux /boot/vmlinuz-2.6.28-15-generic root=UUID=7f69072f-cea2-4ec3-bde9-81dd16744034 ro quiet splash
        initrd /boot/initrd.img-2.6.28-15-generic
}
```
Note that the boot partition is /dev/sda5 (mounted as /boot under Jaunty) and on that partition, the kernel image is /vmlinuz-2.6.28-15-generic  and the UUID for that partition is 9bdeb391-8fd9-48b1-9316-c4a00b7fa7a2.

Is it possible that grub2 has not figured out that Jaunty has a separate /boot and root partition? How can I tell it that?
> 
It will look something like this (this ones mine):

```
menuentry "jaunty (/dev/sda7) (on /dev/sda9)" {
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 5d67fd00-0856-4ce1-b278-9acf3e926a5c
	gfxpayload=1024x768
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=5d67fd00-0856-4ce1-b278-9acf3e926a5c ro
	initrd /boot/initrd.img-2.6.28-15-generic
}
```

Do you have a separate partition for /boot and root?

Thanks for working along with me on this.

---

### Post by ranch hand on 2009-10-06
You might try a custom entry pointing to your boot partition.

I would write all the info down and hit "e" when booting to edit the entry there.  If that poots it i would definitely go with a custom entry.

---

### Post by VMC on 2009-10-06
Your menuentry for jaunty looks correct. Where did you get that grub.cfg from? Was it sd9? That's where your karmic is.

No, I do not have a separate "/boot" partition. Everything under one roof.

Some things can get screwed up when we re-partition things around.

When you boot-up you have a grub2 boot menu, and you selected karmic, correct? Ok, once your booted up under karmic, output from a terminal "df" so we can see where he thinks he belongs.

---

### Post by HankB on 2009-10-06
> **VMC said:**
> Your menuentry for jaunty looks correct. Where did you get that grub.cfg from? Was it sd9? That's where your karmic is.

No, I do not have a separate "/boot" partition. Everything under one roof.

Some things can get screwed up when we re-partition things around.

When you boot-up you have a grub2 boot menu, and you selected karmic, correct? Ok, once your booted up under karmic, output from a terminal "df" so we can see where he thinks he belongs.
Yes, grub.cfg is on /dev/sd9 which holds the Karmic install.

I don't recall where I got the idea to use a separate /boot partition except that it was probably to support root on something that grub cannot handle. It's one of the choices offered when performing a custom partition so it cannot be too non-standard.

```
hbarta@cypress:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda9             10104268   2775452   6815544  29% /
udev                   1977188       332   1976856   1% /dev
none                   1977188       224   1976964   1% /dev/shm
none                   1977188       112   1977076   1% /var/run
none                   1977188         0   1977188   0% /var/lock
none                   1977188         0   1977188   0% /lib/init/rw
/dev/sda8            384435636 161622916 203284512  45% /home
oak:/export/redwood  102396896  86246240  16150656  85% /mnt/oak
oak:/export/share    419417600 378476640  40940960  91% /mnt/share
hbarta@cypress:~$
``` 

thanks,
hank

---

### Post by VMC on 2009-10-06
Having separate partitions for /home,/boot/var is very unix like, very standard. I choose it as my KISS stand. I keep backups aplenty, and it makes cloning my one partition simpler.

Here's another idea. From grub2 menu choose 'c' to get to your grub command prompt. Then type help and you can see all the commands to use. 'ls' will list what it determines as legitimate partitions. Does jaunty come up?

---

### Post by HankB on 2009-10-06
> **VMC said:**
> 
Here's another idea. From grub2 menu choose 'c' to get to your grub command prompt. Then type help and you can see all the commands to use. 'ls' will list what it determines as legitimate partitions. Does jaunty come up?
I gave that a shot. 'ls' shows all partitions. The 'probe <device>' command looks interesting, but I could not figure out the notation for device and the documentation was light on that.

I also tried copying the Jaunty /boot partition to /boot in the Jaunty root partition thinking that was where grub was looking for the kernels but that made no difference either WRT the grub.cfg produced by 'update-grub' or behavior at boot time.

I've found two bugs in launchpad that seem to refer to this problem when there is a separate /boot partition so I've added notes to those to see if they might be related. It seems unlikely that this is something that will be fixed before the release, but I can hope for a work around.

thanks,
hank

---

### Post by VMC on 2009-10-06
> **HankB said:**
> I gave that a shot. 'ls' shows all partitions. The 'probe <device>' command looks interesting, but I could not figure out the notation for device and the documentation was light on that.

I also tried copying the Jaunty /boot partition to /boot in the Jaunty root partition thinking that was where grub was looking for the kernels but that made no difference either WRT the grub.cfg produced by 'update-grub' or behavior at boot time.

I've found two bugs in launchpad that seem to refer to this problem when there is a separate /boot partition so I've added notes to those to see if they might be related. It seems unlikely that this is something that will be fixed before the release, but I can hope for a work around.

thanks,
hank
I was thinking after you boot up karmic try to mount jaunty and look around and see that it looks intact. You mentioned in one of your posts you weren't sure if it was there or not. Also, I think your on to something. Now that I think about it. Does jaunty's fstab reference a separate /boot partition. Try using that /boot partition UUID as reference to boot jaunty.

---

### Post by HankB on 2009-10-07
> **VMC said:**
> I was thinking after you boot up karmic try to mount jaunty and look around and see that it looks intact. You mentioned in one of your posts you weren't sure if it was there or not. Also, I think your on to something. Now that I think about it. Does jaunty's fstab reference a separate /boot partition. Try using that /boot partition UUID as reference to boot jaunty.
Yes, that seems to be the key figuring out the right settings in the grub.cfg file. Here's what (finally!) worked:

```
oot@cypress:/media/disk/boot/grub# diff grub.cfg grub.cfg.save
102,104c102,104
< 	search --no-floppy --fs-uuid --set 9bdeb391-8fd9-48b1-9316-c4a00b7fa7a2
< 	linux /vmlinuz-2.6.28-15-generic root=UUID=7f69072f-cea2-4ec3-bde9-81dd16744034 ro quiet splash
< 	initrd /initrd.img-2.6.28-15-generic
---
> 	search --no-floppy --fs-uuid --set 7f69072f-cea2-4ec3-bde9-81dd16744034
> 	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=7f69072f-cea2-4ec3-bde9-81dd16744034 ro quiet splash
> 	initrd /boot/initrd.img-2.6.28-15-generic
root@cypress:/media/disk/boot/grub# blkid
/dev/sda1: UUID="5C0CDB8F0CDB6296" LABEL="SERVICEV003" TYPE="ntfs" 
/dev/sda2: UUID="C4F8DDE6F8DDD730" LABEL="SW_Preload" TYPE="ntfs" 
/dev/sda3: UUID="DE62E0C562E0A38D" LABEL="Lenovo" TYPE="ntfs" 
/dev/sda5: UUID="9bdeb391-8fd9-48b1-9316-c4a00b7fa7a2" TYPE="ext3" 
/dev/sda6: UUID="7f69072f-cea2-4ec3-bde9-81dd16744034" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="a8b4289b-34b4-4c92-a7b9-c0bd7f253cff" 
/dev/sda8: UUID="e186fa4e-a98c-49b9-b491-2205628c1f75" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sda9: UUID="836c9f55-820b-4760-b2cb-81af5b6fedfe" TYPE="ext4" 
root@cypress:/media/disk/boot/grub# 

```

In other words:
 - specify the UUID of the boot partition in the search line
 - specify the path to the kernel and initial RAM disk relative to the boot partition.

Now the only annoyance is that every time something in the Karmic install reruns 'update-grub' I will need to hand modify the grub.cfg file.

And it remains to be seen what will happen when Jaunty tries to update legacy grub. Maybe I need to install that on Jaunty. I see it is available.

Thanks again for helping me to work through this.

best,
hank

---

### Post by HankB on 2009-10-07
> **HankB said:**
> ...
And it remains to be seen what will happen when Jaunty tries to update legacy grub. Maybe I need to install that on Jaunty. I see it is available.

I went ahead and installed grub2 (grub-pc actually) on my Jaunty setup and found one more bit of strangeness. After running 'update-grub' it produced what looked like a working grub.cfg but it did not do whatever needs to be done to cause grub itself to use the new config file. I was able to determine that grub still uses the config file on the Karmic partition. I suppose I need to run some command to actually rewrite the boot loader to the disk to make that happen. It seems that installing grub2 neither does that nor produces the grub.cfg file by default. Perhaps it detected grub2 already on the boot sector and decided it didn't need to rewrite it.

---

### Post by ranch hand on 2009-10-07
If you put your menu entry in /etc/grub.d/40_custom it will not be over written and will be at the end of your menu.

If you save the file you create with the custom entry to, say, 09_custom, it will not be over written and will be at the beginning of your menu

---

### Post by HankB on 2009-10-07
> **ranch hand said:**
> If you put your menu entry in /etc/grub.d/40_custom it will not be over written and will be at the end of your menu.

If you save the file you create with the custom entry to, say, 09_custom, it will not be over written and will be at the beginning of your menu
Thanks for the tips.

---

### Post by ranch hand on 2009-10-07
If you want to see a grub.cfg file for multi-boot you can see mine at

[http://ubuntuforums.org/showthread.php?t=1284553](http://ubuntuforums.org/showthread.php?t=1284553)

You can see that at the beginning of each section the file in grub.d that is generating that section is listed.

The entries that just list the partition are neat too because they never need editing.  I have even formated and reinstalled something else on partitions and used the old entry to boot.

---

