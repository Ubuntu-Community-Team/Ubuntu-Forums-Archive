---
title: "Linux, Nvidia, and the drivers"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by meinzorn on 2007-03-14
ok.. throw the newb comments at me, I'm expecting them. 

I want to install the nvidia drivers for my video card.  Where do I start?? I downloaded them from the site... but when I tried to type "sh file" it said that I need to be root. 

help....?

---

### Post by chewearn on 2007-03-14
For stable driver in the repository, type;
```
sudo aptitude install nvidia-glx
sudo nvidia-glx-config enable
```

For latest beta driver, use any of the following:
1. Envy
2. Automatix2
3. Or find instruction rom nVidia site

Don't know how to find these?  Google is your friend. :mrgreen:

---

### Post by aysiu on 2007-03-14
**Step 1**. Enable extra repositories by following [these instructions](http://www.psychocats.net/ubuntu/sources).

**Step 2**. Install the drivers by pasting this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get update && sudo apt-get install nvidia-glx nvidia-kernel-common
```

---

### Post by Toet on 2007-03-15
You newb! You should know that by asking questions on this forum you can learn things. Everybody starts out being a newb, asking things and trying things out is the only way to loose this status.

After installing the nvidia drivers as mentioned above, you could try to alter somethings to make the driver go faster and better.

For example you could try to alter the configuration file of X-windows. This file is called xorg.conf and is in the /etc/X11 folder. You can alter it by entering the following code in a terminal window:

```
sudo gedit /etc/X11/xorg.conf
```

In the Section "Device" you can add the following two lines:

```
Option       "RenderAccel" "true"
Option       "NoLogo" "true"
```

This will set acceleration on for faster display and the nvidia logo off when starting X.

Then you can also have a look at the resolutions. When I install my nvidia drivers, the maximum resolution is 1024x768, and I want to have 1280x1024 available.

This is done in the Section "Screen". In my case I add the 1280x1024 in front of the other resolutions.

Always make a backup before you start changing a file!

Have fun, and don't forget to google. (searching for *nvidia driver ubuntu edgy howto* in this example)

---

