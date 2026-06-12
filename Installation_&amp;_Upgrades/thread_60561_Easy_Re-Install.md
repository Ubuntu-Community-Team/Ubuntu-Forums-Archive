---
title: "Easy Re-Install"
date: 2005-08-28
forum: Installation &amp; Upgrades
---

### Post by Wermut on 2005-08-28
Two months ago I decided to test Ubuntu. Now I want to use it as my main OS (I virtually have not been using Windows XP during these two months). Unfortunately, the partition for Ubuntu ist only 4.2 GB, so I'll have to make backups, re-partition the drive and install Ubuntu on a larger partition. Since my Ubuntu is now configured perfectly for my needs, I'd like Synaptic to automatically install all the packages for me I have currently installed on this installation. Is there a way to 'export' a list of installed packages, so that they can easily be installed on a new installation?

---

### Post by weekend warrior on 2005-08-31
Not that I'm aware of, sorry.

---

### Post by heimo on 2005-08-31
```
dpkg --get-selections
``` 
lists installed packages - feeding this list to apt-get / aptitude / your favourite package management frontend, should get you close - as long as your sources.list is same as before.

---

### Post by Wermut on 2005-09-02
Thanks, I executed this command:
```
dpkg --get-selections > packages
``` 

But how can I use this list with, say, apt-get?

---

### Post by heimo on 2005-09-02
You can 
 ```
dpkg --set-selections < packages
dselect install

```

---

### Post by az on 2005-09-02
Hold the phone!

If your other partition is bigger than your Ubuntu partition, you can just copy it there.

You do not need to reinstall!

It is wise to make backups, but you should be able to shrink your Windows partition down and make your Ubuntu partition larger.   that is unless you have a relatively small hard disk...

---

### Post by heimo on 2005-09-02
Oh why, oh why do I do it every time. :) (Azz, you're my hero.) I just blindly answer  questions blindly instead of giving best solution. :) (*ashamed*)

---

### Post by Wermut on 2005-09-05
Heimo's solution is still useful, since I plan to use Ubuntu also on the laptop, therefore thank you!

@azz: Is that really possible??? I thought that it is not.
I have partitioned my harddrive like this at the moment:
~2 MB empty space
~75 GB NTFS
~512 MB Swap
4.2 GB ext3

Could you please briefly explain how to shrink / resize partitions or give me a link?

EDIT: according to [http://www.gnu.org/software/parted/parted.html](http://www.gnu.org/software/parted/parted.html) it's not possible to change the starting point of a partition.

Hum... Maybe I'll try something like this:
500 MB Swap
30 GB ext3
20 GB NTFS
20 GB FAT32

AFAIR Linux can write FAT32 flawlessly, so the FAT32-partition could be used for storage. Swap should be faster at the beginning of the disk, right? I must keep Windows because others might use the Computer as well and maybe I will be useful when I absolutely need a Windows-application.

Just one more suggestion please: If I remember correctly, stupid Windows setup will break the multi-boot configuration. How can I prevent / correct this without having to install first Windows, then Ubuntu?

---

### Post by Wermut on 2005-09-07
*bump*

---

### Post by ppl on 2005-09-26
[QUOTE=azz]Hold the phone!

If your other partition is bigger than your Ubuntu partition, you can just copy it there.

You do not need to reinstall!

It is wise to make backups, but you should be able to shrink your Windows partition down and make your Ubuntu partition larger.   that is unless you have a relatively small hard disk...[/QUOTE]

I am concern shrink Windows as well, My Ubuntu need more space and I don't feel like to reinstall everthing.I have another plan which  is get my current Ubuntu backuped, then I restore it in a fresh installed Ubuntu, so I can keep my  setting, but not sure about it, and it is still lost of works, I get a 3.3G backup file right now and not include my movies and mp3s. 
About backup:[https://wiki.ubuntu.com/BackupYourSystem?highlight=%28backup%29]("https://wiki.ubuntu.com/BackupYourSystem?highlight=%28backup%29")

---

