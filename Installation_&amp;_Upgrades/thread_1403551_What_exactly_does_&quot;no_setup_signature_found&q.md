---
title: "What exactly does &quot;no setup signature found&quot; mean?"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by hbquikcomjamesl on 2010-02-10
See this thread for background: [http://ubuntuforums.org/showthread.php?t=1402323](http://ubuntuforums.org/showthread.php?t=1402323)

I apparently have whatever default boot menu the installer gave me, but it kicks out to a GRUB command prompt. I can successfully do a manual IPL of DOS from that command line, but attempting to do the same for my freshly-installed Ubuntu 8.04LTS gets me a "no setup signature found" if I try to use the kernel on the boot partition, and a "file not found" message if I try to use the link to it that's on the Linux partition.

---

### Post by hbquikcomjamesl on 2010-02-10
Curiouser and curiouser: what little I can find suggests it means a bad kernel file. And yet the live CD from which it was installed works just fine.

---

### Post by sven_nestle on 2011-05-19
well #1 you COULD read the kernel code and see pup ! :)  but this time you need a little extra hint.  but you DO NOT need to recompile the kernel continually !!  may not be the problem at all !!

I have the same problem today with a new kernel.  BUT!  I also have it with the old one but ONLY one location of it.  HMMM.  Same EXCACT vmlinuz file one in / and one in /boot.  diff(1) sees no difference.

Problem?  How the file is stored on the disk.

The OLD kernel boot HOWTOs (floppy) told you flat out: use dd(1) to place the Linux Kernel on the floppy and that a simple cp(1) would NOT work.

Today, while we *usually* have it far easier but keep in mind the root of the problem is still there.

Why is because how it is stored on disk.  You filesystem (there are so many) can piece out a file here and there (wherever there is room in the fs table listings).  Problem:  Boot loaders can't always figure that out I think.

SOLUTION #2: make sure GRUB is the newest version, see if that helps

SOLUTION #1: it's much easier for Boot Loader (any) and Kernel if the file is single and linear on whichever disk it is on.  Do what you can - but try just cp(1) and list several (/vmlinuz1, /vmlinuz2, etc) in your boot loader list and one will work I bet :)

see also: [http://www.ibiblio.org/pub/Linux/docs/HOWTO/Linux-i386-Boot-Code-HOWTO](http://www.ibiblio.org/pub/Linux/docs/HOWTO/Linux-i386-Boot-Code-HOWTO)

---

### Post by sven_nestle on 2011-05-19
YIKES I FORGOT TO SAY !!

You might have a very large hard disk with a BIOS that cannot read beyond some range.  For example my BIOS cannot read past ? 8 gig. on my disk.  This means that ALL of my kernel MUST be in a disk partition or place which is linearly < 8 gigabyes within the real start of the disk.  period no way around it.

BIOS code writers they have done that from MFM/RLL to Ultra IDE.  Why don't they think ahead for once in 3 decades?  (I prefer scsi/firewire to ide/usb - scsi is much less a hack technology as ide is).

---

