---
title: "Any way I can get the updates on a CD?"
date: 2006-08-02
forum: Installation &amp; Upgrades
---

### Post by hypersonic5 on 2006-08-02
I install and reinstall Dapper a lot since I like to tinker with my settings and usually end up messing everything up. So I like to do clean installs. This wouldn't be a problem but after I do a clean install of Dapper, the update manager kicks in and tells me that I have around 200 MB of updates to install. I have a really slow internet connection and this usually takes me a few hours. Is there any way I can get the updates on a separate CD so I won't have to download them a million times?

I apologize if this has been asked before or if this is in the wrong forum.

---

### Post by 5-HT on 2006-08-02
The upcoming point release of Dapper ([http://www.ubuntuforums.org/showthread.php?t=227075](http://www.ubuntuforums.org/showthread.php?t=227075)) will contain all updates until whenever the cutoff is. You'll need to download the disk image, but it should save you a lot of time.

---

### Post by hypersonic5 on 2006-08-02
Awesome. That's just what I need. Thanks.

---

### Post by koshari on 2006-08-02
ok, the dirty and easy way is to go into the /var/cache/apt/archives directory and burn all the .deb files to a rewritable dvd or removable memory card/usbDrive.

then after you have reinstalled the OS copy all the debs back into the /var/cache/apt/archives directory then do te updat, 

any of the debs you had it wont need to download again :-)

there are more refined ways to do this if you want to research, 

things like personal resositorys,

---

