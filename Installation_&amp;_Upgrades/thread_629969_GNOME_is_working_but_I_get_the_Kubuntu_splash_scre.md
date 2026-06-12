---
title: "GNOME is working but I get the Kubuntu splash screens"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by Bartender on 2007-12-02
I installed the "kubuntu-desktop" package from a Kubuntu alt-install CD to Ubuntu 7.10.  I haven't yet gone into the KDE desktop, just restarted the PC afterward.
It appears to work fine - I get the "Sessions" options, the GNOME desktop comes up, etc.  

The weird thing is I get the blue "Kubuntu" splash screen with the progess bar during startup and shut-down.  I went into Sessions and asked it to boot to GNOME instead of "Last Session" - no difference.
This isn't a big deal since everything seems to work OK once I get to the desktop, but it's kind of annoying if you know what I mean and it makes me wonder if something's not quite right.

Anyone know how to get the start-up and shut-down splash screens to coordinate with the actual desktop?

---

### Post by logos34 on 2007-12-03
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_change_the_USplash_Screen_on_startup.2Fshutdown](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_change_the_USplash_Screen_on_startup.2Fshutdown)

---

### Post by Bartender on 2007-12-03
Thanks!
Man, there's a lot of stuff in that guide.  
I need to read it every once in a while.

Whoohoo a thousand beans

---

### Post by TristanDee on 2007-12-03
Yeah, there are a lot of things. Hope logos34's advice did work. I haven't tried it. But I faced a similar situation a few days ago after I uninstalled Kubuntu Desktop.
Anyways, here is another way out--it worked fine for me:

Paste this into a terminal:
[COLOR="Blue"]sudo update-alternatives --config usplash-artwork.so[/COLOR]

Choose usplash-default.so for the default brown Ubuntu splash, or choose whichever one you like.

Then paste this:
[COLOR="Blue"]sudo dpkg-reconfigure linux-image-`uname -r`[/COLOR]

And your Ubuntu Splash is back.

---

### Post by Bartender on 2007-12-05
Well, that didn't work.  I followed the steps in the Ubuntu documentation.  The PC logged off with the Ubuntu splash and I thought all was well, but when it rebooted I got a black screen with three lines of text.  Something about a Kernel Panic Error. 
Since I really don't know much about fixing anything when it's broke I just re-installed Ubuntu.  With a separate /home partition it took very little time to get back to where I was before installing kubuntu-desktop.  This time I'm just installing the specific KDE programs that I want instead of the entire kubuntu-desktop package.

---

