---
title: "Cannot boot installer on UEFI [ASUS Eee pc 1215B]"
date: 2011-12-27
forum: Installation &amp; Upgrades
---

### Post by Veovis Muad'dib on 2011-12-27
I've tried several tips from [this thread]("http://ubuntuforums.org/showthread.php?t=1749630"), to no avail.

I have downloaded the liveCD installer, x86 & x86_64, checksums are fine.  In tools that allow downloading the iso I have downloaded it with the tool as well as trying my downloaded copy.

I have used the Universal USB Installer, UNetBootIn, and a tool called Win32DiskImager to write the image to a USB drive.  None reported any errors.  Each tool and each version of the installer has the same problems:

When booting, I have the option in BIOS to launch```
myUSBDrive
UEFI:myUSBDrive
```The former comes back with a "Please insert bootable media.  Press any key to continue" error.  The latter boots into a bootloader, which gives me these options:```
Try Ubuntu without installing
Install Ubuntu
Test disk for errors
```Any option selected causes the screen to blank out and the USB drive's LED to blink the same way it does when ejected, then about ten seconds later the computer powers down.

---

### Post by oldfred on 2011-12-27
What version of Ubuntu? The newest has some of the grub UEFI fixes, but there still seem to be issues. Most have reported that if they partition in advance it works. But grub2 had a bug where it deletes & then reformats the Windows efi partition, so you have to back it up first before doing an install.

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)
Recompiling GRUB not required with newest versions of grub.
Creating efi partition & folders in advance works.

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

[SOLVED] UEFI Boot Problems 
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)

---

### Post by Veovis Muad'dib on 2011-12-27
> **oldfred said:**
> What version of Ubuntu? The newest has some of the grub UEFI fixes, but there still seem to be issues. Most have reported that if they partition in advance it works. But grub2 had a bug where it deletes & then reformats the Windows efi partition, so you have to back it up first before doing an install. I'm using 11.10 in the hopes that I'd get the 3.0 kernel in order to support Fusion better.  Partitioned already, in fact I was working on getting Arch on this guy when my mother's computer broke.  She needs a new one, won't use Windows anymore since I put her on Ubuntu, so I figured I'd get this up for her.  Not going to dualboot, and it's been wiped since Windows was last on it.

> **oldfred said:**
> [https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell)
Recompiling GRUB not required with newest versions of grub.
Creating efi partition & folders in advance works.
Didn't explain well enough in my OP.  The installer isn't booting.  Though I'll keep this link around for afterward, I know how much trouble I had with UEFI shell when trying to use the Arch documentation.  :P  (Didn't realize that to get to fs0 after a `mount fs0` that I would have to type `fs0:` as though it were a DOS shell.)

> **oldfred said:**
> Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)
Great resource, now if I forget where it is I can check back here.

> **oldfred said:**
> [SOLVED] UEFI Boot Problems 
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)
I'll certainly refer here if I have problems at that point.

Thanks.

---

### Post by oldfred on 2011-12-27
Are you really in UEFI mode or BIOS mode?

I do not know UEFI well but saved those links as I hope to get new computer with UEFI in 2012. I am using gpt with MBR(msdos) and that works but that still is not a ASUS Eee.

---

### Post by Veovis Muad'dib on 2011-12-27
I can't seem to boot anything in BIOS, I'm not entirely sure that it's an option on the 1215B.

I love this laptop, so many nice features.  But booting Linux at all seems to be a pain.  I had better luck doing it on a Mac.  :P

UEFI fixes some issues.  It allows for booting from larger drives, and it is coded in x64 if I understand correctly, which is nice, I'm of the opinion that we should have phased out 32 bit a long time ago, even on machines that don't directly benefit from the change.

What I don't like about UEFI is that it is so amazingly complicated for a replacement to a simple, small system.  I'll be less opposed when Linux is better able to boot from it, and I'm sure that even at 19 I sound like an old fogey here, but there seems to be no advantage from the perspective of an end user other than larger bootable drives.

---

### Post by Veovis Muad'dib on 2011-12-28
Bump for great justice.

---

### Post by oldfred on 2011-12-28
Another UEFI thread where he got it working. Afraid I do not know enough to help any more.

[http://ubuntuforums.org/showthread.php?t=1890048](http://ubuntuforums.org/showthread.php?t=1890048)

---

### Post by Veovis Muad'dib on 2011-12-29
Thank you for the links, I'm reading through them all.  Haven't found what I'm looking for yet, but if this last link does it, I'll report back.

---

### Post by yelo3 on 2011-12-30
I'm also interested in this thread, I have the same laptop and I'm facing the same problem

---

### Post by Veovis Muad'dib on 2011-12-31
No success with any links posted here, nor any research I've done myself.  I was going to install Windows, but I appear to not be able to boot that installer anymore either.  Do you have that issue?

---

### Post by oldfred on 2011-12-31
Some have had to do a cold boot to get system to work. Windows will only install to a primary NTFS partition with BIOS. If UEFI it needs both a efi partition and its boot partition first.

Microsoft reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by yelo3 on 2012-01-01
Actually I didn't remove windows

---

### Post by oldfred on 2012-01-01
@ yelo3 
Please start a new thread so we do not get confused with Veovis Muad'dib issues & solution.

Please post the bootinfoscript. There is a new testing version that also searches for and finds efi files. Post the results.txt it creates. It may be long so put it in code tags by highlighting & clicking on the # in the edit panel  as you post.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'

chmod a+x bootinfoscript

sudo bash bootinfoscript
```

---

### Post by Veovis Muad'dib on 2012-01-01
> **oldfred said:**
> Please post the bootinfoscript. There is a new testing version that also searches for and finds efi files. Post the results.txt it creates. It may be long so put it in code tags by highlighting & clicking on the # in the edit panel  as you post.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'

chmod a+x bootinfoscript

sudo bash bootinfoscript
```

No way to do that.  No *nix system present or bootable, including live media.

---

### Post by oldfred on 2012-01-02
@Veovis Muad'dib
Do you by any chance have an Intel Motherboard? They seem to have that issue if no boot flag is present even though in UEFI the old standard BIOS boot flag is not used. In UEFI you have to have an efi partition with gpt code ef00 which is a "boot flag" in gpt and it has to be the first partition. 

Some have been able to boot in BIOS mode and install. Then install the efi boot loader to the efi partition and in effect convert to UEFI boot. You do have to create partitions in advance on the Hard Drive so the efi partition exists as it must be first.

---

### Post by Veovis Muad'dib on 2012-01-02
Can't do anything to the partitions without booting something.  Which I can't.  I could pull out the hard disk and install on another computer, but that voids the warranty and is a lot of work.

Then again, laptop has been out of commission for over two months, might as well.

---

