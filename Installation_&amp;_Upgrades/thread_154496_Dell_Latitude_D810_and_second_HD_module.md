---
title: "Dell Latitude D810 and second HD module"
date: 2006-04-03
forum: Installation &amp; Upgrades
---

### Post by Mr_Grieves on 2006-04-03
Hello,

I'm having problems installing Breezy on a Dell Latitude D810 laptop.
The problem I'm having is that the second hard drive module (detected as ATA FUJITSU MHV2040A) does not seem to work properly.

I'm installing off two USB drives (one with the boot image and one with the .iso file), which works allright. It's because I don't have a CD/DVD, but two hard drives instead. On the primary I run Windows, on the secondary I want to run Ubuntu.

I need to boot with "linux vga=771" to get the screen to work properly.

The disk is recognices and I seem to be able to build the filesystem (ext3+swap) on the drive, but when I come to the "Install the base system"-part, the install system fails and gives this error message:

```

The debootstrap program exited with an error (return value 1).
Check /target/var/log/bootstrap.log for the details

```

The thing is.. there is no files in /target/var/log, at all.
When I execute a shell and check dmesg I might get a clue why.
I get the error below, ALOT of times:

```

[4295688.990000] loop0: rw=0, want=1202716, limit=792032
[4295688.990000] attempt to access beyond end of device

```

Note: [4295688.990000] is numbers that differs between the rows.

I wonder if it is so that my so called Dell "secondary hard drive module" - the FUJITSU drive.. is not supported.. or if there is any other problem.

According to [http://tkrat.org/d810/](http://tkrat.org/d810/) it seems to be a kernel issue, and that it should work with the 2.4 kernel. My question then is.. how can I get Ubuntu installed with a 2.4 kernel. As I understand it is shipped with 2.6.

I've tried all the boot-switches that is suggested for SCSI and Dell, without any luck.

---

### Post by nauticalthinker on 2006-04-03
Have you tried looking at the virtual console during the install to see what is happening?  Try ctrl+alt+F3.  Report back what you see.

---

### Post by nauticalthinker on 2006-04-03
Actually, I see that you checked dmesg....So, never mind....

Breezy comes only with kernel 2.6 -- That is my understanding anyway.

It appears that your system is trying to access an inode that is well beyond the defined boundaries of your disk.  This could mean a memory or hard drive problem.    

I wonder if you can do this:
Once your file system is created and before continuing with the base install - Open a terminal and issue this command: dumpe2fs -h /dev/<partition#>
<partition#> = something like hda1 or what ever yours is on

You may not be able to issue that command, but we can at least see.  Report back anything related to inode and blocks.  This may help diagnose the issue.  

Anyone else have a suggestion?

---

### Post by Mr_Grieves on 2006-04-04
Ok. I ran dumpe2fs -h on the dev where /target is mounted.

#target/sbin/dumpe2fs -h /dev/scsi/host1/bus0/target0/lun0/part1
```

Last mounted on: <not available>
Filesystem features: has_journal filetype needs_recovery sparse_super
Default mount options: (none)
Filesystem state: clean
Error behavior: Continue
Filesystem OS type: Linux
Inode count: 4685824
Block count: 9361870
Reserved block count: 468093
Free blocks: 9182003
Free inodes: 4685813
First block: 0
Block size: 4096
Fragment size: 4096
Blocks per group: 32768
Fragments per group: 32768
Inodes per group: 16384
Inode blocks per group: 512
First inode: 11
Inode size: 128
Journal inode: 8
Journal backup: inode blocks

```

---

### Post by Mr_Grieves on 2006-04-04
I just notices something. Like i wrote before. I'm not using a CD or DVD drive. Just two USB drives. But when I check 'df' I get:

```

#df
Filesystem	1k-blocks	Used	Mounted on
tmpfs		102400		32668	/
none		5120		2760	/dev
none		5120		2760	/.dev
/dev/discs/disc2/part1 19517424 5331792 /hd-media
/dev/loop/0	631962		0	/cdrom
/dev/scsi/host1/bus0/target0/lun0/part1 36859272 195100 /target

```
What I don't get it.. what's with the /cdrom ... and what's /dev/loop/0?
The fault that seems to fail the installation was about loop0..

```

[4295688.990000] loop0: rw=0, want=1202716, limit=792032
[4295688.990000] attempt to access beyond end of device

```

---

### Post by Mr_Grieves on 2006-04-04
I've tried to boot-up with 'linux memtest'. It doesn't complain about anything. Everything continues as usual, til I get to the "Install the base system" section.

---

