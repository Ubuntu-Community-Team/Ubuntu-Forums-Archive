---
title: "Can i install ubuntu to a new Disk?"
date: 2021-09-21
forum: Installation &amp; Upgrades
---

### Post by rookie69 on 2021-09-21
I have 2 Disk. 1 ssd and one Hdd. I have windows 10 on my ssd. I want to completely remove windows and install ubuntu on ssd. Note that all of my personal data will be in my hdd which have 3 partition. I want all the data of my HDD to be intact and remove all data of SSD and fresh install ubuntu whille i will also remove my Windows (os) from my SSD. How to do this. It would be a great help :D

---

### Post by grahammechanical on 2021-09-21
I find it very difficult to read you post because of the unnecessary colours you have chosen to format the text in. So, I will just direct you to these installation guides.

[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

[https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started](https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started)

1) Make sure you load the USB memory stick with Ubuntu on in UEFI mode
2) Select the Erase Disk and install Ubuntu option
3) Disconnect the hard drive first just in case you choose the hard drive instead of the SSD.
4) Think very carefully about your decision to remove Windows 10. Once it is gone it is more difficult to re-install it than it is to install Ubuntu without removing Windows 10.

Regards

---

### Post by ActionParsnip on 2021-09-21
Yes. Ubuntu can install to a blank drive. I suggest you run a last full backup before you start in case of catastrophe

---

### Post by tea for one on 2021-09-21
What is the file system on the partitions of your HDD?

As mentioned by [COLOR="#0000FF"]ActionParsnip[/COLOR], do you have a backup of this HDD?

---

### Post by kurt18947 on 2021-09-21
> **grahammechanical said:**
> I find it very difficult to read you post because of the unnecessary colours you have chosen to format the text in. So, I will just direct you to these installation guides.

[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

[https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started](https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started)

1) Make sure you load the USB memory stick with Ubuntu on in UEFI mode
2) Select the Erase Disk and install Ubuntu option
3) Disconnect the hard drive first just in case you choose the hard drive instead of the SSD.
4) Think very carefully about your decision to remove Windows 10. Once it is gone it is more difficult to re-install it than it is to install Ubuntu without removing Windows 10.

Regards

All very good advice. It can be handy to have a Windows install just in case. For instance I find myself having to use hardware that there is no foreseeable chance of its working with anything other than Windows. You could use Windows disk tools to shrink the Windows partition if that makes sense. I dual boot and have had no issues. It's simpler to install Ubuntu on a system with Windows already installed than to install Windows afterwards. Windows boot manager will overwrite GRUB and you'd have to re-install GRUB (or something like that). Simpler to install Ubuntu after Windows.

---

### Post by QIII on 2021-09-21
@rookie69 --

Please use the default font and color unless you need to draw attention to a particular part of your post.  Even then, I would suggest italics or bold for the sake of those with limited color perception.

---

### Post by rookie69 on 2021-09-22
Sorry to those who find it difficult to read. I'm new to all these 
NO i dont have any backup of hdd as i want my hdd untouched
I want to install only on my SSD.

---

### Post by rookie69 on 2021-09-22
Thanks Brother
Sorry for the trouble

---

### Post by Impavidus on 2021-09-22
> **rookie69 said:**
> NO i dont have any backup of hdd as i want my hdd untouched

We all want our hard drives untouched and working forever, but the truth is that we accidentally touch them and sometimes they just break down. So it's best to have backups anyway.

tea for one asked about the filesystems used on the hard drive. The thing is, Windows uses different filesystems from Linux. Windows uses NTFS or sometimes FAT or exfat. Linux can read and write NTFS (and the others), but can't repair them if damaged, like after unclean shutdown. That means that one shouldn't use Windows filesystems on a computer that only has Linux installed. You can't convert from Windows filesystem to Linux filesystem leaving the files in place. You have to copy the files to a backup location, format the partitions and copy the files back.

---

### Post by slickymaster on 2021-09-22
*Thread moved to **Installation & Upgrades**.*

---

### Post by rookie69 on 2021-09-22
> **Impavidus said:**
> We all want our hard drives untouched and working forever, but the truth is that we accidentally touch them and sometimes they just break down. So it's best to have backups anyway.

tea for one asked about the filesystems used on the hard drive. The thing is, Windows uses different filesystems from Linux. Windows uses NTFS or sometimes FAT or exfat. Linux can read and write NTFS (and the others), but can't repair them if damaged, like after unclean shutdown. That means that one shouldn't use Windows filesystems on a computer that only has Linux installed. You can't convert from Windows filesystem to Linux filesystem leaving the files in place. You have to copy the files to a backup location, format the partitions and copy the files back.


Now i get it brother. Thanks xD :D

---

### Post by rookie69 on 2021-09-22
> **slickymaster said:**
> *Thread moved to **Installation & Upgrades**.*
Sure bro .
Thanks for all the response to each and everyone of you <3

---

