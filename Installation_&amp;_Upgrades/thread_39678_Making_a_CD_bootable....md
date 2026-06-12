---
title: "Making a CD bootable..."
date: 2005-06-06
forum: Installation &amp; Upgrades
---

### Post by xmastree on 2005-06-06
I downloaded the iSO for the 5.04 installer, but when I made the CD I found a couple of files were corrupted. It's not a bad burn, it's the ISO file itself.

All that was missing were some korean font( no big deal) and xscreensaver, which I installed from my 4.10 CD. I've since downloaded a working version of xscreensaver, and would like to make myself a new CD with the good file.

I can copy everything to a directory and replace the file in question, but how do I then burn that CD so that it boots?

---

### Post by mingus on 2005-06-06
What makes a CD bootable is a binary, usually specific to the application that is on the CD, written to a reserved location on the disc.  You will not see the file in this sector.

To create an Ubuntu bootable CD requires that you can (1) pull this binary either off another bootable CD or out of the .iso file, and that you (2) know how to give the burner a hexidecimal offset and binary size so it will know where to place it.

I'd advise youto download the .iso again, do an MD5 check, burn as image.

---

### Post by xmastree on 2005-06-07
[QUOTE=mingus]I'd advise youto download the .iso again, do an MD5 check, burn as image.[/QUOTE]That's easy for you to say. I'm having major problems downloading it.

Getright turns into Getwrong with large files like this, and bittorrent doesn't seem to work at all. I got my current one from someone on a file sharing network, but he's not around any more...

 ](*,) 

I think I'll just stick with it like it is for now. after all, it's working.

Thanks.

---

### Post by C.B. on 2005-06-07
Can you not just download the ubuntu-5.04-install-i386.iso? If you're using Firefox, the program's download controller will let you resume interupted transmissions if you're having difficulty that way.

Also, you could just order the free install CD from Ubuntu and wait a few weeks.

P.S. Have you checked out "Burning/writing an .iso Image to CD with Windows XP" at [http://www.ubuntulinux.org/wiki/BurningIsoHowto](http://www.ubuntulinux.org/wiki/BurningIsoHowto) ?

---

### Post by xmastree on 2005-06-07
[QUOTE=C.B.]using Firefox, the program's download controller will let you resume[/QUOTE]Thanks, I didn't know firefox could resume an interrupted download. I'll try that.

---

### Post by xmastree on 2005-06-08
I was right. Firefox can't resume an interrupted download.
 :| 

Whatever happened to good old-fashioned ftp?

---

### Post by bored2k on 2005-06-08
[QUOTE=xmastree]I was right. Firefox can't resume an interrupted download.
 :| 

Whatever happened to good old-fashioned ftp?[/QUOTE]
 I would recommend downloading the image using a Bittorrent client. It is safer as the file gets checked regularly for errors and IF found any, get fixed automatically.

---

### Post by xmastree on 2005-06-08
Well, bittorrent seems to be working today... Although I've been trying for over a week to get that. Let's see if I can complete it this time.
 ](*,)

---

### Post by bored2k on 2005-06-08
[QUOTE=xmastree]Well, bittorrent seems to be working today... Although I've been trying for over a week to get that. Let's see if I can complete it this time.
 ](*,)[/QUOTE]
 Port forwarding is the key.

---

