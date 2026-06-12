---
title: "After update, Grub won't boot says Kernel missing"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by Eredeath on 2010-01-09
I used the update manager to update the kernel and whatever the other recommended updates were yesterday. I shut the computer down overnight and now when i try to boot into Ubuntu 9.10 i get a basic grub shell and when i try commands like "boot" it tells me there is no kernel loaded.
I installed Ubuntu with Wubi so it is a dual boot system. 
I've tried to access the Linux volume with a live OpenSuse 11 CD but there is no device to mount. It sees the entire hard-drive as if it hasn't been partitioned. I don't necessarily need to fix the installation. I just need to get my files back. Any help would be much appreciated.

---

### Post by Eredeath on 2010-01-09
I have some extra info. I tried to mount the root.disk and tailed it with dmesg and this is what i got:

```
mount -o loop /mnt/sda1/ubuntu/disks/root.disk /mnt/ubuntu | dmesg | tail
mtrr: no MTRR for e0000000,800000 found
mtrr: type mismatch for e0000000,800000 old: write-back new: write combining
EXT3-fs: loop1: couldn't mount because of unsupported optional features (240).
unionfs: do delay copyup of "appreg"
atl1 0000:01:00.0: Unable to enable MSI: -1
atl1: eth0 link is up 100 Mbps full duplex
unionfs: unhashed dentry being revalidated: tls
spurious 8259A interrupt: IRQ15.
EXT3-fs: loop1: couldn't mount because of unsupported optional features (240).
EXT3-fs: loop1: couldn't mount because of unsupported optional features (240).
mount: wrong fs type, bad option, bad superblock on /dev/loop1, missing codepage or other error
In some cases useful info is found in syslog - try dmesg | tail or so
```

---

### Post by ajgreeny on 2010-01-09
As you have just updated, try booting to an older kernel, though as you are running a wubi install, I have no idea how you do that.  I presume there must be a menu at some point which offers you kernel numbers, eg 2.6.31-14, 2.6.31-16, etc etc.  Try the one that was used at install time which if I remember correctly was 2.6.31-14.  If that is OK uninstall the new kernel from the system when running the old one and you should then boot automatically into the system to the older kernel.

---

### Post by Eredeath on 2010-01-09
I wish it were that easy...
I don't get any menus beyond the choice of vista or ubuntu in the windows mbr. After i choose ubunut it takes me to a minimal grub shell.

---

### Post by meierfra. on 2010-01-09
**Edit:  Turns out that "probe" is not available in the Wubi grub. Go the post 14 for the correct solution,**

Try this at the "grub>sh" prompt:
```

set Path=/ubuntu/disks/root.disk
search -f --set=Root ${Path} 
probe -u (${Root})  --set=UUID   
linux /vmlinuz root=UUID=${UUID} loop=${Path}  ro
initrd /initrd.img
boot 

```

(Type it exactly like that.) 

Once booted in Wubi, open a terminal and type

```

sudo update-grub2

```

---

### Post by Eredeath on 2010-01-09
I tired your solution but after the second line i recieved the error: 
> error: no such device: )
I thought that maybe the set command wasn't working right so i tried inserting /ubuntu/disks/root.disk where Path is (in the second line) but it tells me still that there is no such device.
i also tried a couple variations on the path such as capitalizing the u but still nothing.

Edit:
extra thought. Don't i need to mount a drive or type the path out as it relates to windows in some way?

---

### Post by Eredeath on 2010-01-09
Okay, So i figured out the path issue... but now i'm getting an error that probe is an unknown command

---

### Post by meierfra. on 2010-01-09
Edit:  I hadn't seen your latest post, when I wrote this.  But you might as well  start working on this while I think about your last post.  What did you do to fix the path problem?)

> error: no such device: 
What is the output of

```
set
ls 
ls (loop0)
ls (hd0,1)
ls (hd0,1)/
ls (hd0,2)
ls (hd0,2)/
```
at the "grub" prompt? 

Do whose commands detect your windows partition and your Wubi file system (You might have to try other (hd?,?).)

> I've tried to access the Linux volume with a live OpenSuse 11 CD but there is no device to mount. It sees the entire hard-drive as if it hasn't been partitioned. 

Which version of OpenSuse 11 do you have? I think OpenSuse 11.1 and higher support ext4.  But actually any version should detect your partitions.  So I would like to have a closer look at your setup. Follow these [instruction]("http://ubuntuforums.org/showthread.php?t=1291280") to run the Boot Info Script and post the "RESULTS.txt". If you have Open Suse 11.1 or higher, you can use the Open Suse LiveCD. (But use
```
su
bash ~/Desktop/boot_info_script*.sh
```
to run the script.)
Otherwise it might be best to download an Ubuntu LiveCD.

---

### Post by Eredeath on 2010-01-10
The Path problem was an error of syntax. The way you have it is $(Path) where for me it needs to be $Path without the parenthesis. 

This might help. When i first boot into grub i get a  message that says try(hd0,0) but when i do 
ls (hd0,0) i get
error: no such partition

I have partitions on hd0,1 and loop0 gives me feedback saying that i have an ext2 filesystem

The only part of the code that i havn't gotten to work correctly that you sent me was the probe command

---

### Post by meierfra. on 2010-01-10
> I'm getting an error that probe is an unknown command 

Try this at the grub prompt:

```
linux /vmlinuz root=/dev/sd[COLOR="Red"]a1 [/COLOR]loop=/ubuntu/disks/root.disk
initrd initrd.img
boot
```

You might have adjust the number in  /dev/sda1.  It has to be your windows partition. If the "search" command worked,  just can use the last number in 

```
echo ${Root}
```


If this does not boot you into Wubi, follows the instruction from my previous post.

---

### Post by meierfra. on 2010-01-10
```
The way you have it is $(Path) 
```

No, I have "${Path}", (curly brackets, not round).  "$Path" also works since Path does not have spaces. So  the next time I'll use these instruction, I'll just use "$Path" to avoid the confusion.

---

### Post by Eredeath on 2010-01-10
> **meierfra. said:**
> Try this at the grub prompt:

```
linux /vmlinuz root=/dev/sd[COLOR="Red"]a1 [/COLOR]loop=/ubuntu/disks/root.disk
initrd initrd.img
boot
```
Seems to have gotten me closer. I got a lot of output... here are some of the significant lines from it.
```
[     0.679953] RAMDISK: Couldn't find valid RAM disk image starting at 0.
[     0.681552] No filesystem could mount root, tried: ext3 ext2 ext4 fuseblk
[     0.681677] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)
[     0.681733] Pid: 1, comm: swapper Not tainted 2.6.31-17-generic #54-Ubuntu
```(FYI: I typed that all by hand so if there seems to be anything really odd it might be a typo on my part)

Since that didn't work i'm going to try your previous suggestion

---

### Post by Eredeath on 2010-01-10
> **meierfra. said:**
> ```
The way you have it is $(Path) 
```

No, I have "${Path}", (curly brackets, not round).  "$Path" also works since Path does not have spaces. So  the next time I'll use these instruction, I'll just use "$Path" to avoid the confusion.

AH! I see it now... I'm working off my notebook with a small screen.... they look like round brackets on this thing.

---

### Post by meierfra. on 2010-01-10
Boot into Windows and try this:

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")

---

### Post by Eredeath on 2010-01-10
The results from the boot info script:
> ============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:      Mounting failed:
mount: unknown filesystem type 'ext4'

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb6938bc7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   976,770,094   976,770,032   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="4E1E5AA21E5A82BF" TYPE="ntfs" 
sda1/Wubi: UUID="d12aa92b-d968-41e3-9ce3-3a572d45698d" TYPE="ext4" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
debugfs on /sys/kernel/debug type debugfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,mode=0620,gid=5)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

=============================== StdErr Messages: ===============================

File descriptor 4 left open
File descriptor 9 left open
File descriptor 10 left open
File descriptor 11 left open
File descriptor 12 left open
File descriptor 15 left open
mdadm: No arrays found in config file or automatically


---

### Post by Digikid on 2010-01-10
Looks like you and I both have the exact same problem.

[http://ubuntuforums.org/showthread.php?t=1377175](http://ubuntuforums.org/showthread.php?t=1377175)

Were these updates not TESTED?????

---

### Post by meierfra. on 2010-01-10
"RESULTS.tex" looks fine, in particular there does not seem to a problem with your partition table.   Although   your LiveCD does not  seem to understand ext4. So if the link I posted in my last post does not solve your problem, you should  get an Ubuntu LiveCD.

---

### Post by meierfra. on 2010-01-10
> Were these updates not TESTED?????

As far as I understand, there is no problem with the updates itself.  But they trigger a bug in Grub2  "ntfs" module which only seems to effect Wubi. The new "wubildr"  (see post 14) is supposed to  work around that bug.  So I suggest to directly follow the instruction from the link in post 14.

---

### Post by Eredeath on 2010-01-10
You did it my friend. The patch in windows that you pointed me to worked! I'm in Ubuntu typing this right now :D
You've made my day!
Thank you so much.

---

### Post by Digikid on 2010-01-10
Trying it now.  Thank you for the redirect.

---

### Post by Digikid on 2010-01-10
That did it!  Posting this from Ubuntu now.  Thanks for the patch!!!!

Now get Canonical to release this as an official update for WUBI Users!!!!  LOL!!!!

---

### Post by meierfra. on 2010-01-10
> The patch in windows that you pointed me to worked! I'm in Ubuntu typing 

> That did it! Posting this from Ubuntu now. Thanks for the patch!!!!

Great. I spent a good amount of time today reading through that bug report until I finally saw  the solution in post 210.   So   I'm  glad it really works.

---

### Post by Digikid on 2010-01-10
You created WUBI?

---

### Post by meierfra. on 2010-01-10
> You created WUBI? 

NOOOOOOOOOO!

I rephrased my sentence, to avoid that confusion.

---

### Post by Digikid on 2010-01-10
LOL!!!!!!!!!!!!

My apologies.

---

### Post by svegress on 2010-03-22
Could I just add that I ran into the same problem only yesterday and this [SOLVED] thread helped me fix it.  Unlike my desktop which is a full installation, my portable is a wubi installation that I had frozen on 17 until the dust had settled.  I decided that enough iterations had passed and did a full update to 20 resulting in the Grub complaining that the kernel was missing.
It didn't take long for me to discover this thread and the work of Agostino Russo to fix the problem mentioned in message #14 above.  He had done a [replacement for C:/wubildr ]("https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90")under Windows that I simply downloaded put onto a stick and transferred over to my portable while running Windows.  Perhaps it was because it was a later Ubuntu version but I didn't need to fiddle with any further settings--it just worked straight off.:p

---

### Post by markoturso on 2010-04-02
I had this problem too. Just after installing upgrades Ubuntu wouldn't start,
but this "replacement for C:/wubildr" worked. This thread was my last shot before reinstalling Ubuntu
and this problem gave me a lot of headache, thank you Agostino Russo, you rule :)

---

### Post by Aerex on 2010-04-30
Thanks Mister, I have had this problem for a very long. I had to reformat just so I can boot ubuntu. Bumping this for usefulness.

---

### Post by yoiam on 2011-02-21
I have read all of your messages and tried them all.     But still no working computer.
I am running a msi netbook I only have 1 op system on it witch is ubuntu 10.04
I tried installing the drivers for my TL-WN422G but no luck there so I deleted it after that I turned it off.     When I turned it on the next day it loaded straight in to grub.   
I says I have no kernel :( Please help what can I do I do not want to loose my files.

---

