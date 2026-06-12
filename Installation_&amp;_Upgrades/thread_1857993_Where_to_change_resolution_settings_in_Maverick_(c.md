---
title: "Where to change resolution settings in Maverick (cmd line)"
date: 2011-10-11
forum: Installation &amp; Upgrades
---

### Post by pickarooney on 2011-10-11
I've set up a windows Virtual Machine running Xubuntu 10.10. all was going fine until I stupidly tried to change the resolution to an apparently unsupported widescreen format. now everything is all coloured lines. I am able to just remove the xorg.conf file and restart but then the res is max of 800x600 when I need 1024x768. 

The xorg.conf doesn't specifically mention what resolution to use and I can't figure out where exactly the info to use the buggy resolution is coming from.

---

### Post by WasMeHere on 2011-10-11
Try *xrandr*
It works in lucid, and should work in later versions too

Have fun finding out about linux
Olle

---

### Post by pickarooney on 2011-10-11
> **Olle Wiklund said:**
> Try *xrandr*
It works in lucid, and should work in later versions too

Have fun finding out about linux
Olle

I've been messing around with xrandr for ages but I can't figure out what to do with it so that it writes the default resolution to a config file.

---

### Post by pickarooney on 2011-10-11
I was able to get around it by simply changing the order of the Modelines in xorg.conf to put my preferred resolution there. Simple when you think of it!

---

### Post by WasMeHere on 2011-10-11
> **pickarooney said:**
> I've been messing around with xrandr for ages but I can't figure out what to do with it so that it writes the default resolution to a config file.

Now that you have working graphics, maybe you can use the tips in the following link to make the setting persistent.
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=11321573&postcount=5_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11321573&postcount=5")

---

