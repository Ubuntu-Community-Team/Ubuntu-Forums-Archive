---
title: "GRUB2 does not install properly in Ubuntu 10.10 ?"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by zipeppe on 2010-10-16
Dear ubuntuser

on a IBM Server Intellistation ZPro Ubuntu 10.10 (i386 desktop or alternate) fails during the installation of the loader.

The BIOS sees two IDE drivers where Windows 7 is installed, and a PCI card with a SATA controller has been installed to have four additional sata DISKs.

During the boot the HDD are all recognized as /dev/sdX devices, with /dev/sda and /deb/sdb for IDE, /dev/sdc ... for SATA.


The installation proceeds with no problem on the first SATA drive (dev/sdc with ext4 partitions and LVM), even the grub is installed without error messages on the MBR of /dev/sda to have a choice between different OS.

Unfortunately when the system reboots it hangs immediately with the following error:

[B][INDENT]error: no such device:  e12e23e33-2983-1232-....
grub rescue>[/INDENT][/B]

Does anyone know if there is a bug on GRUB delivered with Ubuntu 10.10?

I tried many time to rescue the system by using the CD by reinstalling the GRUB in the secondary IDE disk, but it does not work.

When I install back the Seven Loader in /dev/sda, Windows 7 start with no problem, so to me it looks a problem with grub.

Any idea?

---

### Post by psusi on 2010-10-16
It sounds like your bios does not recognize the sata drives.  Check for a jumper to enable the bios extension rom on the sata card, or you can install with a small /boot partition on one of the IDE drives.

---

### Post by zipeppe on 2010-10-16
> **psusi said:**
> It sounds like your bios does not recognize the sata drives.  Check for a jumper to enable the bios extension rom on the sata card, or you can install with a small /boot partition on one of the IDE drives.

Thank you for the answer.
I can try to reserve a small /boot partition into one of the IDE drives.  But this cannot explain to me why the grub hangs with the reported error.  I mean, if the loader is unable to point a certain partition it should raise a different kind of error. Is not it?

---

### Post by zipeppe on 2010-10-16
what about a bug?

---

### Post by psusi on 2010-10-16
No, the error is saying that it can't find the partition you have Ubuntu installed on.

At the rescue prompt you can try running ls and see what drives are detected.

---

### Post by zipeppe on 2010-10-16
> **psusi said:**
> No, the error is saying that it can't find the partition you have Ubuntu installed on.

At the rescue prompt you can try running ls and see what drives are detected.

Here's the output:

(hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (hd1) (hd1,msdos4) (hd1,msdos3) (hd1,msdos2) (hd1,msdos1)

they are IDE partitions...

---

### Post by oldfred on 2010-10-16
See DRS305's post:

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

Please post this:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by psusi on 2010-10-16
> **zipeppe said:**
> Here's the output:

(hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (hd1) (hd1,msdos4) (hd1,msdos3) (hd1,msdos2) (hd1,msdos1)

they are IDE partitions...

Yep, your bios does not see the sata disks then.  The sata card should have a bios extension on it to make this happen, so it is either broken, or disabled.

---

### Post by oldfred on 2010-10-16
Have you set BIOS for IDE compatibility mode?

---

### Post by psusi on 2010-10-16
> **oldfred said:**
> Have you set BIOS for IDE compatibility mode?

It sounds like the bios does not know about sata at all, so there is no such setting.  The sata is on an add in card, not built in.

---

### Post by VMC on 2010-10-16
I'd be curious to see what ubuntu see's with that SATA pci card pluged in. Type the following from a terminal:

```
lspci
```

---

