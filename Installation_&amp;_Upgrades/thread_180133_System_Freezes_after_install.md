---
title: "System Freezes after install"
date: 2006-05-21
forum: Installation &amp; Upgrades
---

### Post by Galactus on 2006-05-21
I have been trying unsuccessfully to install Kubuntu on an old Gateway GP7-600 [http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)
](*,). It is a PIII 600 MHz with 384 Megs Ram. I am not sure of the motherboard type (how would I tell without taking the machine apart). The installation seems to work fine all the way to the end. When it appears that the install is complete the screen goes black except for a non-blinking cursor in the upper left corner. After waiting a few minutes to see if anything would happen, I pressed alt-ctrl-F3. Something boots ("Ubuntu 5.10 Breezy Badger ubuntu tty3") and I am prompted to login (non GUI interface - looks like command line interface). I login with user name/password and get a command prompt...It never finishes booting to the desktop. 

Edit:

[B]This is what I am getting:

Fatal Server error:
Server is already active for display 0
     If this server is no longer running, remove /temp/.X0- lock and start again

Please consult the X.Org Foundation support at [http://wiki.X.org](http://wiki.X.org) for help

Xlib: connect to "0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key, giving up
xinit: unable to connect to X server
xinit: No such process (errno3): server error
"command prompt":~$[/B]

I wiped the HD on friday night. It had Ubuntu loaded on it and I wanted to remove it and install Kubuntu. I downloaded Kubuntu 5.10 and burned it to a CD and began trying to load it but to no avail. 

Like I said above, I have had Ubuntu 5.10 running on this computer, however I had previously loaded Ubuntu on the HD when it was in a Dell PC, I then moved the HD into this Gateway Desktop and it has run fine for the last several weeks. I also switched monitors. I had a Viewsonic 17"LCD connected up until Thurs night. I then switched back to my 3 year old HP f1703 LCD (which is a replacement for the original one that I had that went bad and had to be replaced...but that is another storyhttp://ubuntuforums.org/images/smilies/icon_evil.gif
:evil:). So since the new monitor, Ubuntu won't install completely or boot. (I would hate to think that just changing the monitor would cause this big of a problem - that might mean I need to switch to SuSe or some other distro...hmmmhttp://ubuntuforums.org/images/smilies/eusa_think.gif
:-k) 

Anyway if someone can give me a hand or pass on some info I would be most appreciative.[http://ubuntuforums.org/images/smilies/icon_razz.gif](http://ubuntuforums.org/images/smilies/icon_razz.gif)
:p

---

### Post by Sef on 2006-05-27
Sounds like a bad install.

1) Did you md5sum?

2) Can you reburn the disk?

3) Try a live cd and see what happens.

---

### Post by Galactus on 2006-05-27
I downloaded and burned a copy of the live cd for Kubuntu. That would not load completely or work. Evidently (K)Ubuntu has a problem with my graphis card (Old ATI card in a PIII Gateway). I tried Vesa, ATI and several other graphics settings (I did a sudo dpkg-reconfigure xserver...etc...) to no avail. I was able to get Mepis loaded on the machine but am having different problems with that. I am hoping that someone can help me out because I really would prefer to run Kubuntu. I installed Ubuntu on a Dell that I had and loved it so I would like to go with (K)Ubuntu as the distro that I learn on (I am a noobie to Linux). 
I hope someone can help me out....

---

