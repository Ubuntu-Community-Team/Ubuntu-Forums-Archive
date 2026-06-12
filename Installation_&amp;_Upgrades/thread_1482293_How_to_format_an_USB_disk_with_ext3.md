---
title: "How to format an USB disk with ext3"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by Lutz_NL on 2010-05-13
I want to format an USB disk with ext3. If I do this with gparted, it will be formatted, but I cannot write to it. Reading is no problen, at least it shows the lost+found folder.

I guess its a problem with access rights. It would be sufficient if user "papa" would have access on one ubuntu karmic machine. But I cannot solve this graphically.

The purpose of the operation is to be able to copy my /home directory onto the USB disk as a backup, before I upgrade to the current version of Ubuntu.

FAT32 is no option as some files are too long. 

Thanks for reading!

---

### Post by wkulecz on 2010-05-13
sudo rsync -ax /home/ /media/usbdrive

Is how I usually do my backups.

---

### Post by Lutz_NL on 2010-05-14
Actually you are describing the copying step. 

I first have to learn how to format the drive that everybody can write to it. As it is an external disk, I can format it with gparted, but cannot write afterwards.

---

### Post by darkod on 2010-05-14
> **Lutz_NL said:**
> Actually you are describing the copying step. 

I first have to learn how to format the drive that everybody can write to it. As it is an external disk, I can format it with gparted, but cannot write afterwards.

Just a thought. Your hdd ubuntu has users, permissions, etc.

The cd live mode shouldn't. How about booting in live mode, plugging in the ext hdd and trying the format?

---

### Post by wojox on 2010-05-14
You can also open up Disk Utility and format it that way.

---

### Post by Lutz_NL on 2010-05-18
> **wojox said:**
> You can also open up Disk Utility and format it that way.
It finally worked with booting from the internal hard disk, choosing the disk utility and then either ticking or unticking "taking ownership over filesystem".

---

### Post by chiwi on 2010-05-18
if you wanted to backup your whole /home dir, why didn't you just 'tar jcvpf homeBackup.tar.bz2 /home'  ?

---

### Post by Lutz_NL on 2010-05-18
> **chiwi said:**
> if you wanted to backup your whole /home dir, why didn't you just 'tar jcvpf homeBackup.tar.bz2 /home'  ?

The purpose of the operation is the upgrade from Karmic to current with upgrading from ext3 to ext4 and replacing of the harddrive.

That's a lot for someone like me.

---

### Post by chiwi on 2010-05-18
right, i believe it'd be better if you just tar'ed the directory, copy it (it's a single file) to whatever media and filesystem you want (USB stick, cd/dvd ), upgrade to Lucid and then untar the file.

I would've done that, it's just a different approach.

---

### Post by lenooh on 2010-12-02
> **Lutz_NL said:**
> I want to format an USB disk with ext3. If I do this with gparted, it will be formatted, but I cannot write to it. Reading is no problen, at least it shows the lost+found folder.

I guess its a problem with access rights. It would be sufficient if user "papa" would have access on one ubuntu karmic machine. But I cannot solve this graphically.

The purpose of the operation is to be able to copy my /home directory onto the USB disk as a backup, before I upgrade to the current version of Ubuntu.

FAT32 is no option as some files are too long. 

Thanks for reading!
you could just do
```
sudo chown <your_username>:<your_username> <your_mountpoint>
```

then you have read/write access.


br

---

