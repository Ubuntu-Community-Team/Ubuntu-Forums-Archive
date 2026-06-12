---
title: "Cannot create startup usb-flash drive?"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by germanix on 2011-01-07
An uncaught exception was raised: 
[Errno 13] Permission denied: '/media/e6f6ac46-4bfc-487b-9c81-aab706ead9e3/boot'

The above is the error message I get when I try to create an usb-flash boot drive.
I downloaded the iso for Mint10 and use the "create startup disk" program to create the boot drive.
I can see both the iso and the flash drive within the program, but when I click on "create disk" I get the above error message?
What am I doing wrong please?

---

### Post by sikander3786 on 2011-01-07
Are you sure your disk is formatted FAT32?

---

### Post by C.S.Cameron on 2011-01-07
Check the MD5SUM of the ISO:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by germanix on 2011-01-07
1. The disk was formatted when I got it. to fat32. I re-formatted it to ext4. (was this incorrect?)
2. The MD5 sum is correct.

---

### Post by sikander3786 on 2011-01-07
> **germanix said:**
> 1. The disk was formatted when I got it. to fat32. I re-formatted it to ext4.
2. The MD5 sum is correct.

If it is still formatted ext4, re-format is to FAT32 and try again.

Or if you are trying something else like a complete install or something like that, please explain.

---

### Post by germanix on 2011-01-07
All that I am trying to do is to burn the iso to a usb-flashdrive instead of burning it to disk. I have Linux Mint installed on my computer and I just wish to have the iso on the usb drive should I ever need it to either re-install or to boot to, to repair something.
Could you please explain why the usb should be formatted as fat32. I run linux as my sole OS and all of my partitions are formatted as ext 4, I therefore assumed that it would be better to also format the usb as such. I may be thinking wrong but would like to understand why, if so.

---

### Post by sikander3786 on 2011-01-07
To the best of my knowledge, USB creator doesn't support any FS other than FAT nor does Unetbootin.

You can try yourself and if FAT32 is successful, you'll have the answer.

---

### Post by germanix on 2011-01-07
Ok, I reformatted back to fat32 and it now works. I thank you very much for your help and explanations. Have a nice day.

---

