---
title: "GRUB menu lost after upgrade to 6.10"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by Norradj on 2006-10-30
After upgrade to Ubuntu 6.10, the pc was restarted. No Grub menu showed up and after some seconds a wiered text mode showed something that looked like memory check. Serious problem?
Not to bad I found out after some ours checking with live cd, forums etc.
The Grub menu could not show up (invisible) but it was still function. The arrow keys was still working and I could boot to ubuntu 6.10 (top) or Windows (bottom). The Ubuntu boot started with the wiered text until it turned to Graphics mode with the progress bar which was normal. Besides that the upgrade went without any problem. 
My guess is that Grub meny when loading call some new driver(!??) which doesnt work on this PC.

Before  this issue I have already upgraded a more modern PC without any problem.

---

### Post by happy-and-lost on 2006-10-30
sudo gedit /boot/grub/menu.lst

Under the timeout there should be something which looks like:

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

If there's no # before the bottom "hiddenmenu" put one in. That may be your  problem.

---

### Post by Norradj on 2006-10-31
Unfortunatly, this is not the case. The menu.lst is ok.
The Grub menu points to a file: splashimage=(hd1,1)/boot/grub/default-splash.xpm.gz
In Grub folder this is a link (which is broken) that points to /usr/share/pixmaps/grub/ubuntu-artwork.xpm which i can't find.
Still my hard guess, the hidden menu and wiered text mode must be related to splashimage and related. Other tips?

---

### Post by beckn on 2006-11-03
I've got the same problem. Did you find any solution?

---

### Post by Herman on 2006-11-03
If that happened to me I would either just delete the line that points Grub to the non-existing splashimage, or get a splashimage  and place it in somewhere, and edit the line to point to it, so Grub will be happy.

Hey, have you had a look in /usr/share/pixmaps/backgrounds/cosmos :D
There are some really nice .jpg images in there that would make great grubsplashes if one was copied and opened with GIMP and turned into an splashimage.
There are some more in /usr/share/pixmaps/faces too. Those are only 96 x 96 pixels, but they could be resized.   :D

There are some websites on the internet that you can google for and download splashimages already made for you, here are a few links, [McGrof's]("http://ruslug.rutgers.edu/%7Emcgrof/grub-images/images/"),  [schultz-net]("http://www.schultz-net.dk/grub.html"), and [schragehome.de]("http://schragehome.de/splash/")  

Or check these links out,
[Post your GRUB bootsplash image!]("http://www.ubuntuforums.org/showthread.php?t=200852&highlight=grub")             
[Grub Boot Splash Screens]("http://www.ubuntuforums.org/showthread.php?t=278396&highlight=grub+splash")
[GRUB 0.97 and splash screens]("http://www.ubuntuforums.org/showthread.php?t=230485&highlight=grub+splash")
[Kubuntu Widescreen GRUB Splash]("http://www.ubuntuforums.org/showthread.php?t=225193&highlight=grub+splash")
[How to: Grub Splash Image]("http://www.ubuntuforums.org/showthread.php?t=89916&highlight=grub+splash")             
[HOWTO: Grub splash images.]("http://www.ubuntuforums.org/showthread.php?t=30341&highlight=grub+splash")
[simple human GRUB splash]("http://www.ubuntuforums.org/showthread.php?t=171479&highlight=grub+splash")

I hope you will find something there you like,
Regards, Herman :D

---

### Post by Norradj on 2006-11-05
Thanks Herman for your advice. I uncommented the line in Grub; ## splashimage=(hd1,1)/boot/grub/default-splash.xpm.gz 
And voila! Everthing back to normal after reboot.
I found this line on an another pc with Ubuntu 6.06 so it seems that the line is an artifact after upgrade to Ubuntu 6.10. I upgraded the OFFICIAL upgrade method: $ gksu "update-manager -c"

---

### Post by MikeAnix on 2006-11-06
May I add a newbie question to this thread?

I'm having the same problem.  How can I edit the GRUB.conf if Ubuntu does not want to start?

---

### Post by MikeAnix on 2006-11-07
For the profit of every one looking for a solution, I had to re-install GRUB, and now everything is working fine.
:)

---

