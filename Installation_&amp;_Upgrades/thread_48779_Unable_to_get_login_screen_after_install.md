---
title: "Unable to get login screen after install"
date: 2005-07-13
forum: Installation &amp; Upgrades
---

### Post by wizer on 2005-07-13
I am newbie to linux & ubuntu. i seem to have successfully installed hoary on my laptop (dual boot with XP).  However, after it boots up & gives me some messages that it was starting/loading ok, my screen is blank and I am unable to get a login screen.  When I power off, I get a text msg

"home login:_ "

before the laptop shuts down.

Does anyone know how this problem can be solved?

---

### Post by wizer on 2005-07-13
I found the answer under blank screen problems

had to edit my driver from i810 to vesa

---

### Post by dragoons on 2005-07-17
how did you edit this?  i'm having the same problem. and i'm not sure how to do that.

---

### Post by wizer on 2005-07-18
open the root terminal (sorry cant give u detailed steps bec i am in xp now: my adsl prob)
it can be found in the left hand menu (you'll need to type in your pw)

once you are there, at the # prompt

type sudo gedit /etc/X11/xorg.conf

I suggest you do a save of the file as a backup first.

You can then search for i810 & replace that with vesa


Andrew

---

### Post by wizer on 2005-07-18
Oops! forgot u cant get into ubuntu yet.

You'll need to start under recovery mode. Then edit by doing

nano /etc/X11/xorg.conf

(not sure how you can do backup. I guess you could try cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak)

Then search for device section and replace the i810 with vesa

Good luck

---

### Post by mingus on 2005-07-18
And in the event that the video driver is preventing you from getting in with the Recovery option, you can also boot from the install CD with :rescue - you will be asked which partition root (/) is on, that will be mounted, and you will be dropped into a shell.  From there you can use a text editor to make the change.  

Note:  Not positive, but I think vi is the only editor avail in this shell.  If you don't know vi, you can do Ctrl-Alt-F1 to get into a diff shell where you can use nano, which is very simple.  Be sure to make a backup copy first as was suggested.  After you've made the change, umount the partition before you reboot.

---

### Post by damonw5 on 2005-07-18
[QUOTE=wizer]Oops! forgot u cant get into ubuntu yet.

You'll need to start under recovery mode. Then edit by doing

nano /etc/X11/xorg.conf

(not sure how you can do backup. I guess you could try cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak)

Then search for device section and replace the i810 with vesa

Good luck[/QUOTE]
 One quick thing, you need to type sudo first:

sudo nano /etc/X11/xorg.conf

Do your replacing and then hit CTRL+X. When it asks you if you want to save, hit Y. Then reboot!

---

### Post by varunus on 2005-07-18
The vesa driver is not very good; it provides no hardware acceleration.  I would recommend you use the i810 driver.  There's a howto on compiling the newest version of it (that fixes some bugs, works with more cards) in the "Hoary Tips and Tricks" section of the forum.

Good luck.

---

