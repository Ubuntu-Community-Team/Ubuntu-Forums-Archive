---
title: "Dual boot Karmic and Mandriva 2010, need help."
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by rldev on 2009-12-02
Can someone point to a easy to follow instuctions on how I can install Karmic Koala alongside Mandriva 2010? I left unpartioned space on my drive for this very reason. Thanks.

---

### Post by akashiraffee on 2009-12-02
Just use the installer.  But if karmic koala uses the ubuntu installer and you are used to installers from other distros, beware of this:

[http://ubuntuforums.org/showthread.php?t=1343145](http://ubuntuforums.org/showthread.php?t=1343145)

---

### Post by darkod on 2009-12-02
If you already have Mandriva and installed it yourself, I don't know how detailed information you need. The basic would be:
1. Decide if you want to keep current bootloader or install grub2 that comes with Karmic.
2. Boot with Karmic cd and select Install Ubuntu, at step 4 select Use Largest Continuous Free Space or use manual partitioning, your choice.
3. If you decided to keep your current bootloader, at step 7, the last screen before you click Install click on Advanced and tell grub2 not to install. You will need to add manual entry for Karmic in your current bootloader, I guess it doesn't do it automatically.

---

### Post by rldev on 2009-12-02
Thanks. That sounds perfect! Just what I was looking for!

---

