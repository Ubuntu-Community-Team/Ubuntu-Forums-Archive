---
title: "Can't get installer to load"
date: 2017-01-31
forum: Installation &amp; Upgrades
---

### Post by mwootton on 2017-01-31
I'm trying to install Ubuntu (either 16.04 or 16.10) on a computer which currently has Windows 10 installed. I have been able to boot into GRUB using multiple Ubuntu versions,multiple different USB sticks and using multiple different applications to create the installation media (Etcher, Rufus, Win32DiskImager). Additionally, I have tried editing the loading string in grub (using nomodeset, turning off splash and quiet) but the most I can get to happen is for the Ubuntu installer to flash a some lines of text indicating that it is trying to load before my display loses input. Unfortunately the lines of text appear and disappear faster than I can read them. 

I'm thinking that I'm having some sort of hardware issue but I'm not sure what might be the cause. My motherboard doesn't have secure boot or fast/quick boot (that I can tell) and I think the issue might lie with some other piece of hardware. Here is my current setup:

Processor: Intel i7 2600k
Motherboard: Asus Sabertooth P67 Motherboard
Video Card: MSI GTX 970
Hard Drive: Samsung SSD 850 
Current OS: Windows 10

Also, I have confirmed using diskpart in Windows that my OS drive is using UEFI.

Any thoughts on what might be preventing me from launching setup or a livecd version of Ubuntu via grub? I appreciate any thoughts or advice you might have. 

Thanks,!

---

### Post by yancek on 2017-02-01
Did you verify the Ubuntu iso you downloaded was good by using an md5 checksum.  That might be a problem.  If you are using windows 10, it is probably UEFI so I woulds suggest you read through the Ubuntu documentation on that at the link below.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by mwootton on 2017-02-02
I did verify the checksum and after sleeping on it realized I was using the nomodeset in the wrong place in the grub startup string. After moving it to the proper location, the Noveau driver was disabled and I was able to boot. Thank you for your assistance!

---

