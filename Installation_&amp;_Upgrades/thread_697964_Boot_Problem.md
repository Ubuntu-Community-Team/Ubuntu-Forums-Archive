---
title: "Boot Problem"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by spacewiz on 2008-02-15
I've been a windows user since we've have a computer but about 2 days ago my hdd crashed so i decied to switch over to linux.  I got a new WD 500gb sata hdd and i booted up the live cd.  Everything works via the cd so I go to install on my new hdd.  It goes through all the motions and I don't get any errors so I reset and take out the cd.  But now it doesn't boot anything.  It starts up and runs through the bios but when its time to boot an os I just get a blinking "_".  This is the second time I've tried to install.  Is there something I'm missing?

---

### Post by Herman on 2008-02-15
Can you boot your Ubuntu Live CD and run 'sudo fdisk -lu' and post the output here please?
```
sudo fdisk -lu
```

---

### Post by spacewiz on 2008-02-15
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x19ab19d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   390716864   195358401    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000eb645

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   967659209   483829573+  83  Linux
/dev/sdb2       967659210   976768064     4554427+   5  Extended
/dev/sdb5       967659273   976768064     4554396   82  Linux swap / Solaris

```

the second one is the one i'm trying to install on.  the 500.1gb hdd

---

### Post by Herman on 2008-02-15
This is unusual. Your fdisk output looks fine, there are no problems there that I can see. I'm not sure what could be going on here. Can you download yourself a copy of [Super Grub Disk]("http://sgd.benjamin-butschko.de/") so we can try some experiments to see if we can discover the problem?
In the meantime, you'll be able to boot your operating systems with Super Grub Disk until we get it figured out and hopefully fix it.

Regards, Herman :)

---

### Post by Herman on 2008-02-15
> I've been a windows user since we've have a computer but about 2 days ago my hdd crashed so i decied to switch over to linux.:idea: Is that still your crashed Windows HDD you still have plugged into your number1 SATA slot?

Maybe you should try unplugging the bad HDD from the number1 slot and plugging the good HDD into the number 1 slot instead.
Then try installling Ubuntu again and see what happens.
Make sure you install in the 500 GB drive again and this time GRUB will go to the 500 GB HDD's MBR  because it will be the first hard drive.
I don't know what's wrong with your other hard drive bit you'll still be able to access it for files or boot Windows in it, actually it's slightly better if Windows is on your second hard disk.

---

### Post by spacewiz on 2008-02-15
i have super grub disk but its not letting me boot.  i ran through a bunch of options but it gives me
```
Error 17: Cannot mount selected partition
```
even when i remove the cd, grub loads up but i get the same error.

my old crashed hdd isn't connected anymore.  i'm pretty sure the head is broken on it.

so should i go back with live cd and install again since grub cant boot it?

---

### Post by spacewiz on 2008-02-15
i'm installing again via live cd right now

i reinstalled but grub still gives me the same error about not being able to mount the partition

---

### Post by Herman on 2008-02-15
Okay, well 500 GB is a very big nice hard disk, but I think we should try an experiment and shrink your Ubuntu partition with GParted in the Ubuntu Live CD and make it a lot smaller. 
Resize it towards the beginning of the disk.
While you're using GParted, try running a file system check as well. Right-click on the partition you want checked.
Select 'check' from the right-click menu.
Click the 'Apply'  check mark button up on the toolbar.
Click the 'Apply' button in the confirmation pop-up window
Watch the reciprocating bar for a few minutes, a very large file system may take a while

Then try again to boot and see what happens. :)

---

### Post by spacewiz on 2008-02-15
i shrank it down to about ~230gb but i still get the grub mounting error.
should i make it even smaller?

---

### Post by Herman on 2008-02-15
Hmm, well I don't know, that will do for now I guess, that has worked a couple of times in the past for some reason. You probably think I'm crazy, I know, and it's hard to understand why that works sometimes, all I know is it can help. Something to do with hard disk geometry. Let's give that a rest for now and try a different experiment. Thanks for trying that.

Boot your Super Grub Disk and from one of its menus press your 'c' key for [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").

After the Grub prompt, type 'geometry (hd ' ...and then press your 'Tab' key. 
GRUB should reply something like: hd0 hd1

Next, type in the '0)' after 'geometry (hd', so it's 'geometry (hd0) ..and press 'Enter' .
GRUB should tell you your partition in your number 1 hard drive.

Do the same thing for (hd1), which is your second hard drive. 
GRUB should tell you what partitions are in your second hard drive.

I am interested to hear back from you if GRUB tells you your Linux partition is something like:
```
drive 0x80: C/H/S = 1023/255/63, The number of sectors = 156301488, LBA
          Partition num: 0, Filesystem type is ext2fs, partition type 0x83
``` You might get feedback something like that. 

If your linux partition is ext3, it should say 'ext2fs', please let me know what it does say. 

With some BIOSes you may not be able to get feedback like this, but I hope it will work with your BIOS.

> Error 17 : Cannot mount selected partitionThis error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.Regards, Herman :)

---

### Post by spacewiz on 2008-02-15
hd0 (new 500gb hdd) says
```
drive 0x80: C/H/S = 1023/255/63, The number of sectors = 976773168, LBA
          Partition num: 0, Filesystem type is ext2fs, partition type 0x83
          Partition num: 2, Filesystem type is ext2fs, partition type 0x83
          Partition num: 4, No BSD/SOLARIS sub-partition found, partition type 0x82

```

hd2, my second hdd says
```
drive 0x81: C/H/S = 1023/255/63, The number of sectors = 390721968, LBA
          Partition num: 0, Filesystem type unknown, partition type 0x7

```

---

### Post by Herman on 2008-02-15
:) Well it looks like GRUB is able to recognize the file systems all right this time. 
I wonder why it couldn't before?

Lets' try and boot your Ubuntu installation directly with a 'kernel' command from GRUB's Command Line and see if we can boot it!

Try typing 'find /boot/grub/stage2' after the grub> prompt and see what answers you get.
```
find /boot/grub/stage2
```It should say something like (hd0,0) or (hd0,2).


If your feedback from the first command said (hd0,0), then do this,
```
root (hd0,**0**)
``````
kernel /vmlinuz root=/dev/sda**1**
``````
initrd /initrd.img
``````
boot
```


If your feedback from the first command said (hd0,2), then do this,
```
root (hd0,**2**)
``````
kernel /vmlinuz root=/dev/sda**3**
``````
initrd /initrd.img
``````
boot
```

---

### Post by spacewiz on 2008-02-15
i had the hd0,0 one. 
i type the stuff in and it started to run though a bunch of stuff but it didn't work

i get a few errors

```

Begin: Running /scripts/init-bottom...
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
Done.
mount: Mounting /sys  on /root/sys failed: No such file or directory
mount:Mounting proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

Busy box v1.1.1 (Debian 1:1.1.3-5ubuntu7) Built-ini shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [ 1944.469409] ata5: SATA link down (SStatus 0 SControl 0)
[ 1944.780650] ata6: Sata link down (SStatus 0 SControl 300)

```
after that it stops and i get the blinking underscore

---

### Post by Herman on 2008-02-15
```
Target filesystem doesn't have /sbin/init

Busy box v1.1.1 (Debian 1:1.1.3-5ubuntu7) Built-ini shell (ash)
```That 'busybox shell' error message generally indicates some little mistake in your 'root=' options.
```
kernel /vmlinuz root=[COLOR=Red]/dev/sda1[/COLOR]
```Try getting GRUB to look for /sbin/init then and see if GRUB can tell us where it is.
After the grub prompt, type 'find /sbin/init'
```
find /sbin/init
```See what feedback we get. :)

---

### Post by spacewiz on 2008-02-16
```
(hd0,0)
```

---

### Post by Herman on 2008-02-16
Hmmm, as I expected. That appears to be correct.

It's up to you what you want to do next, spacewiz, you can simply try booting exactly the same way again just to make sure your didn't make a mistake last time and press a wrong key there in the 'root=/dev/sda1' part, and/or we can try shrinking your partition some more.

If there might be some kind of a problem with the disc geometry, which sometimes can occur with very large hard disks, the further out in your hard disk the files are scattered, the harder it is for them to be 'seen'.
It seems as if GRUB can 'see' everything okay now, but maybe your kernel is having problems.
That's what makes me think it might help to shrink your partition some more and see what happens.

Regards, Herman :)

---

### Post by spacewiz on 2008-02-16
when i retype those commands i still get the busybox and sata link down.  but now it runs through some more stuff about usb ports.

i'll try resizing even smaller.

gparted says my 500gb hdd is sdb so shouldn't the command be
```
kernel /vmlinuz root=/dev/sdb1
```
sdb1 instead of sda1?

---

### Post by spacewiz on 2008-02-16
holy crap, sdb1 worked.  it booted up.
so should i now be able to boot without the grub cd?

posting from my hdd boot of ubuntu :)

another quick semi-releated question
my second hdd, it isn't being read by ubuntu, unable to mount it.
that because of its formate ntfs?

---

### Post by Herman on 2008-02-16
:) Well done spacewiz! You solved it yourself!   :)

Okay, now while you have Ubuntu booted up (it should be easy from now on since we know the right commands now), let's take a look at your /boot/grub/menu.lst file.
The boot= part won't matter for that because we use a file system UUID number in our menu.lst file's boot commands instead.
Just check to make sure your boot entry for Ubuntu has '(hd0,0)' in it and you should be fine.
```
gksudo gedit /boot/grub/menu.lst
```Something like this,
```
title        Ubuntu, kernel 2.6.20-15-generic
root       [COLOR=Sienna]** (hd0,0)**[/COLOR]
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```
>  another quick semi-releated question
my second hdd, it isn't being read by ubuntu, unable to mount it.
that because of its formate ntfs?Maybe it needs a file system check. It would be best to use CHKDSK for that, from Windows. You can do it with a Windows [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") I believe.

---

### Post by spacewiz on 2008-02-16
i cant check it via windows.  we have windows computers but no of them have sata support.  anyway to do it in ubuntu.

they were all booting from hd(1,0).  kinda werid

thanks for all the help man.  i was hoping i wasn't gonna have to try another distro.

---

### Post by Herman on 2008-02-16
> i cant check it via windows.  we have windows computers but no of them have sata support.  anyway to do it in ubuntu.
Take a look at in with GParted, it's in your Ubuntu Live CD, go 'System'-->'Administration'-->'Partition Editor', and it will have a yellow warning triangle marking your NTFS partition if it needs a file system check.
GParted in Ubuntu can run a file system check on any file system. NTFS is kinda touchy though, especailly if it has an operating system in it. If it's just a data partition it might be okay, but I'm not sure. Even GParted's own documentation still recommends to use Windows CHKDSK after resizing an NFS partition. Unless the software is more up to date than the documentation, and that's normally the case.  GParted's pretty good, it's great for all Linux file systems and FAT32, but I'm not sure if it's as good as Windows on Windows' own file system.  Let's think that over for a while first.

Did you get it booting up okay without the CD? :)

---

