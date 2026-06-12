---
title: "Installation problem"
date: 2015-10-05
forum: Installation &amp; Upgrades
---

### Post by Stephen_Thomson on 2015-10-05
Im trying to install ubuntu 15.04 and it skips the 'installation type' page and goes straight to the partition section and then freezes when i try to click anything. I wanted to erase windows all together and just run ubuntu so i dont want to make partitions... Any ideas??? 
Thanks

---

### Post by yancek on 2015-10-06
How old is the computer and which version of windows are you using.  What method are you using to try the install?  DVD, flash drive?  If a flash drive, what software did you use to put Ubuntu on it?  When you download the Ubuntu iso file, did you do an md5 checksum to verify that it was a good download?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Bucky Ball on 2015-10-06
Welcome. Have you switched off hibernation and fast startup in Windows??? You need to boot into Windows to do this, do a _complete_ machine shutdown, then reboot to the BIOS and switch off secure boot. Presuming Windows is installed in UEFI mode? If you don't know you should be able to work that out from the BIOS.

Do you have free space to install Ubuntu to? If not, create some using the disk management tool in Windows when you switch off hibernation. Free space only, no partitions for Ubuntu. Create them when you install.

See if you can now get to the partitioning section and 'Something Else'. Once there, you can delete all partitions and create what you like (you can also do this from a live session by launching Gparted and deleting all partitions, then click the 'Install' icon). Good luck.

---

### Post by Stephen_Thomson on 2015-10-06
Hey thanks for the replies!
I have a HP envy laptop from 2013, running windows 8.
I have gone into bios and disabled secure boot is that the same as the quick start thing?
I am unable to select 'something else' because it skips that step of the installation. I go into install, then language, then wifi, then the update page but instead of what type of installation it goes straight to the partition bit.
Thanks again, the help is much appreciated.

---

### Post by Bucky Ball on 2015-10-06
As I said, boot into Windows and switch off hibernation and fast startup ......................

The partition bit is the installation. If it is skipping the 'Install alongside Win' it is probably because you haven't done what I state above. Ubuntu doesn't know Win is there if it is hibernating. 

Follow the first paragraph in my last post carefully.

---

### Post by Stephen_Thomson on 2015-10-06
oh and i used universal usb installer 1.9.6.1 to put burn the image to a usb stick.

---

### Post by Bucky Ball on 2015-10-06
Read post #5. How you created the install media is unimportant as it appears to have worked fine.

---

### Post by Stephen_Thomson on 2015-10-06
hibernation, fast startup and secure boot are all off but still have the same problem.....

---

### Post by Bucky Ball on 2015-10-06
Great. Well, if you want to erase Windows completely, you're good to go I'd say. Can you boot to the live session? (Try Ubuntu.) If so, do that, delete the partitions with Gparted, install Ubuntu. Done.

---

### Post by Stephen_Thomson on 2015-10-06
Ok kool thanks :)
So i boot into try ubuntu, then download Gparted and delete the partitions and then go to install ubuntu? cheers

---

### Post by Bucky Ball on 2015-10-06
You don't need to download Gparted. It is already there.

---

