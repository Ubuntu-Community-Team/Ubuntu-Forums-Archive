---
title: "Help installing on a dual-boot with lots of DOS volumes"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by hbquikcomjamesl on 2010-02-09
I have a DOS/Linux dual-boot system. After recently replacing the original motherboard (an Elitegroup P6VEM3, of all things!) with a salvaged Dell D300 motherboard, I'm preparing to replace the Red Hat 8 currently installed with a Ubuntu live CD that I've had for some time (but that wouldn't work at all on the old motherboard, for some reason)

I have a question about the "partitioner" stage of the installer: I don't know what to do with my 5 DOS volumes.

My hard drive is partitioned as follows (from the partitioner's report when I select manual mode; annotations in parentheses):

[FONT=Courier New] /dev/sda
  /dev/sda1   fat16     57MB   33MB       (C:, "DOS")
  /dev/sda5   fat16    106MB   33MB       (D:, "STUFF")
  /dev/sda6   fat16    633MB  121MB       (E:, "APPLICATION")
  /dev/sda7   fat16    633MB   41MB       (F:, "TOOLS")
  /dev/sda8   fat16    419MB   33MB       (G:, "GAMES")
  /dev/sda9   ext3     205MB   15MB       (/boot)
  /dev/sda3   ext3  154224MB 4600MB       (/)
  /dev/sda4   swap    3758MB    0MB[/FONT]

[FONT=Verdana]Running the live CD, all 5 DOS volumes are mountable by name, under the 
"places/removable media" menu, as are both my 1.44M and 360k (yes, 360k) floppy drives.

I'm not sure if saw my 250M Zip drive under the live CD; it reports as "hdb4" under Red Hat 8.

The Partitioner only offers "DOS" and "WINDOWS" as mountpoints for FAT16 volumes;
I have, as you can see, 5 DOS volumes and no WinDoze.

So what do I tell the partitioner about the other DOS volumes?

And do I keep the existing GRUB, or install a new one, and if the latter, how do I tell it that
sda1 is the bootable DOS volume?

Ideally, I'd like Linux to mount C and E as read-only, since one is my DOS, and the other
is where my "family jewels" DOS apps and data live.

Under RH8, I was able (despite the fact that it hasn't been talking to the mouse since
I changed motherboards) to inspect the mtab and fstab files; here is what they report (no
mountpoints for the DOS volumes; I'd had to reinstall RH8 after replacing the hard drive,
and never got around to adding mountpoints for them!):

[/FONT]mtab in RH8:

[FONT=Courier New] /dev/hda3 / ext3 rw 0 0
none /proc proc rw 0 0
usbdevfs /proc/bus/usb usbdevfs rw 0 0
/dev/hda9 /boot ext3 rw 0 0
none /dev/pts devpts rw,gid=5,mode=620 0 0
none /dev/shm tmpfs rw 0 0
[/FONT] 
fstab in RH8:

[FONT=Courier New] LABEL=/ / ext3 defaults 1 1
LABEL=/boot /boot ext3 defaults 1 2
none /dev/pts devpts gid=5,mode=620 0 0
none /proc proc defaults 0 0
none /dev/shm tmmpfs defaults 0 0
/dev/hda4 swap swap defaults 0 0
/dev/hdb4 /mnt/zip auto noauto,owner,kudzu 0 0
/dev/fd0 /mnt/floppy auto noauto,owner,kudzu 0 0
/dev/fd1 /mnt/floppy1 auto noauto,owner,kudzu 0 0
/dev/cdrom /mnt/cdrom iso9660 noauto,owner,kudzu 0 0
[/FONT] 
--
James H. H. Lampert

---

### Post by dstew on 2010-02-09
If you are installing Ubuntu 9.10, I would not designate mount points for the DOS partitions during the installation. You can do that later.

If you want to designate mount points, just give each one a different name, such as /mount/DOS, /mount/STUFF etc. Or, you can do it after you install, and edit the fstab to mount what you want at boot time.

I assume you will be putting Ubuntu into the /dev/sda9 and /dev/sda3 partitions and using /dev/sda4 as swap space. During the partitioning step, you would designate the mount points /boot and / for these two, as they were in Red Hat, but then have the partitioner format them as ext3. It should install OK.

The grub 2 boot loader should detect the Ubuntu and DOS installations and create menu items for them. If it doesn't get the DOS system right, you can create a menu entry for it later by editing the grub configuration files.

---

### Post by hbquikcomjamesl on 2010-02-09
Hmm. There is no obvious way in the Partitioner to specify a user-defined mountpoint for a FAT-16 volume, so do I just leave them "do not use," and add the mountpoints and fstab entries later? Or is there a secret to defining new mountpoints in the Partitioner?

Incidentally, I finally checked the version: according to the envelope, it's 8.04 LTS.

---

### Post by dstew on 2010-02-09
I think if the partitioner is not offering mount points, then just leave them as "do not use" and add the mountpoints and fstab entries later.

---

### Post by hbquikcomjamesl on 2010-02-09
[FONT="Verdana"]I went ahead and installed. Everything shows success, except for one problem:

Instead of booting to a GRUB boot menu, it boots to a GRUB [FONT="Verdana"]command prompt.

Now what?

I was able to get DOS to successfully IPL, with:[/FONT]
[FONT="Courier New"]
    rootnoverify (hd0,0)
    chainloader +1
    makeactive
    boot[/FONT]

But how do I (1) get my freshly-installed Ubuntu (on the partition that's /sda3 to Linux, and presumably hd0,2 to GRUB) to IPL, and (2) build the GRUB menu?

I picked this snippet:[/FONT][FONT="Courier New"]

    root (hd0,0)
    kernel /vmlinuz-i686-up-4GB root=/dev/hda9
    boot

[/FONT][FONT="Verdana"]up from another web site, and I know I need to plug "/dev/sda3" into the root parameter, but what about the kernel pathname?[/FONT]

---

### Post by hbquikcomjamesl on 2010-02-09
I found a kernel, "vmlinuz-2.6.24-16-generic" in the sda9 (hd0,8) root.

But
[INDENT]kernel /vmlinuz-2.6.24-16-generic root=/dev/sda3
   boot
[/INDENT] gets me a "no setup signature found" message, a long beep, and an apparent system halt.

I also found a link in the sda3 (hd0,2) root, "/vmlinuz," that would point to the kernel, if Linux were actually running, but
[INDENT]    root (hd0,2)
   kernel /vmlinuz root=/dev/sda3
[/INDENT] gets me "Error 15: File not found."

---

### Post by hbquikcomjamesl on 2010-02-10
At any rate, given that there *is* a boot menu file in there, albeit one that seems configured to avoid showing itself, and one that *doesn't* include DOS, and also given the error messages attempting to manually IPL Linux from the GRUB command line, I begin to understand why it falls out *to* the GRUB command line.

But what exactly does "no setup signature found" mean?

Have I somehow wandered into a situation in which I was expecting Ubuntu, like Red Hat, to want boot and root as separate partitions, but the OS wants them in the same partition?

Would copying the kernel into the root help?

---

