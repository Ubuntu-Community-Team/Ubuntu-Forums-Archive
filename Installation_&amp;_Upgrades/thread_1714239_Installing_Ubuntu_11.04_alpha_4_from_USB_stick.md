---
title: "Installing Ubuntu 11.04 alpha 4 from USB stick"
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by imh90s on 2011-03-25
Hello,
 
I installed the new Ubuntu 11.04 alpha 3 to give it a try as I searched the web about the new release and it got my full admiration.

I went to this page [http://cdimage.ubuntu.com/releases/natty/alpha-3/]("http://cdimage.ubuntu.com/releases/natty/alpha-3/") and downloaded (64-bit PC (AMD64) desktop CD)which gave me .iso file named natty-desktop-amd64.iso . Due to some problems in my DVD-ROM I decided to install it by booting from a USB stick (which I had done it many times before in  installing my current operating system Windows 7) 

**I used [COLOR="Green"]Universal USB installer[/COLOR] to make Ubuntu bootable on the USB stick but when I try to boot my PC from USB nothing done wich means that the content of the USB stick is unbootable. I also tried [COLOR="green"]Unetbootin[/COLOR] to create a bootable USB drive but the same problem existed.**

**I wonder if this problem is due to the new ubuntu is not supported by the two softwares used to make USB stick bootable that I mentioned above, If not..anyone who could succeeded in this process give me a hand. !!!**

---

### Post by Sef on 2011-03-25
When I make a bootable Ubuntu Live USB, I just follow these [directions]("http://www.ubuntu.com/desktop/get-ubuntu/download").

---

### Post by imh90s on 2011-03-25
> **Sef said:**
> When I make a bootable Ubuntu Live USB, I just follow these [directions]("http://www.ubuntu.com/desktop/get-ubuntu/download").

I followed this instruction exactly while using **universal usb installer** but with no happy result

---

### Post by Quackers on 2011-03-25
A couple of things to check.
What size is your usb stick?
Make sure that your pc's bios recognises it as a usb flash drive. My bios recognises one of my usb sticks as a usb HDD! Check that.

---

### Post by ~Plue on 2011-03-25
also, compare the md5sum of the .iso with
[http://cdimage.ubuntu.com/releases/natty/alpha-3/MD5SUMS](http://cdimage.ubuntu.com/releases/natty/alpha-3/MD5SUMS)

---

### Post by imh90s on 2011-03-25
> **Quackers said:**
> A couple of things to check.
What size is your usb stick?
Make sure that your pc's bios recognises it as a usb flash drive. My bios recognises one of my usb sticks as a usb HDD! Check that.

Thanks this tip made me trying something which made the problem got fixed .The USB port in which the USB stick was plugged in, BIOS wasn`t recognizing it as a port for USB booting. I just plugged it in another USB port and it booted successfully.

The only question I had left is that I want to install Ubuntu along side with windows(dual boot) where I can get the instruction concerned with the partition part.

---

### Post by Quackers on 2011-03-25
Glad that the problem is fixed! :-)
If you are using Windows Vista or Windows 7 I would first create some free space for Ubuntu to install into. If there is no "unallocated" space on your hard drive you should use the Windows Disk Management Console to shrink your C: partition (or any other you may wish to shrink). But first make sure that you have only 3 or less primary partitions in use! If you have 4, you will need to delete one first. This is important.
Then in the Ubuntu installer I would recommend that you choose "specify manually" in the partitioning stage of the installation. You can then choose to create your own Ubuntu partitions (root (/), swap and home (/home, if required) from the free space that you created earlier.

It would also be wise to make a set of recovery dvd's if you have not already done so.
A Windows recovery cd should be made too (commonly called a repair disc) via Control Panel > Backup & restore centre.

---

