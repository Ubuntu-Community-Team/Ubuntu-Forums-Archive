---
title: "dist-upgrade now I can't boot"
date: 2006-03-14
forum: Installation &amp; Upgrades
---

### Post by wilso027 on 2006-03-14
I just ran 'apt-get dist-upgrade' on my Breezy Badger system pointing it to

[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main universe restricted multiverse

in /etc/apt/sources.list. I have a sata hard drive that is my primary hard drive. I use 20 Gigs of this drive for my main system and have lvm setup on the rest of the drive and another one. After the update I am getting the following error message on bootup:

ALERT! /dev/sda1 does not exist, dropping to a shell

and I get a few basic tools. Why is it not seeing my sata drive? Does is have support in the kernel? Any help would be greatly appreciated.

Allan

---

### Post by DaBruGo on 2006-03-14
[QUOTE=wilso027]I just ran 'apt-get dist-upgrade' on my Breezy Badger system pointing it to

[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main universe restricted multiverse

in /etc/apt/sources.list. I have a sata hard drive that is my primary hard drive. I use 20 Gigs of this drive for my main system and have lvm setup on the rest of the drive and another one. After the update I am getting the following error message on bootup:

ALERT! /dev/sda1 does not exist, dropping to a shell

and I get a few basic tools. Why is it not seeing my sata drive? Does is have support in the kernel? Any help would be greatly appreciated.

Allan[/QUOTE]

Allan,

I don't know if this will fix your problem ... but here is a [link]("http://ubuntuforums.org/showpost.php?p=774688&postcount=12") to what may be causing your bootup issue.

Let me know if this helps.


DAVE

---

### Post by wilso027 on 2006-03-14
From what I read from your post you are thinking that there is an error in the menu.lst file? I am going to get a livecd and try to boot to it and see what I can find but I think it has to be something a little worse b/c I can't even see the /boot directory. I am thinking that I have to use mkinitrd to rebuild by image to but to but I am  not sure how to do this correctly or if this is the problem. Once I get my live cd I will post my menu.lst file hopefully this will help. Thanks for helping DAVE and any more ideas or more explinations would be very helpful.

---

### Post by DaBruGo on 2006-03-14
[QUOTE=wilso027]From what I read from your post you are thinking that there is an error in the menu.lst file? I am going to get a livecd and try to boot to it and see what I can find but I think it has to be something a little worse b/c I can't even see the /boot directory. I am thinking that I have to use mkinitrd to rebuild by image to but to but I am  not sure how to do this correctly or if this is the problem. Once I get my live cd I will post my menu.lst file hopefully this will help. Thanks for helping DAVE and any more ideas or more explinations would be very helpful.[/QUOTE]

wilso027,

You shouldn't need a Live CD if you can get to the GRUB menu screen with all your bootup options on it. This [LINK]("http://www.ubuntuforums.org/showpost.php?p=593793&postcount=112") will help you play with the menu.lst choices in GRUB.

Hope that helps.


DAVE

---

### Post by wilso027 on 2006-03-14
Thanks Dave I think that is exactly what I am looking for. One additional question though, I have a sata drive what should the root lines in my menu.lst file look like? I am using the first partition on the drive.

---

### Post by DaBruGo on 2006-03-14
[QUOTE=wilso027]Thanks Dave I think that is exactly what I am looking for. One additional question though, I have a sata drive what should the root lines in my menu.lst file look like? I am using the first partition on the drive.[/QUOTE]

wilso027,

Sorry, but I am not sure on sata drives. I wish I had some in my PC since I hear they are noticeably faster.

I will see what I can dig up for ya.


DAVE

---

### Post by wilso027 on 2006-03-14
Unfortunately no luck, i went in and edited the menu.lst but it still errored out. I think it has something to do with it can't load the sata drive. Any ideas?

---

