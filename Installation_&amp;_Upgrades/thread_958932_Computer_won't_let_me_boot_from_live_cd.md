---
title: "Computer won't let me boot from live cd"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by senor.ehlert on 2008-10-25
Hello,

I am having a problem when first booting up with ubuntu. I have installed wubi on my laptop (to see if I like it) and I would like to install ubuntu with a dual boot on my desktop. However, unlike my laptop when I put the in the cd (which is just the iso which I downloaded and burned) and reboot it wouldn't automatically boot from the cd. I don't really know my way around bios too well, so I kind of stumbled around and turn the primary master from IDE to CDROM. As far as I know it should boot from the cd, right? But during start up it says "Primary Master Drive - ATAPI Incompatitble."

What does this mean? Should I make a new cd or did I not change the right bios settings? 

Thanks for the help.

---

### Post by overdrank on 2008-10-25
> **senor.ehlert said:**
> Hello,

I am having a problem when first booting up with ubuntu. I have installed wubi on my laptop (to see if I like it) and I would like to install ubuntu with a dual boot on my desktop. However, unlike my laptop when I put the in the cd (which is just the iso which I downloaded and burned) and reboot it wouldn't automatically boot from the cd. I don't really know my way around bios too well, so I kind of stumbled around and turn the primary master from IDE to CDROM. As far as I know it should boot from the cd, right? But during start up it says "Primary Master Drive - ATAPI Incompatitble."

What does this mean? Should I make a new cd or did I not change the right bios settings? 

Thanks for the help.

Hi and you can try and go back to bios and undue the change that you made on the primary master and just change the boot order to cd drive first.

---

### Post by senor.ehlert on 2008-10-25
I changed everything back and changed the boot sequence.

It says it is searching for a boot record from CDROM and the light on my cd drive turns on, but after about 10-15 secs the light turns off and it starts to boot in windows.

---

### Post by gpsmikey on 2008-10-25
How did you burn the ISO to the CD ??  The ISO file is an "image" of a real CD.  If you burned the ISO to the CD like a normal file, you ended up with a data CD that has a file on it ending in the .iso -- you need to use a utility that will actually use the ISO to make a CD.  If you are running under windows, check out the free imgburn utility -- I use it all the time and it works very well.  When you install it, it adds an entry to the context menu for you -- browse to where you saved the ISO file, **RIGHT click **it and select "burn with imgburn" or something to that effect.  On the other hand, if I misread your post and you did burn it correctly, then I'm not sure why it will not boot from it at this point.

[http://www.imgburn.com/](http://www.imgburn.com/)  <--- the home page of Imgburn

mikey

---

### Post by senor.ehlert on 2008-10-26
The cd had worked before, but only once (and then it froze and I was never able to get it to work again). I did try using the imgburn though. The result was the same.

Anybody have any ideas? Is there another way to partition my HD and install ubuntu?

---

### Post by gpsmikey on 2008-10-26
Well, the next thing I would do in troubleshooting is figure out if it is a problem with your system (or cdrom) or with the CD.  See if you can find another machine to try the CD in.  Also see if you can find another CD of some sort that is bootable and see if it boots in your system.  That should give you some better ideas as to where the problem is.  As it is right now, it is not clear if the problem is with the CD or something in your system is preventing it from booting.

mikey

---

