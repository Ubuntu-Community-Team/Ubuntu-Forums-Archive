---
title: "how to play .rm files"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by himanshugarg on 2008-06-19
hey folks !!! i m new to linux... and i can't play my rm files in mplayer or movie player. i only get a sound and not video. could you please help me out ..

---

### Post by iaculallad on 2008-06-19
You need to install applicable codecs for RM files. Try reading this [thread]("http://ubuntuforums.org/showthread.php?t=766683").

---

### Post by silkstone on 2008-06-19
I had a problem with Real audio playback in Firefox recently - listening to radio on the BBC site - and the solution, as suggested by the kind people on this forum, was to install RealPlayer. That should also be able to play your rm files. The following is taken from the Ubuntu Wiki...

Installing Real Player 11 and Configuring Mozilla Plugin
--------------------------------------------------------

The following steps show how to install Real Player 11 and Mozilla Plugin for Firefox 3.0 browsers running on Hardy Heron.

Download Real Player 11 from:

  [www.real.com](www.real.com)

Open a terminal and change to the directory where the file was downloaded. Grant execute permissions and run the setup using the following commands:

  ```
chmod 770 RealPlayer11GOLD.bin
  sudo ./RealPlayer11GOLD.bin
```
  

Use the following default installation directory during the installation:

  /opt/real/RealPlayer

The installer will copy the files and create menu shortcuts. Then run the following commands.

  ```
cd /usr/lib/firefox-addons/plugins
  sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.xpt nphelix.xpt
  sudo ln -s /opt/real/RealPlayer/mozilla/nphelix.so nphelix.so
  sudo mv /usr/lib/totem/gstreamer/libtotem-complex-plugin.so ~/.
```

Open Firefox and type ```
about:plugins
``` in the address bar. Scroll down and look for the following entry.

  Helix DNA Plugin: RealPlayer G2 Plug-In Compatible
  File name: /opt/real/RealPlayer/mozilla/nphelix.so
  Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.4005 built with gcc 3.4.3 on Feb 25 2008

If found, your Real Plugin is installed properly!

---------------------

---

### Post by himanshugarg on 2008-06-19
hey thank man ..
bt is it neccessary to install real player ??

---

### Post by silkstone on 2008-06-20
Yes, if you want the streaming to work in Firefox 3. It's not so bad - RealPlayer in Ubuntu isn't invasive like in Windows. It appears in the Sound and Video list, but it doesn't try to make itself the default for media files. I was nervous about installing it, but there have been no problems.

---

### Post by meindian523 on 2008-06-20
or you can just install VLC.
```
sudo apt-get install vlc
```
VLC r0cks!

---

### Post by Bablefish on 2008-06-20
The easiest way to install Real Player, (and by the way I tried VLC and it did not work for me) is head here [http://www.debianadmin.com/install-realplayer-in-debian-sargeetch-and-sid.html](http://www.debianadmin.com/install-realplayer-in-debian-sargeetch-and-sid.html)

---

### Post by meindian523 on 2008-06-20
<bad post>

---

### Post by jaithehulk on 2008-06-21
Use totem media player and win32 codecs....
i forgot the package name 
I guess it was W32codecs...
search for w32codecs in synaptic manager..

---

