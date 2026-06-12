---
title: "update-grub doesn't boot new kernels"
date: 2014-01-18
forum: Installation &amp; Upgrades
---

### Post by ersatzsplatt on 2014-01-18
When I run update-grub, I see kernels being found, but when I reboot I do not see the latest kernels in the boot menu.

update-grub doesn't boot new kernels

I'm running Ubuntu 13.10; 3.11.0-13-generic #20-Ubuntu SMP Wed Oct 23 07:38:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

I see:
/boot/vmlinuz-3.11.0-12-generic
/boot/vmlinuz-3.11.0-13-generic
/boot/vmlinuz-3.11.0-13-generic.efi.signed
/boot/vmlinuz-3.11.0-14-generic
/boot/vmlinuz-3.11.0-14-generic.efi.signed
/boot/vmlinuz-3.11.0-15-generic
/boot/vmlinuz-3.11.0-15-generic.efi.signed

in /boot/grub/grub.cfg I see e.g.:
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menu
entry_id_option 'gnulinux-simple-a7c2475c-8313-4a46-892f-6264b36232bc' {
recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos6'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-
efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  a7c2475c-8313-4a46-892f-6264b36232
bc
        else
          search --no-floppy --fs-uuid --set=root a7c2475c-8313-4a46-892f-6264b3
6232bc
        fi
        linux   /boot/vmlinuz-3.11.0-15-generic root=UUID=a7c2475c-8313-4a46-892f-6264b36232bc ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.11.0-15-generic


The menu shows me 3.11.0-13 and 3.11.0-12 options as well as some older kernel options from another install and another disc.  I got the newer (14 and -15) kernels from updates.  I would like to be able to use them.

is update-grub just broken?  Shouldn't the menu options just autmatically update when I run update-grub?

---

### Post by grahammechanical on 2014-01-18
I have often found it useful to run two commands

```
sudo update-grub
sudo grub-install /dev/sda
```

Assuming that you only have one hard disk (sda). If you have a second hard disk and want Grub in the MBR of the second hard disk (sdb). Then it would be /dev/sdb. The first command updates the Grub configuration file. The second command installs Grub. I have found that the second command is needed and solves this problem.

Regards.

---

### Post by ubfan1 on 2014-01-18
When you have multiple installations, the grub menu is typically pulled from the last one installed.  Updating the other grub.cfg file does nothing, until you rerun the grub-install, which switches the files grub uses.

---

### Post by ersatzsplatt on 2014-01-19
O.k., the whole "use grub-install also" thing looks like a fair point.  Thank you very much for the replies.  Sadly, I am not quite yet enlightened enough to get it all working quite right.  I am in fact running on an external (usb connected) second drive -- so grahammechanical, where mount tells me I am on /dev/sdb ( "/dev/sdb6 on / type ext4 (rw,errors=remount-ro)" ), and I'm booting from said external drive and in particular external drive's grub, I expect to be able to run "sudo grub-install /dev/sdb" and get to where I want ... but no.
I get this sequence:
$ sudo update-grub
Generating grub.cfg ...
[everything I expect -- and looks correct here]
done

$ sudo grub-install /dev/sdb
source_dir doesn't exist. Please specify --target or --directory

---

### Post by carl4926 on 2014-01-19
How about we see

```
sudo fdisk -l
```

---

### Post by ersatzsplatt on 2014-01-19
carl4926, thank you for your interest and responsiveness.

fdisk -l seems a bit more than the detail needed, but no harm so here it is all the same:
$ sudo fdisk -l
[sudo] password for [the guy writing this posed question]: 

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0001478d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   651013822   325505887+  83  Linux
/dev/sda2       651014142  1465147391   407066625    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      1431824384  1465147391    16661504   82  Linux swap / Solaris
/dev/sda6       651014144  1431824383   390405120   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500074283008 bytes
255 heads, 63 sectors/track, 60797 cylinders, total 976707584 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b1726

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   161263318    80630635+  83  Linux
/dev/sdb2       161263614   976705535   407720961    5  Extended
/dev/sdb5       943382528   976705535    16661504   82  Linux swap / Solaris
/dev/sdb6       161263616   935823359   387279872   83  Linux
/dev/sdb7       935825408   943368191     3771392   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by carl4926 on 2014-01-19
So you have 2 HDD's and I assume a couple of Linux installations

The way to manage this is already described. From your running Ubuntu installation:

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

What is the other Linux OS?

---

### Post by ersatzsplatt on 2014-01-19
carl4926, thank you again for your advice.

The thing I don't like about grub-install on /dev/sda is I want to be able to boot my external drive from other machines as well.  I'm assuming here that grub-install /dev/sda will install on my internal drive and not affect the external drive.  I am already booting off of the external drive and I intend to leave the internal drive alone.

I don't see that what is on the internal drive matters given my use case, but again it doesn't hurt for me to mention either -- the internal drive has 12.04 32 bit and a botched 12.04 64-bit, or something like that.  I have a whole different set of things going on there and I intend to leave that well alone.

... so the question remains, how to I update the grub on /dev/sdb?

---

### Post by carl4926 on 2014-01-19
Is sda 750 GB internal or external
Is sdb 500 GB internal or external

Are there any other HD's in play at all?

So to be clear 
As I read: sda is Ub 12.04 and I think internal

sdb could be 13.10 and possibly external (USB?)

---

### Post by ersatzsplatt on 2014-01-19
Seems like you are clear.  sda is internal, and I believe it is 750G.  sdb is external and looks like it is about 500G by what I've already shown.
To be more clear, I don't care about what is on sda for the purposes of this post.
I'm looking to be able to boot into the newer kernels on sdb FROM sdb when booting through grub on sdb.
On another system, sda may have something entirely different, and I would like to boot from this external drive there -- into the NEWER kernels.
I'm already able to boot from sdb into the older kernels (on another system with a single internal hard drive as well).

Something beyond the scope of this initial post is another question:
If the system I have attached the external drive to has more than one internal drive, what do I have to do to boot into my external drive if I am using the external drive grub and I would like to be able to boot from the external drive on systems with one internal drive also?  ... but I suppose I should just make a separate post for that.

---

### Post by carl4926 on 2014-01-19
If you disconnect sda
Can you boot entirely from the USB external?

---

### Post by Bashing-om on 2014-01-20
Guys; hey,

This might come into play;
> 
the internal drive has 12.04 32 bit and a botched 12.04 64-bit
 if os-prober from the primaries' grub is picking up that "botched" install (??).

I am presently triple booting, and how I manage my grub is:
I have grub installed for each install onto the MBR of each disk, ok, now I run "update-grub" on EACH install, and on my primary (the os that is controlling booting) I run install "sudo grub-install /dev/sda" as a last step. Because my primary controlling OS is located on that first hard drive (sda). The control grub picks up all the other operating systems,

The fallacy of my way is that each time there is a update to the kernels, I must go through that routine each time; to get my grub boot menu back in order (10 minutes !).
```

sysop@1310mini:~$ sudo blkid
/dev/sda1: LABEL="1310mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1310mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1204" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1310mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
/dev/sdc1: LABEL="ubie1204" UUID="5bae8c40-b15d-42f8-9fc9-0cf087f338d4" TYPE="ext4" 
sysop@1310mini:~$

```

Note ersatzsplatt, though I have 3 OS installed, all share a single swap partition. Hint . But as you are travelling with one of the drives ya do need to keep a swap on that traveling drive.

[INDENT][INDENT][INDENT]my little bit to help
[/INDENT][/INDENT][/INDENT]

---

### Post by ersatzsplatt on 2014-01-20
carl4926, I don't think I would be able to boot from the external drive if I disconnected from sda, because grub would then reference the external drive as sda and would look for sdb.  You are really asking something related to the question I asked in my last post, which is beyond the scope of the narrow question I'm asking.  The question I'm asking is how to get an updated grub on the external drive I'm booting from.
The question which seems beyond the scope of that question, is how to boot from the external drive on any system regardless of the number of drives already connected to that system.
Bashing-om, you seems to have an interesting use case.  I'm still not sure how I can update the grub on my external drive though.

---

### Post by carl4926 on 2014-01-20
If the external is sdb
Check it is seen as sdb in fdisk and gparted

But I think you tried
```
sudo grub-install /dev/sdb
```

The problem I think might be that sdb is not /dev
but rather (is it) /var/run/media/youruernmame/device-id

---

### Post by Zhivargo on 2014-01-20
There are a lot of tutorials about manually adding a grub bootloader entry... 


But if you want to boot from your external drive treat it like a usb stick: 
make it bootable with syslinux ... right?

---

### Post by Bashing-om on 2014-01-20
et al; Good points.

I failed to mention that the OS/kernel placement in the grub menu is paramount. That primary boot system must be the 1st entry to default to.
I would also insure I was using the device's unique UUID.

Cavsfan has authored a great tutorial on maintaining one's grub:
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

drs305 is our guru on anything grub:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

It is doable
[INDENT][INDENT][INDENT]and you can do this
[/INDENT][/INDENT][/INDENT]

---

### Post by philinux on 2014-01-20
Ersatzsplatt.

Double check you have the package linux-generic installed

---

### Post by philinux on 2014-01-20
Also run this and post back the results.txt file. 

Bootinfoscript.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by efflandt on 2014-01-21
Are you absolutely certain that you are "booting" the external drive, or is it possible that grub on the internal drive is actually booting to it (and may be why kernels are missing)? With some computers (particularly Dell), even if you change the device boot order in CMOS, you may still need to press a hotkey in the BIOS splash screen to select the drive to boot from, for anything other than an internal drive.

---

### Post by ersatzsplatt on 2014-01-22
> **carl4926 said:**
> If the external is sdb
Check it is seen as sdb in fdisk and gparted

But I think you tried
```
sudo grub-install /dev/sdb
```

The problem I think might be that sdb is not /dev
but rather (is it) /var/run/media/youruernmame/device-id

Nope.  It really is /dev/sdb -- I already replied to you with the fdisk information earlier in this thread.  Mount shows it is /dev/sdb too, so looking to change it somewhere it is not won't help me.

---

### Post by ersatzsplatt on 2014-01-22
> **efflandt said:**
> Are you absolutely certain that you are "booting" the external drive, or is it possible that grub on the internal drive is actually booting to it (and may be why kernels are missing)? With some computers (particularly Dell), even if you change the device boot order in CMOS, you may still need to press a hotkey in the BIOS splash screen to select the drive to boot from, for anything other than an internal drive.

I am absolutely certain I am booting from the external drive.  If I boot the same drive from another machine, I see the same install.  I'm quite sure.

Philinux, "linux-generic is already the newest version.", already installed.

---

### Post by ersatzsplatt on 2014-01-25
> **Bashing-om said:**
> et al; Good points.

I failed to mention that the OS/kernel placement in the grub menu is paramount. That primary boot system must be the 1st entry to default to.
I would also insure I was using the device's unique UUID.

Cavsfan has authored a great tutorial on maintaining one's grub:
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

drs305 is our guru on anything grub:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

It is doable[INDENT][INDENT][INDENT]and you can do this
[/INDENT]
[/INDENT]
[/INDENT]


Bashing-om, thank you for the references.  I spent a bit of time looking at them.  I still am not sure what to do to get grub to boot into the newer kernels though.  I'm a bit hesitant to go hack crazy on my grub, because I am using the boot now for productive efforts -- and it kinda works (even though it is not the newer kernel that I would hope for).
It would be great to get some input from drs305.  Now that you mention it, seems like drs305 knows a lot about grub and would probably be able to help me narrow down what needs to happen pretty quick.  I don't know how I can ask for a response from drs305 though.

It also seems like I'm dealing with a bug, maybe not a major bug, but still something is not working right.  I don't think that users should have to do any obscure tweaking of grub just to get the updates they've downloaded to run.  I'd be happy to try and help developers fix this, not just resolve my own issue.  Anyone know the preferred way to get in touch with the right people on this?

---

### Post by Bashing-om on 2014-01-25
ersatzsplatt; Hey ;
In regards to drs305:
[LIST]
[*]He is now retired
[*]I am not in his list of contacts
[*]I would not presume to interrupt his eminence 
[*]
[/LIST]
A bug ? Maybe but, more likely a misunderstanding of what is installed where.

Let's explore that thought and see what is:
See if we can finger this out.

When the external usb drive is connected, it is the primary boot device (sdb6), are the kernels in question available ?
Connect the external usb drive;
In BIOS make sure the 1st boot priority is that external USB drive
BOOT
OK, now let's look at what is:
show the outputs of terminal codes:
```

cat /etc/fstab
mount
ls -la /boot
ls -la /usr/src
sudo fdisk -lu

```
As I scratch my head and try to find that path to follow.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by ersatzsplatt on 2014-01-25
> **Bashing-om said:**
> ersatzsplatt; Hey ;
In regards to drs305:
[LIST]
[*]He is now retired 
[*]I am not in his list of contacts 
[*]I would not presume to interrupt his eminence 
[/LIST]
A bug ? Maybe but, more likely a misunderstanding of what is installed where.

Let's explore that thought and see what is:
See if we can finger this out.

When the external usb drive is connected, it is the primary boot device (sdb6), are the kernels in question available ?
Connect the external usb drive;
In BIOS make sure the 1st boot priority is that external USB drive
BOOT
OK, now let's look at what is:
show the outputs of terminal codes:
```

cat /etc/fstab
mount
ls -la /boot
ls -la /usr/src
sudo fdisk -lu

```
As I scratch my head and try to find that path to follow.
[INDENT][INDENT]where there is a will there is a way
[/INDENT]
[/INDENT]


Hey Bashing-om, thank you for another reply.

I gave most of that information earlier in this post, but here it is all in one place along with any detail that I stripped out before (in the interest of focus) and in the order of your request:

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=a7c2475c-8313-4a46-892f-6264b36232bc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=c34a1436-e88f-4b11-84a7-11032de36747 none            swap    sw              0       0


$ mount
/dev/sdb6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ersatz)
/dev/sdb1 on /media/ersatz/0a6f94fd-d20d-43c8-bfcf-69f9c3ed14b1 type ext4 (rw,nosuid,nodev,uhelper=udisks2)


$ ls -la /boot
total 132396
drwxr-xr-x  3 root root     4096 Jan 11 10:56 .
drwxr-xr-x 24 root root     4096 Jan 11 10:55 ..
-rw-r--r--  1 root root  1005798 Oct  9 09:49 abi-3.11.0-12-generic
-rw-r--r--  1 root root  1006439 Oct 23 01:10 abi-3.11.0-13-generic
-rw-r--r--  1 root root  1006439 Nov 12 09:33 abi-3.11.0-14-generic
-rw-r--r--  1 root root  1006496 Dec  9 10:45 abi-3.11.0-15-generic
-rw-r--r--  1 root root   163251 Oct  9 09:49 config-3.11.0-12-generic
-rw-r--r--  1 root root   163255 Oct 23 01:10 config-3.11.0-13-generic
-rw-r--r--  1 root root   163255 Nov 12 09:33 config-3.11.0-14-generic
-rw-r--r--  1 root root   163245 Dec  9 10:45 config-3.11.0-15-generic
drwxr-xr-x  5 root root     4096 Jan 19 19:12 grub
-rw-r--r--  1 root root 25993952 Dec  2 11:05 initrd.img-3.11.0-12-generic
-rw-r--r--  1 root root 17311690 Dec  2 11:08 initrd.img-3.11.0-13-generic
-rw-r--r--  1 root root 17313072 Dec  4 23:19 initrd.img-3.11.0-14-generic
-rw-r--r--  1 root root 17433456 Jan 11 10:56 initrd.img-3.11.0-15-generic
-rw-r--r--  1 root root   176500 Jun 17  2013 memtest86+.bin
-rw-r--r--  1 root root   178680 Jun 17  2013 memtest86+_multiboot.bin
-rw-------  1 root root  3285893 Oct  9 09:49 System.map-3.11.0-12-generic
-rw-------  1 root root  3286187 Oct 23 01:10 System.map-3.11.0-13-generic
-rw-------  1 root root  3286278 Nov 12 09:33 System.map-3.11.0-14-generic
-rw-------  1 root root  3293845 Dec  9 10:45 System.map-3.11.0-15-generic
-rw-r--r--  1 root root  5600032 Dec  2 10:47 vmlinuz-3.11.0-12-generic
-rw-------  1 root root  5600496 Oct 23 01:10 vmlinuz-3.11.0-13-generic
-rw-------  1 root root  5602424 Dec  2 11:03 vmlinuz-3.11.0-13-generic.efi.signed
-rw-------  1 root root  5601072 Nov 12 09:33 vmlinuz-3.11.0-14-generic
-rw-------  1 root root  5603000 Dec  4 23:19 vmlinuz-3.11.0-14-generic.efi.signed
-rw-------  1 root root  5631184 Dec  9 10:45 vmlinuz-3.11.0-15-generic
-rw-------  1 root root  5633112 Jan 11 10:55 vmlinuz-3.11.0-15-generic.efi.signed


$ ls -la /usr/src
total 40
drwxr-xr-x 10 root root 4096 Jan 11 10:54 .
drwxr-xr-x 11 root root 4096 Dec  7 09:40 ..
drwxr-xr-x 24 root root 4096 Oct 16 12:01 linux-headers-3.11.0-12
drwxr-xr-x  7 root root 4096 Oct 16 12:01 linux-headers-3.11.0-12-generic
drwxr-xr-x 24 root root 4096 Dec  2 11:01 linux-headers-3.11.0-13
drwxr-xr-x  7 root root 4096 Dec  2 11:01 linux-headers-3.11.0-13-generic
drwxr-xr-x 24 root root 4096 Dec  4 23:15 linux-headers-3.11.0-14
drwxr-xr-x  7 root root 4096 Dec  4 23:15 linux-headers-3.11.0-14-generic
drwxr-xr-x 24 root root 4096 Jan 11 10:54 linux-headers-3.11.0-15
drwxr-xr-x  7 root root 4096 Jan 11 10:54 linux-headers-3.11.0-15-generic


ersatz@mysystem:~$ sudo fdisk -lu
[sudo] password for ersatz: 

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0001478d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   651013822   325505887+  83  Linux
/dev/sda2       651014142  1465147391   407066625    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      1431824384  1465147391    16661504   82  Linux swap / Solaris
/dev/sda6       651014144  1431824383   390405120   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500074283008 bytes
255 heads, 63 sectors/track, 60797 cylinders, total 976707584 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b1726

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   161263318    80630635+  83  Linux
/dev/sdb2       161263614   976705535   407720961    5  Extended
/dev/sdb5       943382528   976705535    16661504   82  Linux swap / Solaris
/dev/sdb6       161263616   935823359   387279872   83  Linux
/dev/sdb7       935825408   943368191     3771392   82  Linux swap / Solaris

Partition table entries are not in disk order


... see, there are newer kernels there.  

$ uname -a
Linux mysystem 3.11.0-13-generic #20-Ubuntu SMP Wed Oct 23 07:38:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

I'm saying a bug is likely in that, even if I can get this to work, I have not done anything that should prevent the system from updating to the latest kernel and using it.  The fact that it takes more than the usual two step sequence to fix it also is an indication that something is wrong with the update package or more likely grub utilities.

Thanks for looking at it.

---

### Post by Bashing-om on 2014-01-25
ersatzsplatt; Well !

As you say, all appears in proper order.
One more thing to look at- that slipped my mind:
Let's insure the UUIDs are correct.
post back:
```

sudo blkid

```

And then we will start tracking.

[INDENT][INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT][/INDENT]

---

### Post by ersatzsplatt on 2014-01-25
> **Bashing-om said:**
> ersatzsplatt; Well !

As you say, all appears in proper order.
One more thing to look at- that slipped my mind:
Let's insure the UUIDs are correct.
post back:
```

sudo blkid

```

And then we will start tracking.
[INDENT][INDENT][INDENT]inquiring minds want to know
[/INDENT]
[/INDENT]
[/INDENT]


sure thing:
$ sudo blkid
[sudo] password for ersatz: 
/dev/sda1: UUID="748126a4-31ff-488a-bab7-2dcb6b2098f5" TYPE="ext4" 
/dev/sda6: UUID="aa6d5d95-b411-4da7-8a2d-aa1b477e7aa7" TYPE="ext4" 
/dev/sdb1: UUID="0a6f94fd-d20d-43c8-bfcf-69f9c3ed14b1" TYPE="ext4" 
/dev/sdb6: UUID="a7c2475c-8313-4a46-892f-6264b36232bc" TYPE="ext4" 
/dev/sdb7: UUID="c34a1436-e88f-4b11-84a7-11032de36747" TYPE="swap"

---

### Post by Bashing-om on 2014-01-26
ersatzsplatt; Well,

I have been giving this a lot of consideration during my absence >
I do have 3 courses of action in mind.
Before proceeding I want to see what we are working with as far as permissions, and executable bits,
```

ls -la /etc/default/grub
cat /etc/default/grub
ls -la /etc/grub.d

```

Will see if these change my mind about (re-)installing "initramfs-tools".

[INDENT][INDENT]a puzzle indeed !
[/INDENT][/INDENT]

---

### Post by ersatzsplatt on 2014-01-26
> **Bashing-om said:**
> ersatzsplatt; Well,

I have been giving this a lot of consideration during my absence >
I do have 3 courses of action in mind.
Before proceeding I want to see what we are working with as far as permissions, and executable bits,
```

ls -la /etc/default/grub
cat /etc/default/grub
ls -la /etc/grub.d

```

Will see if these change my mind about (re-)installing "initramfs-tools".
[INDENT][INDENT]a puzzle indeed !
[/INDENT]
[/INDENT]


I do believe this is all going to be default/norm.  I haven't done anything really unusual -- except installing on the external drive.

$ ls -la /etc/default/grub
-rw-r--r-- 1 root root 1238 Dec  2 11:06 /etc/default/grub



$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



$ ls -la /etc/grub.d
total 88
drwxr-xr-x   2 root root  4096 Dec  2 11:05 .
drwxr-xr-x 139 root root 12288 Jan 25 14:58 ..
-rwxr-xr-x   1 root root  7850 Oct 10 10:48 00_header
-rwxr-xr-x   1 root root  5949 Aug 15 01:26 05_debian_theme
-rwxr-xr-x   1 root root 11479 Oct 10 10:48 10_linux
-rwxr-xr-x   1 root root 10258 Oct 10 10:48 20_linux_xen
-rwxr-xr-x   1 root root  1798 Jun 17  2013 20_memtest86+
-rwxr-xr-x   1 root root 11531 Oct 10 10:48 30_os-prober
-rwxr-xr-x   1 root root  1426 Oct 10 10:48 30_uefi-firmware
-rwxr-xr-x   1 root root   214 Oct 10 10:48 40_custom
-rwxr-xr-x   1 root root   216 Oct 10 10:48 41_custom
-rw-r--r--   1 root root   483 Oct 10 10:48 README


seems like a checksum and/or version numbers should clear anything up that might be a benefit from reinstall of tools or other packages.

---

### Post by Bashing-om on 2014-01-26
ersatzsplatt; Yep,

As you say, no fault found.
Ok here goes:
```

sudo apt-get install linux-generic linux-headers-generic linux-image-generic
sudo apt-get clean initramfs-tools
sudo apt-get update
sudo apt-get install --reinstall initramfs-tools
sudo apt-get upgrade

```
clean initramfs-tools will delete the old kernel.debs from your package cache.
update will refresh the package lists from the updates repository, letting your system know that 15. is available
install --reinstall initramfs-tools will force the system to reinstall the initramfs-tools package from the .deb in cache. But we just deleted the .debs, so the system will download a fresh 15.deb from the repository, and then replace the old version running on your system. 
upgrade will upgrade all of all packages on your system that have an upgrade available. It confirms that your package manager is working properly again, REBOOT and confirm that the problem really is fixed.

Looks reasonable to me !
[INDENT][INDENT][INDENT]workie great ?
[/INDENT][/INDENT][/INDENT]

---

### Post by ersatzsplatt on 2014-01-26
> **Bashing-om said:**
> ersatzsplatt; Yep,

As you say, no fault found.
Ok here goes:
```

sudo apt-get install linux-generic linux-headers-generic linux-image-generic
sudo apt-get clean initramfs-tools
sudo apt-get update
sudo apt-get install --reinstall initramfs-tools
sudo apt-get upgrade

```
clean initramfs-tools will delete the old kernel.debs from your package cache.
update will refresh the package lists from the updates repository, letting your system know that 15. is available
install --reinstall initramfs-tools will force the system to reinstall the initramfs-tools package from the .deb in cache. But we just deleted the .debs, so the system will download a fresh 15.deb from the repository, and then replace the old version running on your system. 
upgrade will upgrade all of all packages on your system that have an upgrade available. It confirms that your package manager is working properly again, REBOOT and confirm that the problem really is fixed.

Looks reasonable to me ![INDENT][INDENT][INDENT]workie great ?
[/INDENT]
[/INDENT]
[/INDENT]


$ sudo apt-get install linux-generic linux-headers-generic linux-image-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-generic is already the newest version.
linux-headers-generic is already the newest version.
linux-image-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.


$ sudo apt-get clean initramfs-tools


$ sudo apt-get update
... k, that is a bit too much to paste for any use
...
Fetched 806 kB in 23s (33.6 kB/s)
Reading package lists... Done


$ sudo apt-get install --reinstall initramfs-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 21 not upgraded.
Need to get 49.1 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/main initramfs-tools all 0.103ubuntu1.1 [49.1 kB]
Fetched 49.1 kB in 0s (71.2 kB/s)          
(Reading database ... 264197 files and directories currently installed.)
Preparing to replace initramfs-tools 0.103ubuntu1.1 (using .../initramfs-tools_0.103ubuntu1.1_all.deb) ...
Unpacking replacement initramfs-tools ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file...
Setting up initramfs-tools (0.103ubuntu1.1) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-15-generic


$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  hplip hplip-data icedtea-7-jre-jamvm libhpmud0 libnspr4 libnspr4-0d libnss3
  libnss3-1d libsane-hpaio openjdk-7-jdk openjdk-7-jre openjdk-7-jre-headless
  openjdk-7-jre-lib printer-driver-hpcups printer-driver-postscript-hp
  python-cupshelpers simple-scan system-config-printer-common
  system-config-printer-gnome system-config-printer-udev
  xserver-xorg-video-intel
21 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 69.2 MB of archives.
After this operation, 1,467 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/universe libnspr4-0d amd64 2:4.9.5-1ubuntu1.1 [6,828 B]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/main libnspr4 amd64 2:4.9.5-1ubuntu1.1 [133 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/main libnss3-1d amd64 2:3.15.4-0ubuntu0.13.10.1 [12.4 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/main libnss3 amd64 2:3.15.4-0ubuntu0.13.10.1 [1,086 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/main openjdk-7-jdk amd64 7u51-2.4.4-0ubuntu0.13.10.1 [16.4 MB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/main openjdk-7-jre amd64 7u51-2.4.4-0ubuntu0.13.10.1 [225 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/main icedtea-7-jre-jamvm amd64 7u51-2.4.4-0ubuntu0.13.10.1 [604 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/main openjdk-7-jre-headless amd64 7u51-2.4.4-0ubuntu0.13.10.1 [41.5 MB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/main printer-driver-postscript-hp all 3.13.9-1ubuntu0.1 [687 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/main libsane-hpaio amd64 3.13.9-1ubuntu0.1 [138 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/main hplip amd64 3.13.9-1ubuntu0.1 [83.5 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/main libhpmud0 amd64 3.13.9-1ubuntu0.1 [115 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/main hplip-data all 3.13.9-1ubuntu0.1 [6,717 kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/main printer-driver-hpcups amd64 3.13.9-1ubuntu0.1 [318 kB]
Get:15 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/main openjdk-7-jre-lib all 7u51-2.4.4-0ubuntu0.13.10.1 [40.9 kB]
Get:16 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/main python-cupshelpers all 1.4.2+20130920-0ubuntu1.2 [32.1 kB]
Get:17 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/main simple-scan amd64 3.10.2-0ubuntu1 [157 kB]
Get:18 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/main system-config-printer-common all 1.4.2+20130920-0ubuntu1.2 [36.3 kB]
Get:19 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/main system-config-printer-gnome all 1.4.2+20130920-0ubuntu1.2 [136 kB]
Get:20 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/main system-config-printer-udev amd64 1.4.2+20130920-0ubuntu1.2 [18.7 kB]
Get:21 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/main xserver-xorg-video-intel amd64 2:2.99.904-0ubuntu2.1 [736 kB]
Fetched 69.2 MB in 8min 16s (139 kB/s)                                         
(Reading database ... 264197 files and directories currently installed.)
Preparing to replace libnspr4-0d:amd64 2:4.9.5-1ubuntu1 (using .../libnspr4-0d_2%3a4.9.5-1ubuntu1.1_amd64.deb) ...
Unpacking replacement libnspr4-0d:amd64 ...
Preparing to replace libnspr4:amd64 2:4.9.5-1ubuntu1 (using .../libnspr4_2%3a4.9.5-1ubuntu1.1_amd64.deb) ...
Unpacking replacement libnspr4:amd64 ...
Preparing to replace libnss3-1d:amd64 2:3.15.3.1-0ubuntu0.13.10.1 (using .../libnss3-1d_2%3a3.15.4-0ubuntu0.13.10.1_amd64.deb) ...
Unpacking replacement libnss3-1d:amd64 ...
Preparing to replace libnss3:amd64 2:3.15.3.1-0ubuntu0.13.10.1 (using .../libnss3_2%3a3.15.4-0ubuntu0.13.10.1_amd64.deb) ...
Unpacking replacement libnss3:amd64 ...
Preparing to replace openjdk-7-jdk:amd64 7u25-2.3.12-4ubuntu3 (using .../openjdk-7-jdk_7u51-2.4.4-0ubuntu0.13.10.1_amd64.deb) ...
Unpacking replacement openjdk-7-jdk:amd64 ...
Preparing to replace openjdk-7-jre:amd64 7u25-2.3.12-4ubuntu3 (using .../openjdk-7-jre_7u51-2.4.4-0ubuntu0.13.10.1_amd64.deb) ...
Unpacking replacement openjdk-7-jre:amd64 ...
Preparing to replace icedtea-7-jre-jamvm:amd64 7u25-2.3.12-4ubuntu3 (using .../icedtea-7-jre-jamvm_7u51-2.4.4-0ubuntu0.13.10.1_amd64.deb) ...
Unpacking replacement icedtea-7-jre-jamvm:amd64 ...
Preparing to replace openjdk-7-jre-headless:amd64 7u25-2.3.12-4ubuntu3 (using .../openjdk-7-jre-headless_7u51-2.4.4-0ubuntu0.13.10.1_amd64.deb) ...
Unpacking replacement openjdk-7-jre-headless:amd64 ...
Preparing to replace printer-driver-postscript-hp 3.13.9-1 (using .../printer-driver-postscript-hp_3.13.9-1ubuntu0.1_all.deb) ...
Unpacking replacement printer-driver-postscript-hp ...
Preparing to replace libsane-hpaio 3.13.9-1 (using .../libsane-hpaio_3.13.9-1ubuntu0.1_amd64.deb) ...
Unpacking replacement libsane-hpaio ...
Preparing to replace hplip 3.13.9-1 (using .../hplip_3.13.9-1ubuntu0.1_amd64.deb) ...
Unpacking replacement hplip ...
Preparing to replace libhpmud0 3.13.9-1 (using .../libhpmud0_3.13.9-1ubuntu0.1_amd64.deb) ...
Unpacking replacement libhpmud0 ...
Preparing to replace hplip-data 3.13.9-1 (using .../hplip-data_3.13.9-1ubuntu0.1_all.deb) ...
Unpacking replacement hplip-data ...
Preparing to replace printer-driver-hpcups 3.13.9-1 (using .../printer-driver-hpcups_3.13.9-1ubuntu0.1_amd64.deb) ...
Unpacking replacement printer-driver-hpcups ...
Preparing to replace openjdk-7-jre-lib 7u25-2.3.12-4ubuntu3 (using .../openjdk-7-jre-lib_7u51-2.4.4-0ubuntu0.13.10.1_all.deb) ...
Unpacking replacement openjdk-7-jre-lib ...
Preparing to replace python-cupshelpers 1.4.2+20130920-0ubuntu1.1 (using .../python-cupshelpers_1.4.2+20130920-0ubuntu1.2_all.deb) ...
Unpacking replacement python-cupshelpers ...
Preparing to replace simple-scan 3.10.0-0ubuntu1 (using .../simple-scan_3.10.2-0ubuntu1_amd64.deb) ...
Unpacking replacement simple-scan ...
Preparing to replace system-config-printer-common 1.4.2+20130920-0ubuntu1.1 (using .../system-config-printer-common_1.4.2+20130920-0ubuntu1.2_all.deb) ...
Unpacking replacement system-config-printer-common ...
Preparing to replace system-config-printer-gnome 1.4.2+20130920-0ubuntu1.1 (using .../system-config-printer-gnome_1.4.2+20130920-0ubuntu1.2_all.deb) ...
Unpacking replacement system-config-printer-gnome ...
Preparing to replace system-config-printer-udev 1.4.2+20130920-0ubuntu1.1 (using .../system-config-printer-udev_1.4.2+20130920-0ubuntu1.2_amd64.deb) ...
Unpacking replacement system-config-printer-udev ...
Preparing to replace xserver-xorg-video-intel 2:2.99.904-0ubuntu2 (using .../xserver-xorg-video-intel_2%3a2.99.904-0ubuntu2.1_amd64.deb) ...
Unpacking replacement xserver-xorg-video-intel ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support ...
Processing triggers for cups ...
Updating PPD files for hpcups ...
Updating PPD files for postscript-hp ...
Processing triggers for man-db ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0:amd64 ...
Setting up libnspr4:amd64 (2:4.9.5-1ubuntu1.1) ...
Setting up libnspr4-0d:amd64 (2:4.9.5-1ubuntu1.1) ...
Setting up libnss3:amd64 (2:3.15.4-0ubuntu0.13.10.1) ...
Setting up libnss3-1d:amd64 (2:3.15.4-0ubuntu0.13.10.1) ...
Setting up openjdk-7-jre-headless:amd64 (7u51-2.4.4-0ubuntu0.13.10.1) ...
Installing new version of config file /etc/java-7-openjdk/security/nss.cfg ...
Installing new version of config file /etc/java-7-openjdk/security/java.security ...
Installing new version of config file /etc/java-7-openjdk/security/java.policy ...
Installing new version of config file /etc/java-7-openjdk/content-types.properties ...
Setting up openjdk-7-jre:amd64 (7u51-2.4.4-0ubuntu0.13.10.1) ...
Setting up openjdk-7-jdk:amd64 (7u51-2.4.4-0ubuntu0.13.10.1) ...
Setting up icedtea-7-jre-jamvm:amd64 (7u51-2.4.4-0ubuntu0.13.10.1) ...
Setting up libhpmud0 (3.13.9-1ubuntu0.1) ...
Setting up libsane-hpaio (3.13.9-1ubuntu0.1) ...
Setting up hplip-data (3.13.9-1ubuntu0.1) ...
Setting up printer-driver-hpcups (3.13.9-1ubuntu0.1) ...
Setting up hplip (3.13.9-1ubuntu0.1) ...
Creating/updating hplip user account...
Setting up printer-driver-postscript-hp (3.13.9-1ubuntu0.1) ...
Setting up openjdk-7-jre-lib (7u51-2.4.4-0ubuntu0.13.10.1) ...
Setting up python-cupshelpers (1.4.2+20130920-0ubuntu1.2) ...
Setting up simple-scan (3.10.2-0ubuntu1) ...
Setting up system-config-printer-common (1.4.2+20130920-0ubuntu1.2) ...
Setting up system-config-printer-gnome (1.4.2+20130920-0ubuntu1.2) ...
Setting up system-config-printer-udev (1.4.2+20130920-0ubuntu1.2) ...
Setting up xserver-xorg-video-intel (2:2.99.904-0ubuntu2.1) ...
Processing triggers for libc-bin ...


I'll see on the reboot ...

---

### Post by ersatzsplatt on 2014-01-26
O.k., it is as if nothing has changed:

$ uname -a
Linux mysystem 3.11.0-13-generic #20-Ubuntu SMP Wed Oct 23 07:38:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

didn't see any new entries in the grub menu on boot.

---

### Post by ersatzsplatt on 2014-01-26
$ sudo update-grub
[sudo] password for ersatz: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-15-generic
Found initrd image: /boot/initrd.img-3.11.0-15-generic
Found linux image: /boot/vmlinuz-3.11.0-14-generic
Found initrd image: /boot/initrd.img-3.11.0-14-generic
Found linux image: /boot/vmlinuz-3.11.0-13-generic
Found initrd image: /boot/initrd.img-3.11.0-13-generic
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 12.04.3 LTS (12.04) on /dev/sda1
Found Ubuntu 12.04.3 LTS (12.04) on /dev/sda6
Found Ubuntu 12.04.3 LTS (12.04) on /dev/sdb1
done

$ sudo grub-install /dev/sdb
source_dir doesn't exist. Please specify --target or --directory

$ mount
/dev/sdb6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=bigd)
/dev/sdb1 on /media/bigd/0a6f94fd-d20d-43c8-bfcf-69f9c3ed14b1 type ext4 (rw,nosuid,nodev,uhelper=udisks2)


seems like grub-install will not take /dev/sdb as a valid argument.

any other suggestions?
what do we do if this is a bug?

thanks for the replies.

---

### Post by Bashing-om on 2014-01-26
ersatzsplatt; Yuk,

We know it is updated and the kernels are installed:
> 
Found linux image: /boot/vmlinuz-3.11.0-15-generic


as to why the system can not see /dev/sdb ; I don't have a clue presently.

Does a reboot affect a change ?

Let's take another look at the new config file:
```

cat /boot/grub/grub.cfg

```
as that is the file that the grub menu routine parses.

As to filing a bug report:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

[INDENT][INDENT][INDENT]as around and around we go
[/INDENT][/INDENT][/INDENT]

---

### Post by ersatzsplatt on 2014-01-27
o.k., started the report.

for the grub.cfg, it seems like a bit much to just paste here, so:
[http://paste.ubuntu.com/6824600/](http://paste.ubuntu.com/6824600/)

You can see that the later kernels are listed.
Doesn't really matter if it won't install though, right?

---

### Post by Bashing-om on 2014-01-27
ersatzsplatt; Good;

ubuntu's support structure at work !

I have been doing home work, what results from:
```

sudo update-initramfs -u -k 3.11.0-15-generic

```

see:
```

man update-initramfs

```

Gone to look at your bug report.

[INDENT][INDENT]gett'n to the bottom of things
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-01-27
The answer was given previously I think. Sounds like you are updating the grub that is not the grub you are using to boot. Whichever grub you're updating, get out of that install, boot the other install and update that grub. Reboot.

---

### Post by Bashing-om on 2014-01-27
@ Bucky Ball; 
I also had the thought that the OP was not booting sdb. Per outputs, he is ..

I am always taken aback by what I do not know or fully comprehend:
Compare your "BEGIN /etc/grub.d/05_debian_theme" with mine:
> 
### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1 --hint='hd0,msdos1'  3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
else
  search --no-floppy --fs-uuid --set=root 3a47f1f1-ed1f-4134-b6aa-be101a7d97b4
fi
insmod tga
if background_image /boot/grub/050817-N-3488C-028.tga; then
 set color_normal=cyan/black
 set color_highlight=light-cyan/black
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###


Huge difference - however, my grub is heavily modified, Still, will need to look at the significance of the OP's file's lack of direction.

Bucky Ball, what are your thoughts ?

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

