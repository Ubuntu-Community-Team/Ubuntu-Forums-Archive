---
title: "UEFI/EFI Ubuntu Install can't find my other hard drives"
date: 2017-08-19
forum: Installation &amp; Upgrades
---

### Post by maxcr1 on 2017-08-19
When I go to install my UEFI Ubuntu Install USB alongside Windows 10 on  my UFEI locked computer, I run the install and get the "not enough  space" error, which is spawned from the USB install not being able to  find the other hard drives on my computer.  

To make my UEFI Ubuntu Install, I formatted the USB stick to Fat32, and then installed the ISO using Rufus. 

Other Information: 
All SSDs and other drives are on UEFI.
Computer is UEFI Locked (Meaning BIOS prevents me from changing Boot Mode)

Things I've tried:
Other USB Sticks
Other versions of Ubuntu
Making a FAT32 Partition on my SSD (to see if it could find that)

Am I doing something wrong?  
Any help is appreciated.

---

### Post by oldfred on 2017-08-19
Microsoft requires vendors to let users unlock or turn off UEFI Secure Boot. Only a few small netbook type systems that were UEFI 32 bit were locked to Windows only.
Some require you to add a supervisory password in UEFI to unlock other features.

What brand/model system? And what video card/chip?

UEFI installs in multiple drive systems need to be done using something Else. And best to partition in advance with gpt and include an ESP for UEFI boot. And perhaps a bios_grub for BIOS boot. I add both to all new drives & larger flash drives.

Grub only installs to an ESP - efi system partition on drive seen as sda. Best to also have drives installed in SATA port order SATA0, SATA1, etc with no skips of a port or DVD in between actual drives.

Post this:
sudo parted -l

And review link in my signature. And:
[https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration](https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration)

---

### Post by maxcr1 on 2017-08-20
> **oldfred said:**
> Microsoft requires vendors to let users unlock or turn off UEFI Secure Boot. Only a few small netbook type systems that were UEFI 32 bit were locked to Windows only.
Some require you to add a supervisory password in UEFI to unlock other features.

What brand/model system? And what video card/chip?

UEFI installs in multiple drive systems need to be done using something Else. And best to partition in advance with gpt and include an ESP for UEFI boot. And perhaps a bios_grub for BIOS boot. I add both to all new drives & larger flash drives.

Grub only installs to an ESP - efi system partition on drive seen as sda. Best to also have drives installed in SATA port order SATA0, SATA1, etc with no skips of a port or DVD in between actual drives.

Post this:
sudo parted -l

And review link in my signature. And:
[https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration](https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration)

Very sorry for not mentioning this in my original post; I have a Lenovo Flex 5, a laptop locked on UEFI.  The Ubuntu install can only see the USB drive that the ISO is mounted on, and cannot see the other drives on my computer.  I've installed Ubuntu before on other computers, and never seen this issue.  Here is a pasted parted -l.

```
Model: Sony Storage Media (scsi)
Disk /dev/sda: 2006MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2006MB  2005MB  primary  fat32        boot, lba


```

edit: grammar.  Sorry :)

---

### Post by maxcr1 on 2017-08-20
I have fixed the issue by updating my BIOS, which added the option to switch to AHCI.

---

### Post by kurt18947 on 2017-08-20
Article that talks about Secure Boot, UEFI & Microsoft/Windows:

[https://www.howtogeek.com/116569/htg-explains-how-windows-8s-secure-boot-feature-works-what-it-means-for-linux/](https://www.howtogeek.com/116569/htg-explains-how-windows-8s-secure-boot-feature-works-what-it-means-for-linux/)

Relevant part:[INDENT]For Windows 8 PCs, manufacturers had to give you a way to turn Secure  Boot off. Microsoft required PC manufacturers to put a Secure Boot kill  switch in users’ hands.

 For Windows 10 PCs, this is no longer mandatory. PC manufacturers can  choose to enable Secure Boot and not give users a way to turn it off.  However, we’re not actually aware of any PC manufacturers that do this.
 Similarly, while PC manufacturers have to include Microsoft’s main  “Microsoft Windows Production PCA” key so Windows can boot, they don’t  have to include the “Microsoft Corporation UEFI CA” key. This second key  is only recommended. It’s the second, optional key that Microsoft uses  to sign Linux boot loaders. [Ubuntu’s documentation]("https://wiki.ubuntu.com/SecurityTeam/SecureBoot") explains this.
 In other words, not all PCs will necessarily boot signed Linux  distributions with Secure Boot turned on. Again, in practice, we haven’t  seen any PCs that did this. Perhaps no PC manufacturer wants to make  the only line of laptops you can’t install Linux on.
 For now, at least, mainstream Windows PCs should allow you to disable  Secure Boot if you like, and they should boot Linux distributions that  have been signed by Microsoft even if you don’t disable Secure Boot.[/INDENT]

Another potential hurdle to have to jump over?

---

