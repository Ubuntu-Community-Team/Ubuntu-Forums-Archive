---
title: "Screen Resolution set WAY low - can't reset!"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by WSC on 2008-05-05
Hello...
I have the new version installed as of a couple of days ago (sorry I can't look to see which one it is, I can't see the screen!) Every thing was great and then I decided to try the lowest screen resolution, like 320x?. Now I can't see anything but the top right corner of the screen and I can't get back to change the resolution to a usable size. As Ubuntu loads I see the left top of the screen, but by the time it's done it changes to the right and I can't get back to 'System'.  I have tried to use the terminal and edit the file in 'Vi', but the file only says:"Configured Monitor", "Configured Video Device", etc - are the specifics actually configured somewhere else?  I'm lost.  
Any ideas?

WSC

---

### Post by gdelta9 on 2008-05-05
Insert the ubuntu installation dvd,
Boot system in recovery mode(or whatever is called) and then choose option
"Try to fix X server"
That would bring your screen to your very first settings

---

### Post by WSC on 2008-05-05
> **gdelta9 said:**
> Insert the ubuntu installation dvd,
Boot system in recovery mode(or whatever is called) and then choose option
"Try to fix X server"
That would bring your screen to your very first settings

I was able to access this "Try to fix" screen from the Ubuntu login screen, which still comes up in it's original resolution. I did the "Try to fix X server" and it seemed to run. It didn't do anything, however.  I downloaded the current Ubuntu version straight from the Internet to my old desktop ~ no CD involved. I might be able to find the CD for the last version, but it would most likely be incompatible. I think I'm still stuck.

---

### Post by gdelta9 on 2008-05-05
well im not sure if this is the case but at loggin screen press
ctrl+alt+F2 then loggin and go to /etc/x11 there should be the xorg.conf file.See if there is an xorg.conf.1(or xorg.conf1) or an xorg.conf~ file.Replace the original one with one of those backup cofiguration files

---

### Post by WSC on 2008-05-05
I'm off to give that a try... 

Thanks Gdelta9

Nope sorry, no change.
Bummer... It's a long task to download the whole CD again!

---

### Post by WSC on 2008-05-05
I'm pretty sure I'm going to have to fix this by editing something at the command line, but xorg.conf doesn't seem to hold the information it should and my 'Vi' skills are REALLY rusty. (I was using Unix in the mid 90's I think) Anybody understand how to access the correct file at the command line?

WSC

---

### Post by Girya on 2008-05-05
I'm struggling with screen res right now too. you can try the xorg reconfigure editor its worked for me in the past. most default setting are fine then you can change the screen resolution from there. 

1 log into a term by pressing ctrl+Alt then F2 
after you log in type this:
> 
 sudo dpkg-reconfigure xserver-xorg

that command opens a graphical interface to edit xorg.conf file

good luck kevin

---

### Post by WSC on 2008-05-05
Thanks Kevin, although I'm not sure what we did...
When I put in your above command I got a tiny little 2" x 2" configuration screen (on my 20" monitor, itty bitty little characters!) for KEYBOARD which asked about 6 or 7 keyboard questions and then ended.  Upon reboot the system didn't make it to the graphical interface before it came up with a screen with an "X" cursor and some really funky looking graphical characters. It said I was in 'low res' mode and asked if I wanted to change it. I said 'Yes' and it now gives me 640 x 480 and 800 x 600. This is a great improvement! Now I have to figure out how to have the thing rescan the possible resolutions so I can get back to 1280 X 1024.  Thanks again.
WSC

Went back and got into the system and checked the video card (NVidia) which was running without an NVidia driver. Followed the directions and downloaded it (warnings about non-GNU software interrupted). I not only have all my resolutions back but as screens pop up they grow from small to large, sort of 'grow' into place. Cool.  Thanks to everyone for their help. I'm back up and running.

WSC

---

