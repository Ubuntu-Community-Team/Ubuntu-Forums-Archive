---
title: "Flash error messages since Jaunty Alfa update."
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Peterfc on 2009-04-05
When going to a number of websites that use Flash Firefox comes up with a message "Additional plugins are required to run this page  also on the right side of the page is a button to install missings plugins.

On the screen that comes up Plugin Finder Service one options is for Adobe Flash player installer. When you click next   Package Plugin - Nonefree is already installed. Is dislayed 

With bbc.co.uk iplayer it reports that you need to install Flash Player. When you go to download Flash player and download the Linux version .Deb for Ubuntu 8.04+ then agree and install. Next screen open with Gdeb Package Installer. Package installer says Error a later version is already installed and supports 

This package officially supports the following browsers:
Firefox 2.x, Firefox 3.x, SeaMonkey 1.11 

This has happened on quite a few sites i have been on 


Thanks for reading

---

### Post by freak42 on 2009-04-05
if you go to the 'url' ```
about:plugins
``` in firefox is there a 'Shockwave Flash' entry? if yes, what exactly does it say below the entry?

---

### Post by nandemonai on 2009-04-05
> **Peterfc said:**
> When going to a number of websites that use Flash Firefox comes up with a message "Additional plugins are required to run this page  also on the right side of the page is a button to install missings plugins.

On the screen that comes up Plugin Finder Service one options is for Adobe Flash player installer. When you click next   Package Plugin - Nonefree is already installed. Is dislayed 

With bbc.co.uk iplayer it reports that you need to install Flash Player. When you go to download Flash player and download the Linux version .Deb for Ubuntu 8.04+ then agree and install. Next screen open with Gdeb Package Installer. Package installer says Error a later version is already installed and supports 

This package officially supports the following browsers:
Firefox 2.x, Firefox 3.x, SeaMonkey 1.11 

This has happened on quite a few sites i have been on 


Thanks for reading

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/326609](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/326609)

---

### Post by gandaran on 2009-04-05
> **Peterfc said:**
> When going to a number of websites that use Flash Firefox comes up with a message "Additional plugins are required to run this page  also on the right side of the page is a button to install missings plugins.

On the screen that comes up Plugin Finder Service one options is for Adobe Flash player installer. When you click next   Package Plugin - Nonefree is already installed. Is dislayed 

With bbc.co.uk iplayer it reports that you need to install Flash Player. When you go to download Flash player and download the Linux version .Deb for Ubuntu 8.04+ then agree and install. Next screen open with Gdeb Package Installer. Package installer says Error a later version is already installed and supports 

This package officially supports the following browsers:
Firefox 2.x, Firefox 3.x, SeaMonkey 1.11 

This has happened on quite a few sites i have been on 


Thanks for reading

looks like you have been installing a lot of flash things, if you want it to work perferctly then you must only have one adobe flash plugin installed, it's very simple, just one latest adobe flash release installed!
and also check you haven't installed any open source flash like gnash or swfdec.

---

### Post by Peterfc on 2009-04-05
HI

Not sure About URL Plugins 

I have enclosed a screenshot of the Plugin Finder Service

/home/peter/Desktop/Screenshot.jpg

Thanks

---

### Post by nandemonai on 2009-04-05
> **Peterfc said:**
> HI

Not sure About URL Plugins 

I have enclosed a screenshot of the Plugin Finder Service

/home/peter/Desktop/Screenshot.jpg

Thanks

Check out the bug report I linked.

```
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

---

### Post by Peterfc on 2009-04-05
Hi nandemonai

Followed to the letter and all is now working thanks you very much. I can now watch a football match i was waiting for.

Thanks

---

### Post by nandemonai on 2009-04-05
> **Peterfc said:**
> Hi nandemonai

Followed to the letter and all is now working thanks you very much. I can now watch a football match i was waiting for.

Thanks

Enjoy ;)

---

