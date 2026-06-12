---
title: "dpkg was interrupted"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by Ultimate_goblin on 2008-11-19
Hi everyone... it's me again.
It seems I can't update Ubuntu files. The update manager shows 30 updates ready to install, but as soon as I click "install" it tells me
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."
If I try to run ```
sudo dpkg --configure -a
``` the output is
```
Setting up flashplugin-nonfree (10.0.12.36ubuntu1) ...
Downloading...
--2008-11-19 10:44:00--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
Resolving fpdownload.macromedia.com... 88.221.202.70
Connecting to fpdownload.macromedia.com|88.221.202.70|:80... 

```
But he stuck this way until he says "connection timed out, retrying" and repeating the process over and over again. What's more, even if I close the window, the process still seems to be running, how can I kill it? (I am a reeeeal noob)
I have manually downloaded the alpha version of flash player for ubuntu 64 but of course no improvements.
Any help would really be useful. Thanks in advance

---

### Post by inobe on 2008-11-19
reboot your machine and try again, this time do

```
sudo dpkg --configure -a
```

then

```
sudo apt-get update
```

finally 

```
sudo apt-get upgrade
```

after those steps see if you can run synaptic

---

### Post by Ultimate_goblin on 2008-11-19
> reboot your machine and try again, this time do
```
sudo dpkg --configure -a
```Same thing. When I type ```
sudo dpkg --configure -a
``` I get the output ```
Setting up flashplugin-nonfree (10.0.12.36ubuntu1) ...
Downloading...
--2008-11-19 15:46:34--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
Resolving fpdownload.macromedia.com... 88.221.202.70
Connecting to fpdownload.macromedia.com|88.221.202.70|:80... failed: Connection timed out.
Retrying.

--2008-11-19 15:49:44--  (try: 2)  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
Connecting to fpdownload.macromedia.com|88.221.202.70|:80... 

```
And here it starts over again.

---

### Post by taurus on 2008-11-19
Are you sure your network connection is working because I just tried to download it from a terminal and didn't have any problem downloading it?

```
wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
```

---

### Post by Ultimate_goblin on 2008-11-19
I have a proxy because I'm in a campus, but I can surf on the internet normally and synaptic has access to the web, otherwise no updates would be found. Should be a proxy issue (again), then? What do you suggest me to do?

---

