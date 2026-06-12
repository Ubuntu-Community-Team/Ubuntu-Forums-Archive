---
title: "Install karmic from web"
date: 2009-06-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by halfsane on 2009-06-20
Sorry for the noob ? on the test boards...but

I've never found a step by step on how to do this.  I have a fast connection and would love to install the alpha this way a few times.

Thanks,

---

### Post by xebian on 2009-06-20
> **halfsane said:**
> Sorry for the noob ? on the test boards...but

I've never found a step by step on how to do this.  I have a fast connection and would love to install the alpha this way a few times.

Thanks,

Don't know if this is what you want but you should download the netboot install.  You just get a base command line install, and then you install your fav desktop -
      for KDE      - install kubuntu-desktop
 which will then be fetched from the ubuntu repos.

---

### Post by SuperSonic4 on 2009-06-20
The minimal cd would be better - it is a 10mb ISO and has only the very essentials on it - you can then add whatever you like as above: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Bear in mind that it will be a jaunty cd but you can upgrade to karmic by opening sources as root: ```
sudo nano /etc/apt/sources.list
``` and replacing every instance of **jaunty** with **karmic**. (Ctrl + \ is find and replace in nano and ctrl+x is exit). 

Then update and upgrade ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by halfsane on 2009-06-20
You guys are awesome!  That's exactly what I was looking for!

---

### Post by xebian on 2009-06-20
> **SuperSonic4 said:**
> The minimal cd would be better - it is a 10mb ISO and has only the very essentials on it - you can then add whatever you like as above: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Bear in mind that it will be a jaunty cd but you can upgrade to karmic by opening sources as root: ```
sudo nano /etc/apt/sources.list
``` and replacing every instance of **jaunty** with **karmic**. (Ctrl + \ is find and replace in nano and ctrl+x is exit). 

Then update and upgrade ```
sudo apt-get update && sudo apt-get upgrade
```

How can you be better than yourself?  :p

There is a mini.iso for karmic in cdimages.ubuntu.com with the right kernel and no editing.

---

### Post by Regenweald on 2009-06-20
> **SuperSonic4 said:**
> The minimal cd would be better - it is a 10mb ISO and has only the very essentials on it - you can then add whatever you like as above: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Bear in mind that it will be a jaunty cd but you can upgrade to karmic by opening sources as root: ```
sudo nano /etc/apt/sources.list
``` and replacing every instance of **jaunty** with **karmic**. (Ctrl + \ is find and replace in nano and ctrl+x is exit). 

Then update and upgrade ```
sudo apt-get update && sudo apt-get upgrade
```

The karmic Minimal is available : 
[http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-amd64/alpha-2/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-amd64/alpha-2/images/netboot/)

finished a fresh install a few hours ago.

---

### Post by taavikko on 2009-06-20
> **SuperSonic4 said:**
> The minimal cd would be better - it is a 10mb ISO and has only the very essentials on it - you can then add whatever you like as above: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Bear in mind that it will be a jaunty cd but you can upgrade to karmic by opening sources as root: ```
sudo nano /etc/apt/sources.list
``` and replacing every instance of **jaunty** with **karmic**. (Ctrl + \ is find and replace in nano and ctrl+x is exit). 

Then update and upgrade ```
sudo apt-get update && sudo apt-get upgrade
```

why do this when "update-manager -d" is far better solution?

---

### Post by Swarms on 2009-06-20
There should be a program you could boot from a disc/usb drive whatever and through that connect to the net and install either Ubuntu LTS, latest release or the latest development version.

---

### Post by Regenweald on 2009-06-20
> **taavikko said:**
> why do this when "update-manager -d" is far better solution?

My fresh install is running much better than my upgrade.

---

### Post by taavikko on 2009-06-20
> **Regenweald said:**
> My fresh install is running much better than my upgrade.

Point was: don't edit sources.list manually and do the upgrade, when there's better tools to do it.

Fresh install is always an fresh install. But there really isn't a need for it most of the times. (if you know what you're doing)

---

### Post by Regenweald on 2009-06-20
> **taavikko said:**
> Point was: don't edit sources.list manually and do the upgrade, when there's better tools to do it.

Fresh install is always an fresh install. But there really isn't a need for it most of the times. (if you know what you're doing)

No need to get excited :) , was just sharing. I get and have used your way before.

---

