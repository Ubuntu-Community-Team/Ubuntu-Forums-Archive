---
title: "Installing Ubuntu without CD"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by Ethan McWinston on 2010-10-07
Dear Ubuntu users,

I am dealing with a problem which I cannot seem to fix myself.
I have a computer (age ~1 year) on which I am trying to install Ubuntu.
The problem which I am facing is at the point of choosing to boot from the CD it says 'cannot find bootable device'.

Note that this PC does not have a floppy drive and that I do not have a 1GB USB stick. I do have a 256MB USB stick.

Does anyone have a solution for me to install Ubuntu?

Help is much obliged. :)

---

### Post by rob_l_f on 2010-10-07
It seems that the first thing to do is to figure out why you can't boot from your CD drive.  Will the CD you made boot on another machine?  Can you boot from any other bootable CD in that drive?

There is such a thing as installing ubuntu over a network, but I wouldn't recommend that straight away.  Perhaps you can buy a new memory stick?

---

### Post by viralmeme on 2010-10-07
> **Ethan McWinston said:**
> Does anyone have a solution for me to install Ubuntu?

Try [UNetbootin]("http://unetbootin.sourceforge.net/")

---

### Post by Ethan McWinston on 2010-10-07
> **rob_l_f said:**
> It seems that the first thing to do is to figure out why you can't boot from your CD drive.  Will the CD you made boot on another machine?  Can you boot from any other bootable CD in that drive?

There is such a thing as installing ubuntu over a network, but I wouldn't recommend that straight away.  Perhaps you can buy a new memory stick?
The CD boots on other machines. I've just tried a Kubuntu CD but that also doesn't boot, same error message.

---

### Post by Ethan McWinston on 2010-10-07
> **viralmeme said:**
> Try [UNetbootin]("http://unetbootin.sourceforge.net/")
I've read some of the articles/tutorials using a USB stick, but the USB stick I've got only has 256MB.

---

### Post by NightwishFan on 2010-10-07
Does the pc in question have a wired network connection? Then install a minimal cd on the usb drive (not sure if this is possible, perhaps just use the built in Ubuntu USB Creator, or Unetbootin and see if it has a minimal option, if not treat it as the alternate cd). I advise the Ubuntu Startup Disk Creator over Unetbootin, unless you only have Windows.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by viralmeme on 2010-10-07
> **Ethan McWinston said:**
> I've read some of the articles/tutorials using a USB stick, but the USB stick I've got only has 256MB.

"**UNetbootin** can create a bootable Live USB drive, or it can make a "f**rugal install**" on your local hard disk if you don't have a USB drive. It can load distributions by automatically downloading their ISO (CD image) files, or by **using existing ISO files**" [link]("http://unetbootin.sourceforge.net/")

---

### Post by NightwishFan on 2010-10-07
Update!

On Maverick, the Ubuntu Startup Disk Creator ignores the mini iso. It may work for lucid, its worth a shot.

I will try unetbootin now.

Edit: Unetbootin, choose the mini iso, and target the flash drive. It was a little buggy to boot, but it loaded the installer fine. I did not test the install, so proceed at your own risk, though I see no reason why it would not work. Note you do need a network connection through a wire to use the minimal cd.

---

### Post by Rasa1111 on 2010-10-07
no friends/family members with a larger USB stick you can borrow?

---

### Post by Ethan McWinston on 2010-10-07
Thanks for the feedback guys!:)
I've just tried UNetbootin with Damn Small Linux. When I were selecting Removable Device there was this error message "No bootable device found".

**Update:**
Under 'harddisk'  I found my USB key. It's is doing something now, will let you know soon. 

**Update 2:**
I am now running DSL, what should I do now?

---

### Post by Rasa1111 on 2010-10-07
why did you get DSL?
because it fit on the stick?
sorry, maybe im just confused..
but what are you trying to do now that you have DSL?

---

### Post by Ethan McWinston on 2010-10-07
> **Rasa1111 said:**
> why did you get DSL?
because it fit on the stick?
sorry, maybe im just confused..
but what are you trying to do now that you have DSL?
I wanted to see if something would boot from USB. Now I know booting from USB works I can try something else. Could you recommend me a distro which also fits on my USB key?

---

### Post by Rasa1111 on 2010-10-07
> **Ethan McWinston said:**
> I wanted to see if something would boot from USB. Now I know booting from USB works I can try something else. Could you recommend me a distro which also fits on my USB key?

ahh, ok cool..
So that's a plus, at least. lol

Well,
 The only other distro(s) Im aware of that would fit on a 256MB stick,
is feather linux~ [http://featherlinux.berlios.de/](http://featherlinux.berlios.de/)
which will allow you to have the OS, and give a little storage space..

 or Puppy Linux~ (without open office)
[http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm)
Open office will put it over 256 MB, but without it, P.L. will fit. 

(personally, I would go with Puppy, between the 2)
But ive never used featherlinux either. 

 I remember when I only had 256 MB of external storage,
I feel for ya. lol

 Maybe try to score a few extra bucks? 
a 4GB stick is pretty cheap today. 

 Wish I could do somethin' else for ya mate. :(

---

### Post by Ethan McWinston on 2010-10-08
> **Rasa1111 said:**
> ahh, ok cool..
So that's a plus, at least. lol

Well,
 The only other distro(s) Im aware of that would fit on a 256MB stick,
is feather linux~ [http://featherlinux.berlios.de/](http://featherlinux.berlios.de/)
which will allow you to have the OS, and give a little storage space..

 or Puppy Linux~ (without open office)
[http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm)
Open office will put it over 256 MB, but without it, P.L. will fit. 

(personally, I would go with Puppy, between the 2)
But ive never used featherlinux either. 

 I remember when I only had 256 MB of external storage,
I feel for ya. lol

 Maybe try to score a few extra bucks? 
a 4GB stick is pretty cheap today. 

 Wish I could do somethin' else for ya mate. :(
I'm going to buy a USB stick today, was about time. :P
Thanks for the help though!:)

---

