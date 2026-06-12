---
title: "kernel panic when installing ubuntu"
date: 2014-11-08
forum: Installation &amp; Upgrades
---

### Post by tio3 on 2014-11-08
Hello guys, i'm totally new to this ubuntu stuff, i'm trying to learn here, so i bought a fresh netbook w/o OS
everything went smooth, installer menu pop up as it should be, but after i choose install, then this stuff shows up in my screen

[http://s1236.photobucket.com/user/kebogokilz/media/60192_zps6e850520.jpg.html](http://s1236.photobucket.com/user/kebogokilz/media/60192_zps6e850520.jpg.html)

*some people might feel disturbed for loading this img, so i decided just to post the link :s

kernel panic - not syncing vfs unable to mount root fs on unknown-block(2, 0)

any idea how to solve this ?

i've tried so many stuff,
- trying another iso
- another flashdisk
- using unitbooting and universal usb installer
- dont bother about dvd :s netbook has no dvd
- i've tried all option on installation screen

for some information, my notebook specs :
Lenovo E10-30
- memory 2GB DDR3
- proc intel celeron N2815
- storage 320gb

i'm sorry if this question totally FAQ stuff :s but please help me
if anyone knows some other link that might be related into this, please kindly tell me :s
andd sorry for my bad english

---

### Post by yancek on 2014-11-08
It's possible there was a problem with the download.  You can verify the iso download of Ubuntu with md5sum command.  The page below has a list of all the Ubuntu iso files, find the one you downloaded and run the md5sum check and compare it to the md5 hash listed on the page.  Near the top of the page there is a link, HowToMD5SUM which explains the command to use.

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by tio3 on 2014-11-08
> **yancek said:**
> It's possible there was a problem with the download.  You can verify the iso download of Ubuntu with md5sum command.  The page below has a list of all the Ubuntu iso files, find the one you downloaded and run the md5sum check and compare it to the md5 hash listed on the page.  Near the top of the page there is a link, HowToMD5SUM which explains the command to use.

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

thanks alot for the response, i appreciate it so much

well, i've tried everything that written on your link, and it seems all of my isos are fine

thanks btw , now i know how to check iso file , which is nice :D

---

### Post by sp40140 on 2014-11-10
Hello
go through this thread and see if that helps.
[http://ubuntuforums.org/showthread.php?t=1751574](http://ubuntuforums.org/showthread.php?t=1751574)

---

