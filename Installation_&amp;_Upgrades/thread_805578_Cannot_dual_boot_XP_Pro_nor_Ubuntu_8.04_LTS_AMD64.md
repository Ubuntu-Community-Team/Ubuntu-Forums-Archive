---
title: "Cannot dual boot XP Pro nor Ubuntu 8.04 LTS AMD64"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by Jabbadahut on 2008-05-24
I need some serious help here.  I have 2 hard disks, one with XP Pro that is 120 GB in size, the other for data that is only 6 GB.  I downloaded & burned Ubuntu 8.04 LTS Desktop for AMD64 processors iso file and burned it with no problems.

After booting with the LiveCD, I chose to install Ubuntu on the same hard disk where XP is installed, but I am positive that I chose the guided install where it creates a new partition that resides on disk where XP is installed, so that I can dual-boot.

However, upon rebotting the computer after install, I cannot get into GRUB, unless I use a bootable CD and bypass booting the computer with that CD.  Otherwise if I don't, I get an error stating that "NTLDR is missing", which of course is a Windows error.  If I am understanding the problem, I think what happened is the setup program overwrote the MBR for Windows.

The only way I can get into GRUB is to use my Windows XP setup disk and bypass the "press any key to boot the CD" prompt.  I then see the GRUB menu, but I can only boot Ubuntu, not Windows XP, as I get the "NTLDR is missing" error.

After booting Ubuntu, I looked at the hard disks, and sure enough, the larger hard disk is indeed split up into 2 partitions, with the one where windows is on is now 10 GB in size, the other partition where Ubuntu is taking up the rest.  So thank God the install did not overwrite the whole shmeer.  However, I can't get into Windows now, so how do I fix this without having to start from scratch?

If more information is needed, please let me know.  Thanks!

 - Jabba

---

### Post by PmDematagoda on 2008-05-24
First of all, does GRUB work properly?

---

### Post by Jabbadahut on 2008-05-24
> **PmDematagoda said:**
> First of all, does GRUB work properly?
As I said, I can only get to GRUB when a bootable CD (in this case, my Windows XP Pro setup CD) is in the system, otherwise GRUB doesn't load, and the system goes ahead with booting Windows, but I get the error "NTLDR is missing".  That means that Windows can't find that file in order to boot that OS.  Funny thing is, when I examine the partition that has Windows in Ubuntu, the NTLDR file is there.

When booting with the CD, GRUB does load and appears to be working as far as I can tell.  However, I can only boot to Ubuntu.  If I try to boot to Windows XP from GRUB, I get the same "NTLDR is missing" error.

---

### Post by PmDematagoda on 2008-05-24
Try and see if the [SuperGRUB CD]("http://supergrub.forjamari.linex.org/?section=download") would help to set things right with GRUB.

About Windows, did you try tu run the Recovery process for Windows using the Windows install CD?

---

### Post by Jabbadahut on 2008-05-24
I tried using the recovery console on the XP setup disc.  I tried the "fixmbr" command, but all that did was succeed in not allowing me to boot PERIOD, even with the CD.  In other words, I couldn't boot Ubuntu either.  Tried the "fixboot" command as well, but that didn't do anything.  I was very upset at my foolishness.

So, having no other way to access anything on the hard disk, I went ahead and started from scratch.  Now all I have is Windows XP Pro installed.  I wish I didn't do what I did, but oh well, you live and learn.  Thanks anyways for your assistance. :)

- Jabba

---

