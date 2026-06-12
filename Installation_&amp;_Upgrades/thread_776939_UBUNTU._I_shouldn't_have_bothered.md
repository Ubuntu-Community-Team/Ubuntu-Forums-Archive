---
title: "UBUNTU. I shouldn't have bothered"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by thomasyo on 2008-05-01
:mad:I really wanted to run Ubuntu with a dual boot with xp. I have errors different from any other that i have found on the forum here and in other Linux forums but it appears that either no one has an answer or there isn't one. I am a huge supporter of the Linux philosophy but am at my last straw with trying to install Linux to my PC. I am very disheartened with the Linux community.

I have d/l 7.10 and burnt it once to a cd once to a DVD both times tested perfect and both times instead of installing i only get to the test Ubuntu but it takes me to a login screen to which i have a limited time to login. I have no login as i have not installed Ubuntu i then get the error 

      "Your session only lasted less than 10 seconds.If you have no logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem."

~/.xsessions-errors file

I have tried both failsafe sessions and have tried the graphic safe options but i think my install screen is different from everyone else's as i do not have a cursor and can only use the keyboard (My live cd when in windows says to just double click install)

someone please at least try and work with me on this one as i will not try again, maybe at all to install any Linux programs if i do not get some help or a response to this.

---

### Post by pbpersson on 2008-05-01
> **thomasyo said:**
> :mad:I really wanted to run Ubuntu with a dual boot with xp. I have errors different from any other that i have found on the forum here and in other Linux forums but it appears that either no one has an answer or there isn't one. I am a huge supporter of the Linux philosophy but am at my last straw with trying to install Linux to my PC. I am very disheartened with the Linux community.

I have d/l 7.10 and burnt it once to a cd once to a DVD both times tested perfect and both times instead of installing i only get to the test Ubuntu but it takes me to a login screen to which i have a limited time to login. I have no login as i have not installed Ubuntu i then get the error 

      "Your session only lasted less than 10 seconds.If you have no logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem."

~/.xsessions-errors file

I have tried both failsafe sessions and have tried the graphic safe options but i think my install screen is different from everyone else's as i do not have a cursor and can only use the keyboard (My live cd when in windows says to just double click install)

someone please at least try and work with me on this one as i will not try again, maybe at all to install any Linux programs if i do not get some help or a response to this.

Please tell us exactly what sort of system this is:

Make
Model
CPU
RAM
Video card
Network card
hard drive

What sort of partitions (file systems) are on the hard drive now, or is it totally blank?

If we know the details, someone here might have encountered the same problem with the same hardware or disk configuration

---

### Post by thomasyo on 2008-05-01
> **pbpersson said:**
> Please tell us exactly what sort of system this is:

Make
Model
CPU
RAM
Video card
Network card
hard drive

What sort of partitions (file systems) are on the hard drive now, or is it totally blank?

If we know the details, someone here might have encountered the same problem with the same hardware or disk configuration



CPU; Intel Pent.4 3.2 gig

RAM; 2 gig 

Video card; NVIDIA GeForce 5200 (i know i know i'm getting a new one)

Network card; Realtek RTL8139 Family PCI fast ethernet NIC

hard drive; 120 gig from which i run XP home service pack 2 and a 40 gig currently set as slave to XP but which i would like to use solely for Ubuntu.

Thankyou for the reply and if iv'e missed anything let me know and where to find it as i'm eager to become more computer savvy.:)

---

### Post by bigken on 2008-05-01
you could download 8.04 the latest version also how do you burn your discs ? in windows use [infraRecorder]("http://infrarecorder.sourceforge.net/") and burn as slow as possible your hardware is ok

---

### Post by Aearenda on 2008-05-01
Hardware looks ok to me. I'm not sure I really understand how the problem is manifesting itself - are you saying you start up with the desktop CD but it never logs you on, so you never get to start the installation proper? And this is so even in safe graphics mode?

There is no mouse support at the first boot screen when starting from the Ubuntu CD.

What happens if you press CTRL and ALT and F1 when the login has failed - you should be able to get to a black screen with a command-line logon prompt. (CTRL and ALT and F7 would take you back to the GUI logon screen, it it was working).

A thought - have you tried the alternate installation CD? (separate download - sorry). This often succeeds in installing on systems that have trouble with the desktop CD.

---

### Post by .nedberg on 2008-05-01
> **Aearenda said:**
> 
A thought - have you tried the alternate installation CD? (separate download - sorry). This often succeeds in installing on systems that have trouble with the desktop CD.

Yeah, if you have problems with the desktop CD, try alternate! It is just as easy to use. And dl 8.04 instead of 7.10 (you could actually try 8.04 desktop first, then alternate if you have the time and disks).

---

### Post by thomasyo on 2008-05-04
Well well well, tried slower burning and a friends cd and neither worked. so i d/l hardy and it all works a treat. thanks for the help guys.

---

