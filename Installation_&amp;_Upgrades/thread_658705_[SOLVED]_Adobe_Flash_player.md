---
title: "[SOLVED] Adobe Flash player"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by tiki28 on 2008-01-04
I have installed Ubuntu 7.10 on my Dell 1150 laptop. 
Have tried everything but can get flasher player to work!

If I go to NY Times page it tells me to install it.

Help!!
thanks

artie

---

### Post by PmDematagoda on 2008-01-04
Did you install Flash using:-

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by tiki28 on 2008-01-04
Yes, but it replied with "already newest installed"

---

### Post by Sef on 2008-01-05
What browser are you using?

---

### Post by the_sorrow on 2008-01-05
Do this:
in terminal:
sudo apt-get remove flashplugin-nonfree gnash

Download the tar from the adobe website here. Save to desktop
[http://www.adobe.com/shockwave/downl...ShockwaveFlash](http://www.adobe.com/shockwave/downl...ShockwaveFlash)

then on terminal:
cd Desktop

tar -zxvf install_flash_player_9_linux.tar.gz 

sudo ./install_flash_player_9_linux/flashplayer-installer

Make sure you close all firefox windows and installer should automatically install. If it asks you where to install, install to /usr/lib/firefox

that's it.

---

### Post by Hugo.roy on 2008-01-05
Doesn't work for me. Firefox shows the "plugin required" bar on the top of the page : [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/) and then says that it does not fin any plug in.

---

### Post by Hugo.roy on 2008-01-05
But actually i can perfectly see youtube videos...
I suppose this test page is not working.

---

### Post by tiki28 on 2008-01-05
Well now I see whats wrong!
The down load from the repository has a check sum error.

So, I down loaded it from Adobe, and Installed it in terminal.

Thank!

---

### Post by tiki28 on 2008-01-05
> **the_sorrow said:**
> Do this:
in terminal:
sudo apt-get remove flashplugin-nonfree gnash

Download the tar from the adobe website here. Save to desktop
[http://www.adobe.com/shockwave/downl...ShockwaveFlash](http://www.adobe.com/shockwave/downl...ShockwaveFlash)

then on terminal:
cd Desktop

tar -zxvf install_flash_player_9_linux.tar.gz 

sudo ./install_flash_player_9_linux/flashplayer-installer

Make sure you close all firefox windows and installer should automatically install. If it asks you where to install, install to /usr/lib/firefox

that's it.

Thank you...............very helpful

---

### Post by kaykelkar on 2008-01-05
guys
i am unable to play any videos from youtube.com
it say "Video Player undefined for this type of media. application -x/shockwave- flash"
pls help and advise

---

