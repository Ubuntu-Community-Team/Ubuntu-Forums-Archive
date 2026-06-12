---
title: "Help needed to install side by side with XP"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by tom1252 on 2011-02-20
Hi

I have an old Dell Dimension 2400 and want to install the latest version of the OS. I downloaded the software and burnt the image to a CD. I new the CD had worked as it was recognized by my laptop. When i insert the disk into my CD drive i selected boot from CD drive. It came up with something like "IOSLINUX from a certian date to now" but didnt load. I load up the computer like normal and clicked on the CD from my computer. It came up with a message like " The application could not be loaded, reinstalling it may fix this".

Not sure why.

Any ideas?

Thanks

Tom

---

### Post by kansasnoob on 2011-02-20
Check this out:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by tom1252 on 2011-02-20
Hi Thanks for the reply. That is how i did it.

---

### Post by tom1252 on 2011-02-20
I re burnt the image and has done the same thing.

The exact message is "ISOLINUX 4.01 debian-20100714 ETCD copyright (C) 1994 - 2010 H. Peter Anvin et al EDD: Error bb00 reading sector 348872. No default or UI configuration directive found!"

---

### Post by tom1252 on 2011-02-20
Also tried USB with no luck. Any idea's? :(:confused:

---

### Post by sikander3786 on 2011-02-20
Welcome to the forums :-)

Please first of all check the MD5SUM of your downloaded image.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

And also please let us know which version of Ubuntu did you download and from where?

---

### Post by tom1252 on 2011-02-20
Thanks for the reply. 

I downloaded 10.10 from the official Ubuntu website. The md5sum came out different on the two downloads i made.

---

### Post by sikander3786 on 2011-02-20
Re-download and again check the MD5SUM. If you use a torrent, the image will automatically be checked and there are very little chances of it getting corrupt. Then re-burn a disc or USB and boot from it.

Let us know about your progress please :-)

---

### Post by tom1252 on 2011-02-20
Thank you. I have learnt something new about downloads:D. 

Result the md5sum matched up. I will install it tomorrow.

Thanks again

---

### Post by kansasnoob on 2011-02-20
> **tom1252 said:**
> Thank you. I have learnt something new about downloads:D. 

Result the md5sum matched up. I will install it tomorrow.

Thanks again

Before trying look at posts #1 and #15 here:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

The major problem with the 10.10 installer is now in the release notes:

[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install)

> In dual boot installs, side-by-side partitioning can be overridden by the user, resulting in data loss. After selecting the "Install alongside other operating systems" option, clicking on either the "Use entire partition" of "Use entire disc" buttons will override the side-by-side partitioning and result in a loss of data.

Bug linked to:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

---

### Post by tom1252 on 2011-02-21
Thanks for all the help. It was successful. :D

I am of to play on it now!

---

### Post by tom1252 on 2011-02-21
After all the trouble of downloading error riddled copy's of the latest  ubuntu OS, i have yet again come up with more troubles. All though it  has been a challenged I think it is cracking piece of software, and it's  FREE. Anyway I have a WG111v2 Netgear dongle. I have followed the  following guide [10 steps of how to set up WiFi (Netgear WG111) on Ubuntu - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=202254&highlight=wg111+netgear"),  the best i can. It is for the older version and a few things have  changed. (E.g. Buttons have different names.). Anyway it has picked up a  neighbours wireless network but can't find mine. So i tried to add it  manually and that worked and says it is connected but no Internet  connection. Any idea's why?

---

### Post by tom1252 on 2011-02-23
> **tom1252 said:**
> After all the trouble of downloading error riddled copy's of the latest  ubuntu OS, i have yet again come up with more troubles. All though it  has been a challenged I think it is cracking piece of software, and it's  FREE. Anyway I have a WG111v2 Netgear dongle. I have followed the  following guide [10 steps of how to set up WiFi (Netgear WG111) on Ubuntu - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=202254&highlight=wg111+netgear"),  the best i can. It is for the older version and a few things have  changed. (E.g. Buttons have different names.). Anyway it has picked up a  neighbours wireless network but can't find mine. So i tried to add it  manually and that worked and says it is connected but no Internet  connection. Any idea's why?

I have narrowed it down to being something with the router settings. I have no idea what i am looking for with the settings but I can log in to the router to edit them. So if someone with experience knows what to do it would be great. Thanks Tom

---

### Post by tom1252 on 2011-02-23
This is the router i have:

[http://www.ebuyer.com/product/78906](http://www.ebuyer.com/product/78906)

---

### Post by tom1252 on 2011-02-23
I have gone through some of the router settings. I have changed the  security type from WEP, WPA and none at all. No luck. I have no idea  what to do. Windows is so much easier to setup wireless network but  Ubuntu is a lot better at other stuff, otherwise i would have gone back.

---

### Post by tom1252 on 2011-02-24
Also when I try and manually connect to my router, it asks for the key and I type it in. A message pops up says wireless disconnected and then asks for the key again. Forgot to mention that.

---

