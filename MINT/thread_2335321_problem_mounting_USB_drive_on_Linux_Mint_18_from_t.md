---
title: "problem mounting USB drive on Linux Mint 18 from terminal"
date: 2016-08-27
forum: MINT
---

### Post by mtzgamer01 on 2016-08-27
Hi,

I was trying to install the video drivers for my PC and it got screwed up, so now I am trying to save some of the files, but I only have the terminal and cannot figure out how to find my USB drive. I have tried this method so far:

```
fdisk -l
```

And then:

```
mount /dev/sda1 /media/usb
```

But I am not sure if sda1 is the drive or what. It says that it is the EFI System, but there is no sda that tells me it is the USB. How do I find which one is the drive, and how do I make sure that it is the one?

Thanks.

---

### Post by ajgreeny on 2016-08-27
*Thread moved to **MINT**.* which is more appropriate for the problem.

Show us the output of terminal command ```
sudo parted -l
```
and then after attaching the USB drive the output of command ```
mount
```

---

### Post by yancek on 2016-08-27
sda1 is the EFI partition so rest assured, that isn't it.  Did you not get any output from fdisk?  Posting the parted output should tell you.

---

### Post by mtzgamer01 on 2016-08-29
*I am doing this all as superuser for ease of use*

I did
```
parted -l
```

and found the drive is /dev/sdb

Then I did

```
fdisk -l
```

and it output that the disk /dev/sdb is /dev/sdb1.

Then I did

```
mount /dev/sdb1 /media/usb3
```

and that mounted it. 

Thank you all for helping me to figure it out. I didn't post the outputs because they are really long and I didn't have much time.

---

