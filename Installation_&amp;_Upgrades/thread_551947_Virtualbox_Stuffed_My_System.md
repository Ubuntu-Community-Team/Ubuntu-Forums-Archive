---
title: "Virtualbox Stuffed My System"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by treeko11 on 2007-09-15
Hello everyone,

Ok, last night i tried to install virtualbox, so ii downloaded the deb file and ran it, so i thought it was just gonna install all by itself but it didn't, it need an input by me, i didn't know this at the time so i went away and left it to install.

I came back only to find it had made no progress, so i went show console and it wanted me to press ok, i tried to press ok but it didn't work, SO i closed the install thing, which was a bad idea. I couldn't close the actual Gdebinstaller thing so i continued. I then turned off my computer by holding down the button.

I woke up this morning to find that i can't update, i can't use apt-get and i can't use synaptic because i get this error
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'

So i downloaded the deb again but now it says that i can't access it becuase of permissions or something...

Any Ideas?

---

### Post by gali98 on 2007-09-15
It could be a couple of things...
First you may have locked apt by powering off.

Open up that terminal and try

sudo rm /var/cache/apt/archives/lock

I think that's all you have to do. Try that and see if you can open synaptic.
if the same thing happens again try this...

sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/aptitude/lock
sudo rm /var/lib/dpkg/lock
sudo rm /var/lib/apt/lists/lock
sudo dpkg --configure -a

It could also be that you don't own the file.
You could try..
sudo chown bob file
with bob being your username and file being the deb.
I don't think that would be the problem, but who knows.
I'm kinda new too, so You might wait until someone else posts to make sure I'm right. Hope this helps,
Kory

---

### Post by treeko11 on 2007-09-15
thanks for the help but none of that worked =(

---

### Post by Pumalite on 2007-09-15
Try:

sudo dpkg --remove --force-<packagename>, if not:

sudo apt-get remove --purge <packagename>

---

### Post by treeko11 on 2007-09-15
ok, im doing this now, lets hope it works!

---

### Post by treeko11 on 2007-09-15
W00T! sorry for DP but, that you sooooo much, i can now use my computer again! YAY ^_^

---

### Post by Pumalite on 2007-09-15
I'm glad you got it working.

---

