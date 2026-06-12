---
title: "Which format do you prefer for shared partitions?"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by PerlMountain on 2007-05-13
[SIZE="4"]**[CENTER]_What is your preference?_[/CENTER]**[/SIZE]

[CENTER][IMG]http://perlmountain.com/fs.jpg[/IMG][/CENTER]

Which type of file system do you prefer to use for shared files on a dual boot setup?

[LIST][*]NTFS file system using [**ntsf-3g**]("http://ubuntuforums.org/showthread.php?t=217009"), allowing Linux write access.
[*]Ext3 file system using [**FS-Drive**]("http://www.fs-driver.org/") allowing Windows read and access.
[*]FAT32 file system, allowing both access with some limitations.
[*]Something else (please specify).[/LIST]

PME

---

### Post by hal8000 on 2007-05-13
Personally I use an ext3 partition to share data amongst my linux and FreeBSD installs. I can safely write and read from my windows ntfs partition from linux but would never trust a windows partition to even read my ext3 file system, its probably safe but thats just me.

Ther are alternatives though, a USB memory stick is also good for copying data between different systems, and you dont have to worry about your /etc/fstab

---

### Post by PerlMountain on 2007-05-13
Makes sense using USB. Also, I found a very clear tutorial on [**/etc/fstab**](http://www.tuxfiles.org/linuxhelp/fstab.html).

.

---

### Post by nphx on 2007-05-13
Can Windows XP write to Ext3 ?

---

### Post by PerlMountain on 2007-05-13
> **nphx said:**
> Can Windows XP write to Ext3 ?I haven't used it, but yes, using [**FS-Drive**](http://www.fs-driver.org/). ([*notes](http://www.fs-driver.org/faq.html#acc_ext3)).

---

### Post by ep2011 on 2007-05-13
> **PerlMountain said:**
> I haven't used it, but yes, using [**FS-Drive**](http://www.fs-driver.org/). ([*notes](http://www.fs-driver.org/faq.html#acc_ext3)).

I've used a similar program (Forgot the name, sorry, Im in Ubuntu now) That lets you read them only and transfer files from Linux -> Windows only, and it worked great. (The reason I liked it is because you don't need to install anything, you can run it without installing.)

---

### Post by bulldog on 2007-05-13
I think it's important which OS is your main OS.
If it's ubuntu you probably don't want to copy it to a NTFS partition.
If it's windows you could have the need to copy something from an ext3 partiton.

So my conclusion is install the  [http://www.fs-driver.org/](http://www.fs-driver.org/) in your windows.

But that's just me.........:) 

It works without a problem,though.:guitar:

---

### Post by PerlMountain on 2007-05-13
I picked NTFS even though I haven't done this yet, the ntsf-3g option looks very friendly to me so:

I just created a small and a large (storage) NTFS file format and left about 4 GB for my Kubuntu install. As much as I want to switch over, I think Xp will be my main OS while I'm getting through this curve and learning Linux.

That's why 8)

---

### Post by gorkur on 2007-05-13
I use FAT32. Ubuntu is my main OS and I only use Windows for gaming.

---

### Post by tkainz on 2007-05-15
I currently have a 10 GB partition as fat32 which, so far, seems to work great for both Windows and Linux.  This is only temporary of course as once I've completed installing and configuring Unbuntu and have put into place all of the software I need for my day to day life and once my Linux learning curve has hit the "comfortable" phase - Windows is "TOAST".:)

---

