---
title: "[SOLVED] help with syntax for installing to libs firmware"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by tunznath on 2008-07-14
Hi All
please help
I am trying to copy a file I downloaded to my desktop called firmware_v3.tgz to /lib/firmware - I cannot drag it into the folder as I dont have the right permission(root) - what is the terminal command to do this. Please could someone put the correct command in a post so I can copy and paste it into the terminal to get it to copy - also an explanation on how to get sudo permissis would be great to drag files if it is possible.

I am trying to get TV working using this tutorial
[http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices](http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices)
many thanks in advance
Nathan

---

### Post by diafanos on 2008-07-14
you can do:
```

sudo mv ~/Desktop/firmware_v3.tgz /lib/firmware/firmware_v3.tgz

```

and then give your password.

or if you prefer with drag-n-drop, then
press:
```

Alt+F2

```

and in the new window type:
```

gksudo nautilus

```

Give the password, and now you can drag and drop your files wherever you like, using the "root nautilus"...

---

### Post by tunznath on 2008-07-14
Hi Diafanos
Many thanks for that - I have been trying for ages to get a hauppagge hvr900 to work so hopefully this will help

---

