---
title: "Update to breezy and a little problem with gnome"
date: 2005-10-05
forum: Installation &amp; Upgrades
---

### Post by Eleka on 2005-10-05
Hello!!!

Yesterday I decided to upgrade my ubuntu to breezy, I executed first an update (changing before the sources.list), an upgrade and, finally a dist-upgrade.

When the proccess ask me about keep or write new configuration files, I answer that make it new, because I didn't have very much things configurated, but, when I restart, the gnome can't start and I have a black screen that only can be solutioned with a hardware-reset.

How can I repare the gnome using somethiung about dpkg or similar?

Thanks to all and excuse me by my english :S

---

### Post by heimo on 2005-10-05
First thing to try is reconfiguring X:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start

```

---

### Post by Eleka on 2005-10-05
I can't test it now, but I suppose that I wouldn't run /etc/init.d/gdm stop, because it was off if I start in recovery mode, isn't it?

I think that I have a backup of my xorg configuration, Would it be good for me?

---

### Post by heimo on 2005-10-05
Yes, no need to stop something that's not running. It's there just to make sure (someone else might use these instructions) that autoprobing works as well as possible. I think reconfiguring process itself also makes backup of the config file.

---

### Post by Eleka on 2005-10-07
Hi people!

Heimo, it works! I think that I don't set all the correct values in the dpkg-reconfigure, but it works (it boots ...)

Now, I have aproblem with the language, because the desktop is in english, but some menu elements, how "administration" are set in my correct language (spanish-spain) .. 

I resolve that! Now, only some things are in english, but a little things without importancy. Thanks a lot.

Note: oOo ... the wireless card doesn't appear :S I only have 3 networw interfaces: eth0, lo and &#191;ppp0? Before updating to Breezy I have one named wlan0 ... :S

---

