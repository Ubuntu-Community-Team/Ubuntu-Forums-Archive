---
title: "no firefox plugins"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by bjlockie on 2011-02-16
I'm trying to install Adobe Flash but it won't work and I noticed about:plugins says "No plugins are installed".

---

### Post by amsterdamharu on 2011-02-16
I think the package is available in nonfree, try the following command:

```
sudo apt-get install adobe-flashplugin
```

If that didn't work please post the output of the following command:

```
apt-cache search adobe | grep flash
```

To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in code tags: &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

---

### Post by bjlockie on 2011-02-17
$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'adobe-flashplugin' has no installation candidate



$ apt-cache search adobe | grep flash
red5-doc - flash streaming server - documentation
red5-server - flash streaming server
xul-ext-flashblock - mozilla extension to block Adobe Flash content
flashplugin-nonfree-extrasound - Adobe Flash Player platform support library for Esound and OSS
flashplugin-installer - Adobe Flash Player plugin installer
flashplugin-nonfree - Adobe Flash Player plugin installer (transitional package)


$ sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-installer is already the newest version.


$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.

0 plugins. :-(
I think it is looking i the wrong place.

---

### Post by amsterdamharu on 2011-02-17
If you installed flashplugin-installer you should have a file called /usr/share/ubufox/plugins/libflashplayer.so

If you don't then you can re install it

```
sudo apt-get install --reinstall flashplugin-installer
```

I think the adobe-flashplugin is only available on Mint (or in the Mint repository)

---

### Post by bjlockie on 2011-02-19
> **amsterdamharu said:**
> If you installed flashplugin-installer you should have a file called /usr/share/ubufox/plugins/libflashplayer.so

If you don't then you can re install it

```
sudo apt-get install --reinstall flashplugin-installer
```


The reinstall fixed it.

---

