---
title: "Ubuntu 14.04 Crashing After Install"
date: 2015-08-22
forum: Installation &amp; Upgrades
---

### Post by scottinpa40 on 2015-08-22
Hi, I just recently installed Ubuntu 14.04 to dual boot with Windows 7 and Ubuntu seemed to be working fine until I saved a couple pictures into the Pictures folder.  When I double click the folder, it shows the picture thumbnails, but when I click on any of the pictures to view them, the window disappears and takes me back to the desktop.  I then get an internal error message, which I attached to this message.  I would appreciate any help and can't understand how a new install is crashing already.

-Scott

---

### Post by howefield on 2015-08-22
Generally I'd take the error and search the web for more information.

In your case "nautilus crashed with SIGSEGV in jpc_qmfb_join_colgrp()"

Could be [https://bugs.launchpad.net/ubuntu/+source/jasper/+bug/555238](https://bugs.launchpad.net/ubuntu/+source/jasper/+bug/555238)

---

### Post by scottinpa40 on 2015-08-22
OK I read some of it and had a question:  Does Ubuntu have a problem with certain images, like jpeg or png?  I think I put a jpeg image from my Data folder (from the internal hard drive on my PC) into Pictures when this happened.   I'm basically copying some files from the Data partition that I made for Windows 7 and pasting them into Ubuntu folders.

---

### Post by yancek on 2015-08-22
>   Does Ubuntu have a problem with certain images, like jpeg or png?  I

No.  Have them on my Ubuntu install and no problems copying them or viewing them.  I've never seen the problem before so don't have any ideas.

---

### Post by howefield on 2015-08-22
> **scottinpa40 said:**
> OK I read some of it and had a question:  Does Ubuntu have a problem with certain images, like jpeg or png? 

Not that I have ever seen, but it seems that this certain "type" of jpg (jp2) may give the file manager a problem, possibly in creating the thumbnails for the images.

---

### Post by scottinpa40 on 2015-08-22
OK thanks for the answers, I appreciate it!

---

