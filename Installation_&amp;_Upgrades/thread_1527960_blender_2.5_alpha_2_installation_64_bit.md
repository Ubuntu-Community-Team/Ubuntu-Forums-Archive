---
title: "blender 2.5 alpha 2 installation 64 bit"
date: 2010-07-10
forum: Installation &amp; Upgrades
---

### Post by xredan on 2010-07-10
I really need to install blender 2.5 alpha 2 64 bit but i can't figure out how

this is the download link
[http://www.blender.org/index.php?id=1262&f=http://download.blender.org/release//Blender2.50alpha/blender-2.5-alpha2-linux-glibc27-x86_64.tar.bz2]("http://www.blender.org/index.php?id=1262&f=http://download.blender.org/release//Blender2.50alpha/blender-2.5-alpha2-linux-glibc27-x86_64.tar.bz2")
:icon_frown::icon_frown:(*,)](*,)](*,):cry::-k:-k

---

### Post by crichard on 2010-07-10
It's almost similar to how to "[install Firefox and Thunderbird in Ubuntu]("http://surferzworld.com/2010/01/installing-firefox-thunderbird-ubuntu/")"

Right click on that downloaded file(tar.bz2) & select extract here, rename that folder to blender.
Keep that folder on your home directory.
In terminal execute the following code,

```
sudo mv ~/blender /opt && sudo ln -s /opt/blender/blender /usr/bin/blender
```

To create a launcher, refer the same post (Bonus tutorial: How to create a launcher for our Firefox and Thunderbird?)

For blender, these launcher icons are available under icons folder. For Command & Name field, enter blender.

That's it. I don't like to explain step by step here, clear instructions are available on that post itself.

Let me know the result. :)

---

### Post by xredan on 2010-07-13
I tried it but it won't work

---

### Post by xredan on 2010-07-14
It now works perfectly thanks

---

### Post by crichard on 2010-07-16
> **xredan said:**
> It now works perfectly thanks

Glad to know it worked for you.:D  Please mark this thread  a as Solved.

---

