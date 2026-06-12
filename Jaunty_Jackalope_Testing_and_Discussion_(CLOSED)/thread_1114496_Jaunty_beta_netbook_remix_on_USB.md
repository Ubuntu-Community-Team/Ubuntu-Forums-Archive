---
title: "Jaunty beta netbook remix on USB"
date: 2009-04-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dndrich on 2009-04-02
Ubuntupals:

I am downloading the netbook remix USB disk image for Jaunty to try on my Dell Mini 9.  I've heard great things.  How do I install it on the USB drive?  Do I just format the drive and drag it over?  Or do I need to do something else?

---

### Post by blackened on 2009-04-02
Nope, just dragging and dropping isn't going to work. Check out unetbootin ([http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/"))if you're using Windows. If you're using Ubuntu already on another machine and have the NBR image on that machine, then you can use System -> Administration -> USB Startup Disk Creator.

---

### Post by dndrich on 2009-04-02
OK, but I thought that was for putting a cd image onto a usb drive.  I have done that successfully with intrepid.  But this time I have downloaded an image that claims to be a usb image.  Do I still need to use the make a usb startup disk option in Ubuntu with this image?

---

### Post by Sef on 2009-04-02
Moved to Jaunty Forum.

---

### Post by xzero1 on 2009-04-02
I don't know if the usb startup disk creator applies here. The recommended procedure is described here [https://wiki.ubuntu.com/MobileTeam/Mobile/HowTo/ImageWriting](https://wiki.ubuntu.com/MobileTeam/Mobile/HowTo/ImageWriting)

---

### Post by dndrich on 2009-04-03
Yup.  USB starter disk is not the one.  The program above is the one for putting an image on a USB drive.  I did it successfully.  Unfortunately, doesn't look like it will boot.  It brought up the ubuntu splash screen when booting to usb, but then it brought up busybox, some kind of built in shell.  Doesn't go to the graphical user interface for some reason.

---

### Post by blackened on 2009-04-03
> **dndrich said:**
> Yup.  USB starter disk is not the one.  The program above is the one for putting an image on a USB drive...

Yeah sorry, I forgot that the UNR download is an img file and not an iso like everything else.  I just use the regular Jaunty install on my netbook.

> **dndrich said:**
> ...I did it successfully.  Unfortunately, doesn't look like it will boot.  It brought up the ubuntu splash screen when booting to usb, but then it brought up busybox, some kind of built in shell.  Doesn't go to the graphical user interface for some reason.

Can you manually start the xserver?  Try *startx* at the prompt.

---

### Post by dndrich on 2009-04-03
I reformatted my USB drive, reinstalled the image, and now it works!  Not sure I'm crazy about the remix though.  Think I'll stick with classic...

---

### Post by raymondh on 2009-04-03
> **dndrich said:**
> Yup.  USB starter disk is not the one.  The program above is the one for putting an image on a USB drive.  I did it successfully.  Unfortunately, doesn't look like it will boot.  It brought up the ubuntu splash screen when booting to usb, but then it brought up busybox, some kind of built in shell.  Doesn't go to the graphical user interface for some reason.

dndrich .... I followed this guide using 9.04 UNR.  Am currently trying it out (live session) on my MSi Wind as I type.  Have not yet FULLY decided whether to install though am leaning towards UNR at this point whilst I search the forums for more learnings. 

[https://wiki.ubuntu.com/UNR?action=show&redirect=unr#Installation](https://wiki.ubuntu.com/UNR?action=show&redirect=unr#Installation)

When I first booted, Disk integrity check revealed 1 error.  I just went ahead and booted and got the usual splash, etc.

Maybe you'll need to re-write the image?

BTW, Wifi (rtl8187se) / fn+keys / webcam / touchpad / volume / keyboard  ... works for me.

Hope this helps.

Quick question to the group.  Current Ubuntu install is 8.10 intrepid.  UNR wiki says to use the latest 9.04.  If i do install through network/synaptic, will it match?

Raymond

---

### Post by blackened on 2009-04-03
I like the netbook interface alot, but it just so happens that when I went to download it the servers were so bogged down that I couldn't get more than 4 or 5 k/s, so I had the option of grabbing the beta torrent or installing from an alpha 3 iso already on my machine.  I opted for the former.

I wonder why all available downloads aren't offered as torrents.  Seems a smart thing to do, especially on server-intensive release or semi-release days.

---

### Post by DecIRC on 2009-04-05
[QUOTE=raymondhenson]

BTW, Wifi (rtl8187se) / fn+keys / webcam / touchpad / volume / keyboard  ... works for me.

Hope this helps.

[/QUOTE]

I've tried but unable to make the webcam. Even with Fn-F6
But the rest is ok for me on my MSI Wind U100 :(

---

### Post by Salkin on 2009-04-11
Okay, but shouldn't Jaunty be able to use a USB image to create a USB Startup Disk with its USB Startup Disk Creator? Seems silly not to.

Or perhaps Canonical could make an .iso image of it as well.

---

### Post by vahnx on 2009-04-15
> **blackened said:**
> 
Can you manually start the xserver?  Try *startx* at the prompt.

I am encountering the same busy box error. Tried startx to no avail. I booted into it fine the first time I tried it, but today when I wanted to use the USB Live Stick, it booted into Busy box and now that's all it's booting to!

---

### Post by TomRod on 2009-04-21
I'm getting the same error. If the USB stick is small, does that cause this?

---

