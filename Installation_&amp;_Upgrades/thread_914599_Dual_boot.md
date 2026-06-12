---
title: "Dual boot ?"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by ManyBeers on 2008-09-09
I am about to install Ubuntu 8.04 on my Vaio laptop that currently runs WindowsXP SP3 in a dual boot arrangement. Windows is the only partition om my 20 gig drive at this point which leaves me about 12.5 gigs for Ubuntu and a small shared drive
which i intend to partition with the Ubuntu install. 

   Here's the deal, I do not want to use Grub as my bootloader but instead use Windows ntldr so I will install Grub in Ubuntu's partition and not the MBR. However if I am not mistaken when Ubuntu is installed it sets itself as the active partition which would make my Windows unbootable(because Windows
bootloader the ONLY one in the MBR at this time is now pointing to an INACTIVE partition). Is this correct? If so can this be avoided during
Ubuntu's install?

---

### Post by manishtech on 2008-09-09
> I do not want to use Grub as my bootloader but instead use Windows ntldr so I will install Grub in Ubuntu's partition and not the MBR. 
I dont recomment this since Windows Bootloader cant chainload. Additionally it cant boot linux, only made for booting windows. Chain loading means it cant even call another bootloader.
I suggest you to use GRUB on your MBR, your way of installation is quite unusual as far as I know. I havnt heard of ntldr booting linux.

> However if I am not mistaken when Ubuntu is installed it sets itself as the active partition which would make my Windows unbootable. Is this correct?
Not at all! Who said this that installing ubuntu makes windows unbootable? I triple boot and never ever face any problems. Go ahead, nothing will happen. Just while intalling take care when you select partitions.

---

### Post by manishtech on 2008-09-09
>  if I am not mistaken when Ubuntu is installed it sets itself as the active partition
I hope you know the meaning of active partition! :)

---

### Post by ManyBeers on 2008-09-09
> **manishtech said:**
> I dont recomment this since Windows Bootloader cant chainload. Additionally it cant boot linux, only made for booting windows. Chain loading means it cant even call another bootloader.
I suggest you to use GRUB on your MBR, your way of installation is quite unusual as far as I know. I havnt heard of ntldr booting linux.


Not at all! Who said this that installing ubuntu makes windows unbootable? I triple boot and never ever face any problems. Go ahead, nothing will happen. Just while intalling take care when you select partitions.

Is that a fact? Maybe you shpould read [http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=1]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=1")
The reason most people don't do it this way is because it is more difficult.

---

### Post by ManyBeers on 2008-09-09
Not at all! Who said this that installing ubuntu makes windows unbootable? I triple boot and never ever face any problems. Go ahead, nothing will happen. Just while intalling take care when you select partitions.[/QUOTE]

If Grub is not installed in the MBR but in the Ubuntu partition instead that means Windows's bootloader is still in the MBR, and still pointing to Windows... Right? Ok. So, if after installing Ubuntu it makes itself the active partition on the drive, that would make the Windows partition inactive... Right? OK, so we finish installing Ubuntu and reboot like it tells you to do so it can finish the install from the harddisk. Only now the Windows bootloader is looking for an active partition to boot but it cannot see one because Ubuntu has declared itself the ACTIVE partition on the drive, and since Windows bootloader does not have an Ubuntu entry on it's boot.ini file neither operating system can boot. The article in my link explains it all.

---

### Post by JMorg on 2008-09-09
The grub menu.lst is essentially windows boot.ini. It is editable and if i'm not mistaken you can completely reorder the way your partitions are ordered. I have had to remove a few unnecessary items that were being loaded by grub. He was just trying to let you know that grub is the preferred and most hassle-free way to install linux for new users.

---

### Post by ManyBeers on 2008-09-09
> **JMorg said:**
> The grub menu.lst is essentially windows boot.ini. It is editable and if i'm not mistaken you can completely reorder the way your partitions are ordered. I have had to remove a few unnecessary items that were being loaded by grub. He was just trying to let you know that grub is the preferred and most hassle-free way to install linux for new users.

Thanks for replying. I just prefer to use the Windows bootloader
     
      Are you saying you can edit Grub Before the Ubuntu install asks you to reboot so it can finish installing from the harddrive. Because if you cannot edit the file prior to the reboot then the computer will boot neither system.(If you do as suggested in the tutorial and install Grub in Ubuntu's partition and not in the MBR which is waht I intend to do.  

      By the waythis:[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=1](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=1) is the tutorial I am going by.

     Either way has risks. **** happens. Though the way it is done via the tutorial is probably a little riskier because apparently you will end up with an unbootable system temporarily. And I am at little apprehensive about using the SystenRescueCD as mentioned in the tutorial because it is fairly complex looking but it is neccessary i guess. Basically if at all possible I would like to avoid having to use the System Rescue cd to reflag the Windows partition as active and just 
leave it active all the time.

If you read that tutorial I posted it explains exactly what happens and what steps are neccessary to get the dual-boot working with Windows' bootloader.

---

