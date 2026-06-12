---
title: "Vista User needs help"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by Hwest on 2009-12-21
Ok, Im a complete noob to this, I am currently operating Vista and have downloaded the 9.10 install ISO, i am considering installing it but i am affraid of destroying my machine and vista. My machine is a Toshiba Satellite A300D. How can i go about installing it in a manner to perserve Vista, because i need it for somethings.
Cheers,
Hamish

---

### Post by KeLa on 2009-12-21
You can install it with wubi. (WindowsUbuntuInstaller)
It will create one directory to your hard drive and put everything there and
you can uninstall it from windows control panel if you don't like it or it doesn't work.

---

### Post by bit mad on 2009-12-21
Try creating a Live CD or USB key first, so you can play with it at no risk (no permanent install required). When you're happy with it, you'll probably be less afraid of messing anything up :)
Make sure all your files are backed up before you do a full install, and if the worst happens then there should be a way of rescuing the situation somehow.

---

### Post by Hwest on 2009-12-21
Will that give me the dual boot option, and i have made a second partition for it

---

### Post by Hwest on 2009-12-21
Ok, do i need to download anyhting for Live Cd

---

### Post by darkod on 2009-12-21
I don't recommend wubi. Yes, easy to install for windows users but do you want to use windows or ubuntu? Wubi can possibly create some issues because it's installed inside windows, it works like virtual ubuntu on its ntfs partitions, etc. You are not getting real linux and its capabilities.
Just crate the cd or usb stick as mentioned, use the Try Ubuntu option first, and when you are happy backup your data and you can use the guided resize option to install it next to vista in its own partition as it's supposed to work.
If it helps you:
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

---

### Post by darkod on 2009-12-21
> **Hwest said:**
> Ok, do i need to download anyhting for Live Cd

The desktop ISO image is called the LiveCD.

---

### Post by Hwest on 2009-12-21
Ok, thanks, i intend to use both OS's

---

### Post by darkod on 2009-12-21
> **Hwest said:**
> Will that give me the dual boot option, and i have made a second partition for it

You made a partition or just freed unallocated space? You CAN NOT create partitions for linux from windows, linux doesn't use ntfs. And during install linux ignores all existing partitions, so if you're new, it will only confuse you to install that way.
From windows, delete that partition you have planned, and leave it as unallocated space.
Then when you want to install ubuntu, boot with the cd, select Install Ubuntu, and in step 4 use the Use Largest Available Free space option. That will set it up in the unallocated space you made.
Job done. :)

---

### Post by Hwest on 2009-12-21
I have made 15.10 GB free space available for ubuntu, Is this enough?

---

### Post by WolfRage on 2009-12-21
More than enough, Ubuntu takes up about 2.75 Gb or less; Depending on which flavor you install.

---

### Post by darkod on 2009-12-21
> **Hwest said:**
> I have made 15.10 GB free space available for ubuntu, Is this enough?

For a start yes, but only if you don't put large videos/music/pics stuff there. The OS itself is around 3-3.5GB so that should give you an idea. Also, few GB will go towards swap partition that will be created by the installer.
But Ubuntu can read ntfs partitions so if you have any videos for example in your vista, you can use them. Or from external hdd.

---

