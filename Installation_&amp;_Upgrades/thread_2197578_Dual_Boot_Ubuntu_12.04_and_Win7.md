---
title: "Dual Boot Ubuntu 12.04 and Win7"
date: 2014-01-04
forum: Installation &amp; Upgrades
---

### Post by gerwalt on 2014-01-04
Hi everyone,

as I messed up my main harddrive ([http://ubuntuforums.org/showthread.php?t=2197301](http://ubuntuforums.org/showthread.php?t=2197301)) and am currently trying to recover it with some help, I'm looking into setting up my system completely from scratch.

The old system was a Win7/Ubuntu 13.04 Dual boot, both systems on a SSD with 128GB using a GPT and EFI.

Most of the time I'm using Linux, Windows is only necessary for gaming and tax/office software, although I could use VMs for the latter.

I got a spare SSD with 128GB.

So here is my plan:
As the old SSD is still in use for recovering purposes I planned on installing Ubuntu first (because I need it) and install Windows later on the old SSD (when everything is recovered).

The new SSD will be completely used for Ubuntu 12.04:
- MBR
- BIOS (no EFI anymore, MB supports both)
- ~17GB for swap (I have 16GB RAM)
- 10-20GB for /
- rest /home

And when the old data is recovered the second SSD will be used for Windows:
- MBR
- BIOS
- everything for system (moslty used for games)

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Any thoughts about it and things that dont sound so great? Especially on partitions sizes and BIOS/MBR settings?

Maybe some links for useful information, I dont want to mess it up again for some stupid reason (and because I'm sometimes a bit unpatient).

---

### Post by Bucky Ball on 2014-01-04
Two things I notice at a glance:

1/ If you want to share data between Ubuntu and Windows you want an NTFS partition;
2/ I have noticed on the forums people mentioning to avoid gaming in VMs.

I'm wondering what the BIOS you have is in each disk. Are they partitions? With no EFI, wondering why they need to be there, but that could be my ignorance. I didn't think Win7 required a partition for boot if not using EFI? I'm running Win7 and it doesn't use one. 

Anyhow, the BIOS is something else, so maybe you are using the wrong terminology there. Perhaps you mean something like an efi partition for Win7 and a /boot/efi partition for Ubuntu. Perhaps you could clarify.

It is generally easier to install Windows first but shouldn't take much to get things booting correctly if you install it second so that is no real concern. I did it awhile ago with XP. Might be different with Win7, but don't think so.

---

### Post by gerwalt on 2014-01-04
> **Bucky Ball said:**
> 1/ If you want to share data between Ubuntu and Windows you want an NTFS partition;
2/ I have noticed on the forums people mentioning to avoid gaming in VMs.

to 1: I have a third separate hdd with 2 partitions (ntfs and ext) for each of them. If I have to share data, I use an external drive
to 2: Yes, I wouldnt do that either. I ment I would only use the VM for office- and tax-software.

> **Bucky Ball said:**
> 
I'm wondering what the BIOS you have is in each disk. Are they partitions? With no EFI, wondering why they need to be there, but that could be my ignorance. I didn't think Win7 required a partition for boot if not using EFI? I'm running Win7 and it doesn't use one. 

Anyhow, the BIOS is something else, so maybe you are using the wrong terminology there. Perhaps you mean something like an efi partition for Win7 and a /boot/efi partition for Ubuntu. Perhaps you could clarify.

Yes, I meant BIOS. UEFI is the successor of BIOS. So just the way the system boots. But as we talk about it, I think I will stick to UEFI (or EFI) instead of BIOS. But I'm not sure if I will still use GPT or step back to MBR.

> **Bucky Ball said:**
>  It is generally easier to install Windows first but shouldn't take much to get things booting correctly if you install it second so that is no real concern. I did it awhile ago with XP. Might be different with Win7, but don't think so.

Yes I know, but the current situation doesnt give me any opportunity.

---

### Post by gerwalt on 2014-01-04
Another thing I didnt mention:

Both OS will be 64bit. Dont know if Windows 7 64bit requires GPT or UEFI, but as far as I know it doesnt

---

### Post by Bucky Ball on 2014-01-04
Don't think so. As I say, I'm running Ubuntu and Win7 and have no GPT or EFI or BIOS partitions. Their requirement could be related to newer hardware than mine, though, and therefore my ignorance on why they are needed on your setup. 

If you set the BIOS to boot in legacy are they not required? Dunno. :-k

---

### Post by gerwalt on 2014-01-04
I think you misunderstood me. I just wrote that I wanted to use BIOS, to make clear that I'm not going to use EFI. BIOS does not need a seperate partition as EFI does.

---

### Post by Bucky Ball on 2014-01-04
Ah, sorry. Just confused me how it was in the outline of each SSD. All good. ;)

---

