---
title: "Upgrade to Karmic 9.10 &amp; ext3 or ext4"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Mark_in_Hollywood on 2009-10-13
With Karmic Koala 9.10 just around the corner. If I do

Alt-F2 

upgrade -d

will I get offered ext4 or will the upgrade be automatic, without user intervention?

---

### Post by swoody on 2009-10-13
I believe you are referring to:
```
update-manager -d
```
If you're planning on using this method to upgrade, then it will keep your filesystems the way they are. It will update your repositories, and download all the new packages available for 9.10, but it won't give you the option to change your filesystem type. If you're interested, please take a look at this guide on how to change from ext3 to ext4:
[http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21](http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21)

** Please note: before doing any version upgrade, or changing your FS type, *please* create backups of any files and data that you don't want to risk losing! **

---

### Post by BDNiner on 2009-10-13
I don't think that you would be upgraded from ext3 to ext4. If you want to upgrade to ext4 then I suggest you do a clean install when 9.10 is released. I know you can upgrade ext3 to ext4 and leave the file system intact. I however do not know anyone that has done this.

---

### Post by swoody on 2009-10-13
> **BDNiner said:**
> I however do not know anyone that has done this.

It's well documented, and there have been many people who have done this successfully. However, I do agree that a fresh re-install would be my preferred way to upgrade to 9.10, as there is also the issue of upgrading to Grub2 when upgrading from an existing installation.

---

### Post by QIII on 2009-10-13
I'm not at my Ubuntu machine right now ...

This is not as intimidating as it may seem, if you follow the tutorials to the letter.  If you are at all uncomfortable, however, it would probably be best to back everything up and wait to do a fresh install of Karmic.

GRUB2 can be installed on Jaunty and the file system can be changed to ext4.

I have done both to my Jaunty machines.

A reference was provided for changing to ext4, I believe.  There are also GRUB2 tutorials.

(Here's a tutorial.  Like I said, I'm not at my machine, so I can't consult my notes...
[http://linuxhub.net/2009/07/install-grub-2-on-ubuntu-jaunty-jackalope/](http://linuxhub.net/2009/07/install-grub-2-on-ubuntu-jaunty-jackalope/))

Before doing anything, however, DO BACKUPS!  

If you are dual booting, you will want to install os-prober, run os-prober and then update-grub2.  If you'd like instructions, search for my nickname and "os-prober" and you'll find several instances.

If you want to upgrade from Jaunty to Karmic rather than reinstalling, I highly suggest you do both before upgrading.

---

### Post by BDNiner on 2009-10-13
> **swoody said:**
> It's well documented, and there have been many people who have done this successfully. However, I do agree that a fresh re-install would be my preferred way to upgrade to 9.10, as there is also the issue of upgrading to Grub2 when upgrading from an existing installation.

that is true it is well documented and i did consider doing this myself but instead I went with a fresh install.

I felt that it is the better route (although maybe longer) to do a full backup and then a fresh install using the new file system. 

I would feel better referencing a tutorial or guide if i had done the steps myself, or seen some one do it.

---

