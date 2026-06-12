---
title: "How do I install Assault Cube for Ubuntu 9.1?"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by SNYP40A1 on 2009-11-28
I just installed Ubuntu 9.1 last night and I have enjoyed playing Assault Cube in Windows.  I would like to install in Ubuntu.  I found this forum with instructions:

[http://ubuntuforums.org/showthread.php?t=526417](http://ubuntuforums.org/showthread.php?t=526417)

But it looks like there is no deb package for Ubuntu 9.1.  What's the best way to install it?

---

### Post by kleeman on 2009-11-28
[http://old.getdeb.net/app/AssaultCube](http://old.getdeb.net/app/AssaultCube)

---

### Post by SNYP40A1 on 2009-11-28
The packages installed without any error and an Assault Cube icon now appears under my Applications menu.  But when I click on it, nothing happens. :-(

---

### Post by lessmemorelove on 2009-11-28
i dont know if this makes a difference but getdeb put all the games under a playdeb repository. you can find assault cube here: [http://www.playdeb.net/updates/?page=8#assaultcube](http://www.playdeb.net/updates/?page=8#assaultcube)

from the site on how to add the repository:

[LIST=1]
[*]Go to System-Administration-Software Sources, Third-Party Software tab, Add:
 								deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb games 								Add the repository GPG key, open a terminal window and type:
 								wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -
[*] 							Click the "Install this now" button below the screenshot of the desired game.
[/LIST]

---

### Post by SNYP40A1 on 2009-11-28
lessmemorelove, thanks for the tip.  I un-installed my previous assaultcube package and I downloaded and successfully installed AssaultCube 1.04 from the link you provided.  When I click on the icon under Applicaitons, nothing happens.  When I go to terminal and type in assaultcube, I get this:

```

Using home directory: /home/houston/.assaultcube_v1.0
init: sdl
init: net
init: world
init: video: sdl
init: video: mode
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  17
  Current serial number in output stream:  17

```

Looks like something is wrong with my video.  I just installed Ubuntu last night and I am using the default open source video drivers.  I have an Ati 9200 SE, runs the game fine under windows at full resolution and settings.

---

### Post by SNYP40A1 on 2009-11-28
Fixed it by doing this:

sudo apt-get remove xorg-driver-fglrx
sudo reboot

([https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/293012](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/293012))

I probably installed that last night in an attempt to fix the "black desktop background" video issues that I was having.  

Anyhow, the game playes, but really badly.  The video chops hard even at medium detail.  Running around 3-4 FPS on a Core2 E6700 system with Ati video card.  It runs perfectly smooth even at the highest graphics settings in Windows XP, but chops hard in Linux.  Are there any graphics settings that I might be missing?  For some reason, I don't seem to have an xorg file.

---

### Post by lessmemorelove on 2009-11-28
you have ati? sorry. i have nvidia and the game is playing flawless. we will need somebody with ati and ubuntu experience to help you any further. you could always try playing it under wine using the windows install. it has a platinum rating.

edit: do you have compiz off?

---

### Post by SNYP40A1 on 2009-11-28
I thought about that (and other games as well), but how would that work?  Either way, I am still using the same video driver.

By the way, does Nvidia have better support for Linux than Ati?  How old is your video card?

Downloaded and installed Wine.  The whole integration was very good and performance was a little better, but not as good as running under WinXP.  This is probably because the video driver settings that I am using are not optimized.  I am sure Ati "could" better drivers than the OS drivers simply because they know their own hardware better and how to get better performance out of it.  

I will look to see if anyone has some better settings for the Ati 9200 SE.  Maybe I need to set some options to improve performance of the Linux version of Assault Cube.  But I was able to get both to run, so that's an accomplishment.

---

