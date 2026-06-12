---
title: "Video-related issues on install of 6.10"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by dvord on 2006-10-27
Hullo there.

I started Ubuntu at 6.06 and had some issues with the video (I wanted 1280X1024), and of course I crashed X trying to fix it.  I wasn't particularly married to that installation and picked up 6.10 today.

To start with, just beginning the CD load was a problem.  The installer tried to use a screen resolution that didn't play with my LCD monitor. I got an out of synch error on the monitor's OSD menu.

I hit F4 at the CD load menu to select a different startup resolution.  I selected 1280X1024 (which is what I run Windows at), and I got a bizarre resolution with half a screen and really fine lines doubled up over and over.  At least I didn't get an out of synch error...

So I tried loading up again at 1024X768, so far so good, I could see the desktop fine...

No mouse cursor.

I think this is more video problem than mouse problem, because as I moved the mouse, the tooltips over certain areas would come up so there was a mouse cursor but it was playing halloween hiding games.  

I have an Nvidia GeForce 6600 GT/128MB, and a KDS 915-S LCD monitor.  

I can manage a bit without a mouse cursor but it'd be helpful to have it during install, then maybe I can figure the rest out.  Any suggestions?

---

### Post by dvord on 2006-10-28
Bumping my own thread.  Silly, I know, but I'm ](*,)

---

### Post by stream303 on 2006-10-28
Let's try the simple stuff - what is your monitors "native" resolution?

You can try the generic nv driver and set your resolution like this from a terminal:

sudo dpkg-reconfigure -fgnome -phigh xserver-xorg

Perhaps reboot or log in/out to restart gdm...

---

### Post by dvord on 2006-11-01
Hey thanks for the tips!

I have no idea what the "native" resolution of the monitor is.  AFAIK you plug it in, and it displays the resolution given.  Never a problem with Windows, so I honestly can't tell you. It's supposed to be at least XGA so 1024X768 SHOULD work.  I use 1280X1024 in Windows, so I would think it should work as well.

Regarding the driver, which turned out to be the problem, I followed the advice in this thread; [http://www.ubuntuforums.org/showpost.php?p=1680332&postcount=6](http://www.ubuntuforums.org/showpost.php?p=1680332&postcount=6)

Which turned out to be precisely what I needed to fix the problem.  Not only am I running but I am now running in the resolution I wanted to run in.

I would definitely advise folks to go with the Alternative install CD.

---

