---
title: "Installing GUI for 8.04 server"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by Jahoobie on 2008-06-26
How would I go about installing the GUI on a server running Hardy with only the CLI?

AND, is that something that is recommended?  I am not adept at using the CLI, and am having some issues with Apache after upgrading to 8.04...just wondering if the GUI would be easier for me.

---

### Post by avtolle on 2008-06-26
Take a look at [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) for some ideas. I know that you may not have a low memory system, the concepts in the link apply to installing a GUI atop a server install (in fact, that is the general thrust thereof).

EDIT: Generally, one does not install a GUI on a server system; if this helps you, hey, its your computer, do what makes you feel comfortable. BTW, you could have, had you chosen to do it, done a desktop install and then added the server apps you wanted. Someone on the Forums likes to post something like this: "Desktop Ubuntu = server + GUI", with which I generally agree, recognizing that the kernel for the server edition is optimized for server apps.

---

### Post by Jahoobie on 2008-06-26
Sooooooo...it is generally a bad idea to install the GUI (or at least frowned upon)

This is my very first dive into anything Linux related...

Ok, I will open a new thread with the apache issues so I can get that resolved.

Thanks for the info!

---

### Post by avtolle on 2008-06-26
Like I said, it's your computer, and you should do what you need to do to feel comfortable. That's what it's all about, to me (freedom of choice and all).

---

### Post by DGortze380 on 2008-06-26
If you decide to, installing a gui should be as simple as:

```
 sudo apt-get install ubuntu-desktop 
```

---

