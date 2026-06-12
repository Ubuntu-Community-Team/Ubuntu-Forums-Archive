---
title: "Installed but only able to get 'login'"
date: 2005-02-15
forum: Installation &amp; Upgrades
---

### Post by Ron W on 2005-02-15
I've just installed Ubuntu today, but am only able to get the login - not GNOME.

It seems to be a problem with disk space which I don't understand as I've partitioned as suggested in the Ubuntu Installation Manual. I've partitioned as follows:-

/ - 100MB
/home - 1GB
/tmp - 50MB
/var - 3GB
/usr - 3GB
swap - 64MB
/usr/local - 2GB

Any ideas where I might have gone wrong?

I'm thinking that maybe one of the partitions is too small. My limited understanding of 'aptitude' would suggest that GNOME has not been installed. Where should GNOME be located (ie which partition)? 

Thanks

Ron

---

### Post by drasko on 2005-02-15
The applications you install are usually put in /usr/share (the data) - so searh for gnome there ```
$ls -la /usr/share | grep gnome
``` 
Executables are kept in /usr/bin, so search also in that directory.

But, booting in text mode is usually issue of bad configured X system. Check the messages from X in /var/log/Xorg.log. If you see gnome trying to start at boot several times and fail - that's it. Also to boot in gnome right away you have to have installed not only gnome, but also gdm - gnome display manager. Apt-get it, if you don't have it.

And finnaly - check your /etc/inittab. What is your default runlevel? It can also be the reason of booting in consloe mode...

Drasko

---

### Post by alastair on 2005-02-15
That's quite a partition setup - perhaps a bit over complicated for a desktop. I tend to use /home, / and perhaps /usr (for a desktop).

You say "It seems to be a problem with disk space" - what makes you think this?

In "aptitude" and "installed packages", I have a "gnome" section.

Maybe try installing a gnome package, see dependencies and watch an install - and error messages, if any.

---

### Post by Xian on 2005-02-15
[QUOTE=Ron W]It seems to be a problem with disk space which I don't understand as I've partitioned as suggested in the Ubuntu Installation Manual. I've partitioned as follows:-

/ - 100MB
swap - 64MB

Any ideas where I might have gone wrong?[/QUOTE]
There's no way your root partition should be only 100MB.
I can see it for /boot but that's another story.

And that swap would only be appropriate for 32MB or physical ram.
You don't have more perhaps?

Try something more conservative and similar to this:

/  - 8 GB
/home - 1 GB
/boot - 100MB
swap - *Twice the amount of your phys ram (up to 1 gig)*

---

