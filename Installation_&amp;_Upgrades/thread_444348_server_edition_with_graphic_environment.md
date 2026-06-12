---
title: "server edition with graphic environment"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by myname on 2007-05-15
First of all, is there a difference between the server install then installing gnome/ubuntu desktop vs. installing Ubunutu Desktop and all the server pieces (apache, mysql, bind, etc.)?

I installed Ubuntu Feisty Server last night, then installed the Ubuntu Desktop to get gnome.  Very easy install on both, GREAT JOB.

After the installed of ubuntu-desktop, gnome started and I had a native resolution of 1280x1024, which is GREAT.  This will come into play in a minute.

However, when I went to install the restricted video drivers via the menu, I received an error saying that the restricted modules-server is not installed.  I tried to install them but received an error.  Is this even possible with the server?

After the above didn't work, I did a fresh install of Ubuntu Feisty Desktop, that's the great thing about Ubuntu, doesn't take long to install, though my native resolution was 1024x768... odd.... I then installed the restricted video drivers (nvidia card with 256 megs RAM), and resolution was still 1024x768, and I didn't see any nvidia control panel.  

Is it recommended to install the video drivers manually and not with the restricted drivers install tool?

--Kevin

---

### Post by dfreer on 2007-05-15
to install manually I believe the correct command is:
```
sudo apt-get install nvidia-glx
```
or nvidia-glx-new
```
sudo nvidia-settings
``` should let you access nvidia control panel.

You can install the same packages from either version, but the desktop from what I hear doesn't get configured the same as it does from a Desktop install cd. Everything should work the same but the question is whether ubuntu detects everything the same way and configures it correctly.

---

### Post by myname on 2007-05-15
Thanx.  I will probably install the video drivers with Envy, since that is REALLY easy. :)

I'll give it a shot, if it doesn't work, I only spent 20 minutes and I can re-install at lunch.

-Kevin

---

### Post by myname on 2007-05-15
I installed Feisty Server
Installed Gnome 
installed Xserver
Now I have another problem the graphical environment isn't loading b/c it can't find the fonts.  Is there a font package?

Or is it just better to install Feisty Desktop and add the server pieces?  I guess I'm going the server route then adding the graphical as a learning experience.

Can anyone point me in a direction to get gnome loaded?

--Kevin

---

### Post by dfreer on 2007-05-15
you should just install the ubuntu-desktop package and it should install everything it needs. gnome, xserver, etc.

if you have problems with ubuntu detecting hardware, use the Desktop CD to install, then install the server packages you want/need.
if you want to learn how the desktop is installed go the route you are using, by manually installing the packages that you want/need.
if you just want a server, why bother with GUI at all? :D ssh is easy to use and you'll learn more about the CLI then any other method.

---

### Post by myname on 2007-05-15
Thanx for the tips...

Sometimes it's easier for me to sit on the box and just point and click.  :)

Do you know what the font packages are called?

I may just install the desktop, and remove/add what I (don't) need, might be quicker.

--Kevin

---

### Post by dfreer on 2007-05-15
hmmm i dunno, but if it caused an error on a specific file (say it couldn't find /usr/share/fonts/myubercoolfont.ttf), you could look and see which package owns that font on [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

