---
title: "Installation problem on ThinkPad 600e"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by pchernik on 2006-11-21
Hi All,

I'm trying to install Ubuntu desktop 6.10 or 6.06 (tried both) on my ThinkPad 600e, but running into the following issue:

I put in the CD, wait for it to boot up to the initial menu, and select "Start or install Ubuntu".

Eventually it gets me to the graphical desktop and I double-click on "Install" to start the installation.

After a couple of minutes I see a blank "install" window, and hard disk and cdrom lights are flashing (something is happening)... After about 5 more minutes the whole thing freezes.

](*,) 

Any ideas / suggestions are appreciated.

Thanks,
-Pavel

---

### Post by king20878 on 2006-11-21
Hi Pavel,

I had the same problem on my 600e.  Download the alternative install CD and use text mode to install.  I didn't have any problems after that.

You'll run into the same issues setting up the sounds as in the past, but the procedure that worked with Dapper works with Edgy as well.  Video playback is MUCH better after the switch to the new gstreamer.  All in all I think Edgy is a nice improvement for the average 600e owner out there.  :) 

- Jeffrey

---

### Post by pchernik on 2006-11-21
> **king20878 said:**
> Hi Pavel,

I had the same problem on my 600e.  Download the alternative install CD and use text mode to install.  I didn't have any problems after that.

You'll run into the same issues setting up the sounds as in the past, but the procedure that worked with Dapper works with Edgy as well.  Video playback is MUCH better after the switch to the new gstreamer.  All in all I think Edgy is a nice improvement for the average 600e owner out there.  :) 

- Jeffrey

Hi Jeffrey,

Thanks for the reply! I will be trying that next (after Red Hat installation is done and I Ghost it just in case :-? )

Did you have any issues with pcmcia network card? I have a 3com one and it seems that it's being recognized by Ubuntu, but I keep getting "destination unreachable".

Thanks,
Pavel

---

### Post by king20878 on 2006-11-21
I use an atheros based pcmcia network card and I need to include: "*pci=noacpi acpi=off pnpbios=off*" in the kernel parameters for it to work correctly.  

Without these settings, setting the card up is confusing, because it will power up and appear under iwconfig, but it won't be able to connect to anything.

I don't know if you need ndiswrapper to get that card to work, but edgy ships with a nice gui tool for doing that.

Good luck and let me know if you have other questions.  I've been using the 600e under Ubuntu for about a year and a half now, so I've seen just about everything. ;)

---

### Post by pchernik on 2006-11-21
> **king20878 said:**
> I use an atheros based pcmcia network card and I need to include: "*pci=noacpi acpi=off pnpbios=off*" in the kernel parameters for it to work correctly.  

Without these settings, setting the card up is confusing, because it will power up and appear under iwconfig, but it won't be able to connect to anything.

I don't know if you need ndiswrapper to get that card to work, but edgy ships with a nice gui tool for doing that.

Good luck and let me know if you have other questions.  I've been using the 600e under Ubuntu for about a year and a half now, so I've seen just about everything. ;)

It's working! **Thanks for your help**!!!

-Pavel

---

### Post by king20878 on 2006-11-21
Glad I could help!  :)

I think we need to start a 600e support group.  I don't think mine is going to die anytime soon.  They built this thing like a tank.  Look me up if you ever have a question.

---

### Post by kebajonathan on 2006-11-22
I didn't have time to update it, but that's for 6.06 on tp 600E:

[http://www.mueller.ch.vu/misc/tp600e_en.html]("http://www.mueller.ch.vu/misc/tp600e_en.html")

have fun, Linux on the 600E perform great!

---

### Post by king20878 on 2006-11-22
> **kebajonathan said:**
> I didn't have time to update it, but that's for 6.06 on tp 600E:

[http://www.mueller.ch.vu/misc/tp600e_en.html]("http://www.mueller.ch.vu/misc/tp600e_en.html")

have fun, Linux on the 600E perform great!

Hi Jonathan,

That's a very nice howto.  Thanks for writing it!

- Jeffrey

---

### Post by tekno62 on 2007-02-07
> **king20878 said:**
> Hi Jonathan,

That's a very nice howto.  Thanks for writing it!

- Jeffrey



Very good how to. I sent you link to a friend thats trying Ubuntu on his 600E - He will be installing Edgy tho. whould you have any pointers for him or would your How To work?

---

