---
title: "Install error at GRUB (Dual-boot system)"
date: 2005-06-17
forum: Installation &amp; Upgrades
---

### Post by Ameet on 2005-06-17
I am trying to install Ubuntu 5.0.4 on a system that already has Windows XP installed.  The installation keeps stalling when its trying to install GRUB.

First, my partitions (it's a 40 GB hard drive):
```

hda1  primary  15.7 GB  NTFS  WindowsXP
hda2  primary  10.0 GB  ext3   /
hda4  primary   8.2 GB  ext3   /boot
hda5  logical  13.7 GB fat32  /home
hda6  logical 567.5 MB  swap

```

At the point when the installation script tries to set up the booting, I get the following error:
"Unable to install GRUB in (hd0).  Executing 'grub-install (hd0)' failed.  This is a fatal error."

I then picked the option to boot manually.  The installer told me I have to "boot manually with /vmlinuz kernel on /dev/hda2 and root=/dev/hda2", and that after Ubuntu loads up, it will complete the installation process.

Now, I have installed GRUB on a floppy disk, and so tried to use that to just get this going -- but can't.

1) trying to install GRUB to the MBR fails each time: GRUB says it can't recognize the filessystem 0x7 on (hd0).  (I think that's the Windows NTFS partition).

2) trying to boot up manually doesn't click either:

GRUB> root (hd0,1)
GRUB> kernel /vmlinuz root=/dev/hda2
  Error 15: File Not Found.

If I do find /vm <TAB>, I get filename completion for /vmlinuz, so I know the file is there in hda2 -- but GRUB insists it can't find it during the kernel loading.

Any suggestions?  I do have a Knoppix Live CD so I can use Linux commands if needed to try to fix this situation.

I can also boot normally into Windows XP (which is how I am reading this forum right now).

---

### Post by sf-andrew on 2005-06-18
[QUOTE=Ameet]I am trying to install Ubuntu 5.0.4 on a system that already has Windows XP installed.  The installation keeps stalling when its trying to install GRUB.

First, my partitions (it's a 40 GB hard drive):
```

hda1  primary  15.7 GB  NTFS  WindowsXP
hda2  primary  10.0 GB  ext3   /
hda4  primary   8.2 GB  ext3   /boot
hda5  logical  13.7 GB fat32  /home
hda6  logical 567.5 MB  swap

```

At the point when the installation script tries to set up the booting, I get the following error:
"Unable to install GRUB in (hd0).  Executing 'grub-install (hd0)' failed.  This is a fatal error."

...

I can also boot normally into Windows XP (which is how I am reading this forum right now).[/QUOTE]
 I am having the same problem. I tried installing GRUB on evey partition in turn, and then on a floppy, but without success (always the same "fatal error" message). I will be checking to see whether anyone answers your question!

Incidentally - how do you install GRUB on a floppy? Do you need to format the floppy in any special way?

---

### Post by Ameet on 2005-06-19
[QUOTE=sf-andrew]I am having the same problem. I tried installing GRUB on evey partition in turn, and then on a floppy, but without success (always the same "fatal error" message). I will be checking to see whether anyone answers your question!

Incidentally - how do you install GRUB on a floppy? Do you need to format the floppy in any special way?[/QUOTE]
 OK.  I solved my problem.  I had tried to be TOO clever, by setting up separate partitions for /, for /boot, and for /home.  I had read somewhere that this was a good idea; I also wanted to be able to share files between the Linux and WinXP OS's (with a shared /home partition).

BUT...  I reinstalled Ubuntu with a single partition for /.  And it installed.  Without a hitch.  No GRUB problems.  And, I get a GRUB menu to choose between the two OS's, just like it should !!  :-)  

But how do I access other partitions?  I still have the fat32 partition I made earlier for /home (I just told the Installer not to use it for anything).  Can I save files onto that partition?  Read files from there?  I don't see in Ubuntu how one mounts other partitions into the file system.  Does anyone have any suggestions??


As far as sf-andrew, to install GRUB on the floppy:

1) format a floppy as "bootable" using Windows.
2) follow directions found at: [http://www.ubuntulinux.org/wiki/HowToMakeAGRUBBootFloppy](http://www.ubuntulinux.org/wiki/HowToMakeAGRUBBootFloppy)

You need some kind of working Linux OS to do step #2; like a live CD or another machine that is up and running with Linux.  I used a live CD of Knoppix.

Good luck,
Ameet.

---

