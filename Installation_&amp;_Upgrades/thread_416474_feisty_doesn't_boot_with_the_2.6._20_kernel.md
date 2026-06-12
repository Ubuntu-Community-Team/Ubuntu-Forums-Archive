---
title: "feisty doesn't boot with the 2.6. 20 kernel"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by karellen on 2007-04-21
I've upgraded yesterday to feisty, all went well, the update manager downloaded and installed the new packages, but after reboot when I selected from Grub menu the first option: "kernel 2.6.20", feisty doesn't boot. instead it stalls with this screen:

> /bin/sh: can't access tty: job control turned off
(initramfs)


then it does nothing.

if I select de old 2.6.17 kernel image, it boots without a hitch and everything works fine, I can enjoy my new feisty dektop.
does anybody have any idea why the new kernel behaves like that? (I have a pretty old configuration - p4, ide hdd, nvidia geforce4, no name ethernet card - nothing fancy and Linux always managed to fully recognize my hardware)

---

### Post by josel on 2007-04-21
I got a hang problem with the same kernel and manage to boot only after  installing 2.6.20-12 - it can be found somewhere on launchpad.net.

The weird thing is that the live cd boots while hdd does not with 2.6.20-15. Any idea ? - it must be something to do  with disks and/or filesystem.

---

### Post by bulldog on 2007-04-21
Check the UUID in fstab and in menu.lst if they are the same.
Had some problems with an earlier kernel and it messed with the UUID.
To find your disk UUID```
ls /dev/disk/by-uuid -lh
```

---

### Post by karellen on 2007-04-21
> **josel said:**
> I got a hang problem with the same kernel and manage to boot only after  installing 2.6.20-12 - it can be found somewhere on launchpad.net.

The weird thing is that the live cd boots while hdd does not with 2.6.20-15. Any idea ? - it must be something to do  with disks and/or filesystem.

yes, the live cd worked for me too. but I can't boot from the hdd. for now I'll stick with the 2.6.17 kernel as I feel no need for a newer (better no way!) one

---

### Post by b0le on 2007-04-21
I have same problem, except that it works in recovery mode:

```

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=efd7320d-b0bf-48d3-beeb-0c9d800c33e1 ro quiet [COLOR="Red"]splash[/COLOR]
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=efd7320d-b0bf-48d3-beeb-0c9d800c33e1 ro single
initrd		/initrd.img-2.6.20-15-generic

```

I removed "splash" (in red) and now it boots fine.

---

### Post by karellen on 2007-04-21
ok, I'll try these suggestions

---

### Post by cvi on 2007-04-21
I have the same problem. It looked like (at least for me ) that the ide modules weren't being loaded so it couldn't load the rest of the startup stuff cause it wasn't seeing it. After I loaded the ide module(s) and typed exit. It booted up.

---

### Post by brutal_deluxe on 2007-04-21
> **cvi said:**
> I have the same problem. It looked like (at least for me ) that the ide modules weren't being loaded so it couldn't load the rest of the startup stuff cause it wasn't seeing it. After I loaded the ide module(s) and typed exit. It booted up.

Same problem here too.  How did you load the ide modules? I have tried
[I][B]modprobe ide-disk
modprobe ide-generic[/B][/I]
at the busybox prompt in an attempt to find and mount the root parition but my two harddisks (which are attached to a pci ata controller card) are never found and my cdrom found only occaisionally. Generally it just returns
***ide0: ports already in use, skipping probe***
I'm pretty sure that the UUID in *menu.lst* and *fstab* are consistent.  Some threads seem to indicate that with the new kernel PATA disks previously labelled *hdxx* are now changed to (or supplemented by) *sdxx* entries in */etc/mtab*.  No changes have been made to my *mtab* file.  Is this the problem?

---

### Post by brutal_deluxe on 2007-04-21
> disks previously labelled hdxx are now changed to (or supplemented by) sdxx entries in /etc/mtab. 
whoops, I meant */boot/grub/device.map* not */etc/mtab*

---

### Post by josel on 2007-04-22
I got
> root@mira:~# ls /dev/disk/by-uuid -lh
total 0
lrwxrwxrwx 1 root root 10 2007-04-22 13:22 2f2237d4-8958-41e8-b563-c52be76f688b -> ../../sdb1
lrwxrwxrwx 1 root root 10 2007-04-22 13:22 a9908951-e1d0-4414-93e1-670c36998bd5 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-04-22 13:22 e07d5887-b280-4510-b466-6a9cd8b1c36f -> ../../sda5
root@mira:~#                                                                                  

and
> root@mira:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hdc1
UUID=a9908951-e1d0-4414-93e1-670c36998bd5 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hdc5
UUID=e07d5887-b280-4510-b466-6a9cd8b1c36f none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sdb1 /home/delt auto users,atime,auto,rw,nodev,noexec,nosuid 0 0
root@mira:~#  

and 
part of menu.lst
> title           Ubuntu, kernel 2.6.20-15-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-386 root=UUID=a9908951-e1d0-4414-93e1-670c36998bd5 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-386
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-386 root=UUID=a9908951-e1d0-4414-93e1-670c36998bd5 ro single
initrd          /boot/initrd.img-2.6.20-15-386

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=a9908951-e1d0-4414-93e1-670c36998bd5 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=a9908951-e1d0-4414-93e1-670c36998bd5 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, kernel 2.6.20-12-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-12-generic root=UUID=a9908951-e1d0-4414-93e1-670c36998bd5 ro quiet splash
initrd          /boot/initrd.img-2.6.20-12-generic
quiet
savedefault

my main disk was hdc in edgy so im wondering why i can boot in 2.6.20-12 and not 2.6.20-15 ist there any entryes connected to  2.6.20-15 that i can try to alter?

---

### Post by trico on 2007-04-23
My symptoms are very similar to Karellen's and Josel's.  Except the kernels that work and don't work seem to differ.

I upgraded from 6.1 to 7.04 taking the upgrade path (not live disk) and have ended up with three kernels to choose from when I boot.  2.6.20-15 and 2.6.17-11 both fail with the TTY complaint that Karellen noted at the start of this thread.  But 2.6.17-10 works.  I haven't a clue why.

My system has two disks, hda and hdd.  The linux partition is hdd1.

> 
larry@trico:~$ ls /dev/disk/by-uuid -lh
total 0
lrwxrwxrwx 1 root root 10 2007-04-23 13:59 4187-66F9 -> ../../hdd3
lrwxrwxrwx 1 root root 10 2007-04-23 13:59 6ac13ccd-52dd-4cde-9944-c798662f34cc -> ../../hda2
lrwxrwxrwx 1 root root 10 2007-04-23 13:59 8802f316-b157-4e44-93cb-c8a7d97bf1a9 -> ../../hda3
lrwxrwxrwx 1 root root 10 2007-04-23 13:59 a3c29acf-679f-4261-890b-bbd41fe4d5c7 -> ../../hdd2
lrwxrwxrwx 1 root root 10 2007-04-23 13:59 D6988F4D988F2AD7 -> ../../hda1



> 
larry@trico:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd1       /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=D6988F4D988F2AD7 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdd3
UUID=4187-66F9  /media/hdd3     vfat    defaults,utf8,umask=007,gid=46,shortname=winnt 0       1
# /dev/hda2
UUID=6ac13ccd-52dd-4cde-9944-c798662f34cc none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


And from /boot/grub/menu.lst
> 
title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=/dev/hdd1 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=/dev/hdd1 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hdd1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hdd1 ro single
initrd          /boot/initrd.img-2.6.17-11-generic

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdd1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdd1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet



---

### Post by Corvo78 on 2007-04-24
I don't know if any of this information helps, but here goes anyway.
I upgraded my recently installed Edgy to Feisty.

Before I started I removed everything Beryl-related and also changed my xorg.conf to use the 'nv' driver instead of the restricted Nvidia driver.Then I backed up my /boot and xorg.conf.
Last but not least: I upgraded.

Usually any update which modifies my grub, always ends up b0rking my system.
So, before restarting I re-edited my Grub's menu.lst so the I would boot from sdd1 (which I always did).

Guess what... I restart and nothing boots. "Waiting for root file system".
After trying the kernels I find out that only the latest generic-kernel works but still dies during start-up.
Well, long story short: The latest kernel identifies my drives differently. So, my main-drive which was sdd1 is now sde1.
For some reason all drives (even those from my USB memory-cards reader) were re-ordered.

Since I have more then 1 drive and corresponding partitions, I ended up editing my fstab aswell (using Live-CD).
Since in my fstab everything was pointing to an incorrent drive.

After that, my system was alive again. Once that was sorted: feisty works great.


Again, in short my upgrade:[list][*]Only the latest generic kernel played nice[*]Kernel (or grub) identifies my drives differently (sde1 instead of sdd1)[*]fstab contains wrong drive identifications[/list]


Hope this helps anyone doing an upgrade from Edgy to Feisty.

---

### Post by kalimotxo on 2007-04-24
I have exactly a similar problem:

First of all i will describe my sistem:
Pentium IV 1.5 Mhz on a SiS 645DX/961B (NS70-EL from DFI) chipset board, with two ATA Hard Disk. I am trying to install feisty final release, and with the feisty livecd, hard disks are partitioned like this:

First Hard Disk 40 gb (Master of IDE1)
hda1-> Windows XP (30 gb). I want to keep it aswell.
hda2-> / (8.5 gb approx)
hda3-> swap (1.5 gb approx)

Second Hard Disk 120 gb (Slave of IDE1)
hdb-> /home (120 gb)

After installing, i reboot and the remove the livecd, and when when grub loads, I select the latest Kernel (2.6.20-15), and then the progressbar does not make any progress. (Same bug in the Kernel (2.6.20-12 to 2.6.20-15 last one). After one or two minutes i can see this:

"Udevd-event [1950]: run-program: '/sbin/modprobe' abnormal exit

BusyBox v.1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-install (ash)

/bin/sh: can access tty; job control turned off (initramfs)"

and this:

"ALERT! /dev/disk/by-uuid/xxxxxxxxxxx Does not exist, dropping to a shell"

i thinks that "xxxxxxxxxxxx" is the by-uuid identificator for the system disk "/"
The number of Udevd-event [xxxx] can vary from 1950 to 1960 (in other install tryings)
The system works perfectly with Edgy with the same partitioning configuration.

---

### Post by Corvo78 on 2007-04-24
I guess that means your Grub's menu.lst uses a disk's UUID?
Perhaps you could try changing it to /dev/hda2

---

### Post by kalimotxo on 2007-04-24
I tryed it already, but it didn't work, it's simply that feisty doesn't recognize pata (ide) hard disks.

---

### Post by Corvo78 on 2007-04-24
I remember that SATA and PATA drives don't play nice when it comes to Grub.
Alas, I don't remember the specific details. It had something to do with the fact
that Grub would use a different order then Ubuntu. So in one case the Sata drives came first,
and in the other case the Pata drives came first.
I think this applies to ```
root (hd1,0)
```
You could try changing that?
If you switch to manual Grub commands (I believe you have to press C for that), then enter:```
find /boot/grub/stage2
```And see if the output matches...


That's about all I have learned concerning Grub. Hopefully you'll get it sorted out or someone else whose knowledgeable will help you out ;)

---

### Post by Klaynos on 2007-04-24
I'm getting the same problem. An update of edgy to feisty.

I also get the problem in the live CD if I do not use the safe graphics mode.

It wont book in kernals 2.6.20-15 or 2.6.17-11 but will using 2.6.17-10.

It will also boot successfully into recovery mode.

It did book once, I edited xorg.conf to change from the nvidia driver to the nv driver, restarted and it booted fine.

How can I find out in recovery mode what sdb# the uuid that it says is failing is pointing to to see if I need to rename them?

---

### Post by Corvo78 on 2007-04-24
Not sure, but I believe it was something like this:```
ls /dev/disk/by-uuid
```

---

### Post by Klaynos on 2007-04-24
I've fixed my problem with the fix found here:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964/comments/61](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964/comments/61)

---

### Post by trico on 2007-04-25
Perhaps I'm doing something wrong.  It didn't work for me.

I applied the changes reported in the bug-report, ran initramfs -u (working from memory... it was something like that).  Rebooted - same problem.

trico

---

### Post by r!ots on 2007-05-01
I'm experiencing something similar:

I updated from ubuntu 6.10 using the update manager. When I restarted the PC and booted the 2.6.20-15-386 kernel it hang at "loading hardware drivers" and flashed two keyboard led's.
I tried booting in the recovery mode, but it stopped at the same point and came up with the following message:

> floppy0: sensei repl[0]=80
floppy0: unexpected interrupt.

Then I booted in the 2.6.17-11-386 kernel and apart from the X-server it worked fine. I'm now using the nv-drivers and running the old kernel.

Do you have any ideas why the boot process hangs at this point?

---

