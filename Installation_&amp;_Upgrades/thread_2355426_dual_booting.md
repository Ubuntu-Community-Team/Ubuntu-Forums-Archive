---
title: "dual booting"
date: 2017-03-12
forum: Installation &amp; Upgrades
---

### Post by 12cherith on 2017-03-12
I have windows 10 installed on one partition and wish to install ubuntu 16.04 on another partition. However on bootup only windows is availabe. How can I install ubuntu and see both windows and ubuntu on bootup .Also when this happens how do I retrieve the ubuntu partition when only windows is available.

---

### Post by RobGoss on 2017-03-12
Hello and welcome, Have you already installed Ubuntu on the second partition?

Is your machine **UEFI**? these questions are most important if you're trying to dual boot your system

Take a look at Oldfred's** UEFI** tips before you attempt to dual boot your system [https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295) please make sure you have a full understand how this is done to prevent damaging your Windows's installation

---

### Post by yancek on 2017-03-12
I would also suggest you read the Ubuntu documentation on dual booting windows/Ubuntu UEFI which is most likely what you have IF windows 10 was pre-installed.  Also, it isn't clear from your post whether you are just planning to install or have a failed attempt.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by 12cherith on 2017-03-12
No I don't believe that my comp[uter has UEFI. I have had numerous failed attempts where only windows loaded in the boot menu.In the current install I got as far as the partitioning found I couldn't install side by side so pulled out. The point is if I do install and only windows boot how do I retrieve ubuntu?
Many Thanks

---

### Post by RobGoss on 2017-03-13
If your machine is not **UEFI **then most likely it's Legacy, if this is the case you should still be able to setup a dual boot system

Please tell us in details what steps have you already taken to install Ubuntu and what the** specs **are for your machine, **Model, Ram, Video chip,** 

How are you creating the partition to install Ubuntu? are you using Windows **Disk management** tool to create it

What method are you using to create the Ubuntu's ISO file meaning what program?

---

### Post by oldfred on 2017-03-13
From live installer post this.

sudo parted -l

---

