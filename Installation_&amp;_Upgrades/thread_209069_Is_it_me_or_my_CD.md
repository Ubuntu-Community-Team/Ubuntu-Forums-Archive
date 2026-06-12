---
title: "Is it me or my CD?"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by twoseids on 2006-07-04
I have been trying for two days (not continuously) to install Dapper onto my brand new Dell Latitude, with no success. Partitioning seemed to go fine, and the installation seems to go okay until it's actually doing the installation of files. When it gets somewhere around "Preparing ubuntu-desktop", my screen goes mostly black, with the exception of a couple white squares.

The little computer light still blinks intermittently on my computer, telling me the hard drive is still doing something. But after a minute or two, that stops as well.

Do I just have a bad download? Or a bad CD? Or is this a known problem?

Thanks!

P.S. I'm doing the alternate install, since the live desktop install was WAY problematic for me.

---

### Post by adwait on 2006-07-04
Did you check the MD5 of the downloaded ISO image and compare it with the one published @ [www.ubuntu.com](www.ubuntu.com) ? Also, did you check the CD for defects through the installer itself?

---

### Post by aysiu on 2006-07-04
Yeah, it sounds like a bad download or burn.
[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html) should help.

---

### Post by twoseids on 2006-07-04
I'll check both of those things after some of the 4th festivities. Thanks for your tips - if they don't really reveal anything unusual, I'll just download it and burn it again...

---

### Post by twoseids on 2006-07-04
No dice. I followed the steps above, and even downloaded a fresh copy from a torrent, since torrents apparently are less frequently corrupt. But my computer still froze up during the installing of ubuntu-desktop (somewhere around 55% done).

Also, the partitioner wouldn't let me mount my Windows partition as /windows. I had to settle for /media/sda2.

I guess I'll just download Breezy and then upgrade?

---

### Post by Magadass on 2006-07-04
Yeah its your burner I had the same issue and couldnt figure it out so I took one of my older burners from another one of my machines and burned my ISO and it worked fine.  Was odd because MD5 and everything checked out just fine, I think it has to do with the compatability layer that is written to the DVD's and so forth. It may be written differently depending on your firmware for your drive, and the Linux BootLoader my have some issues with it.  

I think they need to seriously look into this issue though, its a huge thing and I have run into it quit often in the forums on the net.

---

### Post by Magadass on 2006-07-04
BTW I am a Microsoft engineer, I'll take no offense to the signature though :P

I enjoy developing for Microsofts products, its fun and everyone is a hardcore geek around me, but I also love linux so what can I say! hehe

---

### Post by twoseids on 2006-07-05
[QUOTE=Magadass]BTW I am a Microsoft engineer, I'll take no offense to the signature though :P

I enjoy developing for Microsofts products, its fun and everyone is a hardcore geek around me, but I also love linux so what can I say! hehe[/QUOTE]
Thanks for the advice, Magadass - I burned it from my dad's computer and it installed just fine.

Only problem is that it's text only. How do I get to X? Never done this bit before...

---

### Post by Magadass on 2006-07-05
Well not sure why you are getting only text, it should start X server for you using the Live CD.  But if you are staring at a command shell just type startx and it will load X server for you...

---

### Post by twoseids on 2006-07-05
[QUOTE=Magadass]Well not sure why you are getting only text, it should start X server for you using the Live CD.  But if you are staring at a command shell just type startx and it will load X server for you...[/QUOTE]
I'm not using the Live CD, I'm using the alternate install. The Live CD was even buggier than the alternate on my machine.

I've been searching the forums and can't get this thing working. I've been *dpkg-reconfigure xserver-xorg*'ing all over the place, but it's not fixing the problem.

---

### Post by smoop on 2006-07-05
I am having the same problem where the install hangs up and I get a black screen with two small squares in the middle.

I also did all of the checks that come with cd.

I am using the alternate CD and have already had success with it on another computer.

I am using an Alienware Sentia laptop.

I am going to download and try out the live cd to see if I can get it up an running again.

---

### Post by twoseids on 2006-07-05
[QUOTE=smoop]I am having the same problem where the install hangs up and I get a black screen with two small squares in the middle.

I also did all of the checks that come with cd.

I am using the alternate CD and have already had success with it on another computer.

I am using an Alienware Sentia laptop.

I am going to download and try out the live cd to see if I can get it up an running again.[/QUOTE]
I got the "small squares" problem up until the time I burned the alternate install .iso on a different computer. Then it finally worked (or did it?).

---

