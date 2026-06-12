---
title: "Installing Mplayer in 11.10"
date: 2011-10-31
forum: Installation &amp; Upgrades
---

### Post by robn30 on 2011-10-31
Ok I am trying to install Mplayer in Ubuntu 11.10 and keep getting an error that I need to install gtk-2.  GTK+3 is already installed but maybe it needs GTK+2.  So when I try to install GTK2 in get the error listed below

checking for FT_New_Face in -lfreetype... yes
checking For sufficiently new FreeType (at least 2.0.1)... no
configure: error: pangoxft Pango backend found but did not find freetype libraries

I checked and libfreetype6 is installed but not sure if that is good enough.  I am a beginner and need some expert advice here.  I have been in and out of the Ubuntu (Linux) world and just don't know enough yet to smartly work around these errors.  Thanks in advance for any help you all may provide me.

---

### Post by robn30 on 2011-10-31
I even just installed freetype 2.4.7 and all went well with that but still getting the error when trying to install GTK+2.

---

### Post by andrew.46 on 2011-11-02
You are attempting to compile MPlayer from source? This is certainly an option if you are not happy with the repository offering, although a simple:

```
sudo apt-get install mplayer smplayer

```
is enough for many people. If you *definitely* need the latest MPlayer perhaps have a look here:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)

---

### Post by robn30 on 2011-11-02
> **andrew.46 said:**
> You are attempting to compile MPlayer from source? This is certainly an option if you are not happy with the repository offering, although a simple:
 
```
sudo apt-get install mplayer smplayer

```
is enough for many people. If you *definitely* need the latest MPlayer perhaps have a look here:
 
Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)
 
Yeah I figured out how to do it.  I just needed to use Synaptic to install libgtk2-dev.  Once I did that all went well.  There is a bit of a learning curve getting back into this that is for sure.  If you know what you are doing most things are fairly easy and make sense.  I agree the repository method is the best.  Is the Ubuntu repository the same thing as compiling it from source from the Mplayer site?

---

### Post by andrew.46 on 2011-11-02
> **robn30 said:**
>  Is the Ubuntu repository the same thing as compiling it from source from the Mplayer site?

No, the repository version is reasonably aged while the svn site carries the cutting edge source and all the bug fixes, improvements and risk that that implies.

---

