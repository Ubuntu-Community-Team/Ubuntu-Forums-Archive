---
title: "gnome and keyboard lockup on login"
date: 2008-08-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by centyx on 2008-08-15
I just did a fresh install ( guided partioning, entire hard disk, otherwise default install ) of alpha 4 onto a Dell Dimension 2400 w/ 512mb of ram. 

After logging in via GDM, I see a tan background and am able to move the mouse, but am unable to use the keyboard - I've tried hitting CTRL-ALT-Backspace to kill X. Even caps/numlock do nothing.

If I choose the Failsafe Gnome session, when logging in I see the desktop wallpaper instead of just tan, but the keyboard still "goes away", and no windowmanager/panel or anything else seem to load.

I've let it sit for approx. 10 minutes just to see if gnome would load.

I tried creating ~/.config/xserver-xgl/disable just in case I was having issues with xgl ( I have in the past ), but this didn't help.

Finally I tried logging in to the machine via SSH and killing off X, but the display just turns to blue and green stripes until I shut the system down.

I logged into a virtual console and installed openbox, chose OpenBox Session in GDM, and was then able to login without any issue. 

Here is my [.xsession-errors]("http://www.centyx.net/xsession-errors.txt").

Has anyone else experienced anything similar to this?

Thanks!

---

### Post by grumpymole on 2008-08-15
There are some other threads about USB keyboards and mice not working.  If this is your case, then you will need to add two lines to xorg.conf to get them working again.

Just look around here for threads about USB keyboards not working.

cheers

---

### Post by Slug71 on 2008-08-15
Try CTRL + ALT F1 at boot to go straight to terminal, your keyboard should work, type 
sudo apt-get update
sudo apt-get upgrade

and it should work

---

### Post by Nullack on 2008-08-16
Sounds like your repo mirror is way out of date. Hit canonicals directly and see what updates you get

---

### Post by centyx on 2008-08-16
Thanks I'll try that. FWIW this is a PS/2 keyboard.

---

### Post by centyx on 2008-08-18
I logged in via vc and ran sudo apt-get update && sudo apt-get dist-upgrade, rebooted, but still the same result. 

My apt sources are using us.archive.ubuntu.com. Should I be using  

Any ideas what else may be the matter?

Thanks!

---

### Post by Nullack on 2008-08-18
Try the main archive not a mirror

---

### Post by centyx on 2008-08-18
> **Nullack said:**
> Try the main archive not a mirror

Sorry, what is the address for the main archive?

archive.ubuntu.com and us.archive.ubuntu.com resolve to the same 3 addresses.

---

### Post by Nullack on 2008-08-18
Oh, I didnt know that :) Thats interesting. Yes the "main server" as reported in the software sources GUI is archive.ubuntu.com

There was recently some X love but clearly its not helping you.

I recommend starting up a bug report on X, using this as a guide:

[https://wiki.ubuntu.com/X/Debugging](https://wiki.ubuntu.com/X/Debugging)

It also has some info on how to debug X some more yourself.

Bryce on the Ubuntu X mailing list sent out notice of a new script that easily grabs all the info his group needs for debugging:

*******************************

Heya all,

We now have a simpler way for reporting xorg bugs:

   $ apport-cli -f --package xorg

It auto-collects all the junk we like for debugging.  :-)

You can also specify some of the other common X packages instead of
'xorg'.  For example:

   $ apport-cli -f --package xserver-xorg-video-ati

So if you need to report bugs, or if you're triaging bugs and need to
suggest someone file separate bugs or something for Intrepid, please
consider suggesting the above command.

Bryce

---

