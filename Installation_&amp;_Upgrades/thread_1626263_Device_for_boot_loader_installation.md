---
title: "Device for boot loader installation"
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by -yay- on 2010-11-20
Hi all :p

I'm trying to create a dual boot with ubuntu 10.10 on my acer laptop with windows 7.

I looked at my hard drive and I found out that it has three partitions, one called SYSTEM RESERVED, another one called PQSERVE or something like that (which is a recovery partition since acer laptops dont have a recovery cd), and the third partition is C:. 

So I shrunk my C: drive, and created a 44gb partition for ubuntu, and a 6gb swap. 

I then booted with the ubuntu cd and went into manual partitioning. I selected the 44gb partition as "/", and set the 6gb partition to swap.

The problem is at the very bottom of the partition manager, where it says "Device for boot loader installation". I get several choices, and I'm a bit unsure which one to choose.

The choices are as follows:

/dev/sda ATA WDC WD5000BEVT-2 (500,1GB)
/dev/sda1 Windows Vista (loader)
/dev/sda2 Windows 7 (loader)
/dev/sda3
/dev/sda5
/dev/sda6

My first thought was of course why do I have a vista loader? I don't even have vista!

So which one should I choose? And what happens if I choose the wrong one?

Thanks for reading;)

---

### Post by Quackers on 2010-11-20
Grub is normally installed to the mbr of the drive on which Ubuntu is being installed. ie sda in your case (note no partition number on the end).
The vista loader will be your Windows 7 loader, it does not differentiate between the 2 Windows.
Please note that installing grub to the mbr may break the Windows loader (but this is often not the case with W7) and in those circumstances a Windows Vista/7 installation disc is used to repair it.

---

### Post by ajgreeny on 2010-11-20
You should put grub on /dev/sda, the disk itself, not onto a partition.  That way grub will take over from the windows bootloader and give you the option of which OS to boot.

Don't worry about the Vista thing, that is just the way grub identifies the partition.

If you should ever need to restore the windows bootloader/MBR it can be done with the ubuntu live CD/USB, if you don't have a windows install CD.

---

### Post by mcmacker4 on 2013-03-02
And what about mac? What should I select? I will use rEFIt to select the operating system i want to use, but, anyways, i don't know where to install the bootloader and i wouldn't like to replace the mac boot loader since I don't know where my mac's boot disk is...

---

### Post by QIII on 2013-03-02
Thank you for sharing.  Everyone’s questions and answers are valuable.

If a thread has had no activity for about a year or more, it is best to start a new thread of your own. Not only will you be more likely to get a response, but things change so quickly in the software world that an old thread may cause you more trouble than it will help due to outdated information.

Please feel free to add a link to the original thread in your new one if you think it might be helpful.

Best wishes!

Thread closed.

---

