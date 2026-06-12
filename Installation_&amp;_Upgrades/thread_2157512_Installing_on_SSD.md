---
title: "Installing on SSD"
date: 2013-06-25
forum: Installation &amp; Upgrades
---

### Post by bower4311 on 2013-06-25
I have a 64GB Crucial SSD on the way. I am running 13.04, I've recently run 12.04 and 12.10 and for my luck 13.04 has been the most stable for me. Well, I'm ditching my HDD for an SSD. I have a 3T external for movies and music. I don't really do anything extraordinary on Ubuntu. I just like the quickness and stability. I am considering dual booting with XP, I am stuck on Word 2010 and can't break it, I have one year left of college then I will never need it for what I do now. I may also download the occasional program only for XP. Will I run into problems dual booting on the SSD? Or just search dual boot XP and Ubuntu and it shouldn't be a big deal? Any other quirks with the SSD?

---

### Post by oldfred on 2013-06-25
SSD & XP do not go together well as I found out. But then I was somewhat looking for a way to convince myself to stop booting XP anyway.

With the SSD you need BIOS set for AHCI and XP does not have those drivers. If a new install of XP it may be possible to install them. I only looked for ways after the fact and it was too much for a system I really did nto want anyway.

Also your 3TB drive will not be seen by XP, it has no drivers for gpt partitioned drives. I dual booted XP on a MBR drive and my older 160GB hard drive which I converted to gpt to learn about gpt. I also use gpt on my SSD.

---

### Post by bower4311 on 2013-06-25
> **oldfred said:**
> SSD & XP do not go together well as I found out. But then I was somewhat looking for a way to convince myself to stop booting XP anyway.

With the SSD you need BIOS set for AHCI and XP does not have those drivers. If a new install of XP it may be possible to install them. I only looked for ways after the fact and it was too much for a system I really did nto want anyway.

Also your 3TB drive will not be seen by XP, it has no drivers for gpt partitioned drives. I dual booted XP on a MBR drive and my older 160GB hard drive which I converted to gpt to learn about gpt. I also use gpt on my SSD.


Then no XP it is. I'm surrounded by enough Windows computers...unfortunately. Meaning I have to always fix them. I'll just be installing 13.04 and I'll be happy.

---

### Post by oldfred on 2013-06-25
How new is system? Does it have both UEFI & BIOS?

Since you have gpt on your 3TB drive, I might suggest gpt on your SSD. I was planning on a new system soon after my then new SSD so I use gpt and left space for an efi partition, but had to add the bios_grub partition to boot with my current BIOS. Still have not build new system, but hope to soon.

```
fred@fred-Precise:~$ sudo parted /dev/sde unit s print
Model: ATA SSD G2 series 64 (scsi)
Disk /dev/sde: 117231408s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End         Size       File system  Name     Flags
 1      2048s      616447s     614400s    fat32                 boot
 2      616448s    618495s     2048s                            bios_grub
 3      618496s    58925055s   58306560s  ext4         Precise
 4      58925056s  117229743s  58304688s  ext4         Quantal

```

---

### Post by bower4311 on 2013-06-26
> **oldfred said:**
> How new is system? Does it have both UEFI & BIOS?

Since you have gpt on your 3TB drive, I might suggest gpt on your SSD. I was planning on a new system soon after my then new SSD so I use gpt and left space for an efi partition, but had to add the bios_grub partition to boot with my current BIOS. Still have not build new system, but hope to soon.

```
fred@fred-Precise:~$ sudo parted /dev/sde unit s print
Model: ATA SSD G2 series 64 (scsi)
Disk /dev/sde: 117231408s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End         Size       File system  Name     Flags
 1      2048s      616447s     614400s    fat32                 boot
 2      616448s    618495s     2048s                            bios_grub
 3      618496s    58925055s   58306560s  ext4         Precise
 4      58925056s  117229743s  58304688s  ext4         Quantal

```


I don't know much about computers compared to most, I just like Ubuntu's reliability and simplicity.

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2406888](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2406888)

That is my motherboard, it has UEFI.

---

### Post by oldfred on 2013-06-26
How you boot install media is how it installs. So if you boot Ubuntu flash drive installer from UEFI in UEFI mode it installs in UEFI mode. If you turn off UEFI and turn on CSM/Legacy/BIOS and boot flash drive in BIOS mode it installs in BIOS mode. 
You can also tell as in UEFI the installer gives you a grub menu, where BIOS has the accessibility icons (tiny keyboard & person at bottom of screen) for a few seconds at startup.

If installing UEFI mode, see link in my signature.

---

### Post by TNFrank on 2013-06-26
Not to change the subject but, couldn't you use something in the LibreOffice suite to do your Word stuff with?  :confused:

---

