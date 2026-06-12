---
title: "Old PC install of Ubuntu - Help!"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by Upside on 2010-01-26
I accidently installed Ubuntu 9.10 on my old Dell Dimension 8100 (128MB RAM) instead of the minimal or alternative CD install. It seems like its "hung up". What's the best way to correct this? Or are there any options... There's nothing on the screen except a mouse arrow.
Please Help. Thanks!

---

### Post by earthpigg on 2010-01-26
> **Upside said:**
> What's the best way to correct this?

i assume there is no vital data on the system?

clean re-install is the easiest/fastest thing to do, if that's what you mean by 'best'. 

if you ***really*** have your heart set on correcting this the geek-tastic way, we can help point you in the right direction. hint: it will involve spending a lot of time looking at nothing but a black screen with white text on it and a blinking cursor.

also: the alternative install will work fine, but you have to make sure you select 'command line only install' at the ubuntu options menu thing. i think you have to press f4 for 'modes' or something and navigate via arrow key to 'command line only install'.... if you don't do that, an 'alternative cd install' results in exactly the same thing as the standard install cd.

---

### Post by kerry_s on 2010-01-26
> **Upside said:**
> I accidently installed Ubuntu 9.10 on my old Dell Dimension 8100 (128MB RAM) instead of the minimal or alternative CD install. It seems like its "hung up". What's the best way to correct this? Or are there any options... There's nothing on the screen except a mouse arrow.
Please Help. Thanks!

i agree just do a new install, but not with ubuntu, with only 128mb ram it will just be barely usable if at all.

---

### Post by earthpigg on 2010-01-26
> **kerry_s said:**
> i agree just do a new install, but not with ubuntu, with only 128mb ram it will just be barely usable if at all.

**_if this is a 70% usage / 30% learning project:_**

it'll be fine. use one of the lightweight WM's or DE's, don't expect the world from it, and pick fast software... ie: chrome instead of firefox.

for the DE/WM, im a fan of LXDE and openbox, personally.

this may be of help to build up from a command line system to something a bit more usable: [http://sites.google.com/site/masonux/home/notes-to-myself](http://sites.google.com/site/masonux/home/notes-to-myself)

**_if this is a 70% learning / 30% usage project:_**

Perhaps consider Arch Linux?


this is all "in my humble opinion", of course ;)

---

### Post by adam814 on 2010-01-26
I'd suggest the above-mentioned "command-line install" and once that's done "sudo apt-get install lxde" should take care of it for you.  It's about the lightest desktop environment you'll find.  Other options I'd recommend if you don't like LXDE are fluxbox (not really a full DE, but very lightweight) or XFCE (middleweight).

---

### Post by djchandler on 2010-01-26
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

It will run on a computer with only 128 MB.

---

### Post by Upside on 2010-01-27
Thanks Everyone for the help!!!! So, I'm going to assume that's ok to simply shut it down and start the install over with the light weight version. It should still boot the same way, yes?

I'm sorry.. I'm a REAL newbie to this arena!!!

---

### Post by adam814 on 2010-01-27
You just have to watch what installation option you choose depending on what you want.  If Ubuntu is going to be your only OS then using the entire disk is safe and will overwrite the previous install attempt.

If you have another OS you need to keep you'll have to do manual partitioning (at least you'll have to select the partitions you already used the last time).

---

### Post by Upside on 2010-01-27
Thanks Adam814! That's great. I had Windows98Me on this PC but looking to completely switch over to LinuxOS to give this PC some renewed life.

Thanks for the help!

---

