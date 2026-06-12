---
title: "restore (backup) VPN connections nm-applet"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by oneindelijk on 2010-03-30
Hi, 

I reinstalled my computer :-)
I was wondering if I can restore all the VPN connections I had in the nm-applet.
I have a backup of my complete home directorie.
Or are these stored in the gconf-editor ?
If so, is there a way to extract that data from the backed-up version and insert it into the current version ?

thx !

---

### Post by oneindelijk on 2010-04-11
I found this in a nm-applet related bug:
> you can dump all your settings (from 0.6 and 0.7) by running

gconftool-2 -R /system/networking

Can I use this to import the results (partly) back into the gconf (to restore my VPN settings) ?

---

### Post by oneindelijk on 2010-04-14
:-) Happy !!
My VPN network connections reappeared in the nm-applet after restoring the directory ~/.gnome/gconf/system/networking.
All the passwords were gone though.
So next time I will use the new way, which is exporting gconf to an xml file
and I will back up my passport-wallet !

So, Closure (and peace)

---

