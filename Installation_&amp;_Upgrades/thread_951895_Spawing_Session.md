---
title: "Spawing Session"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by getnripped on 2008-10-18
Well here is a new issue that I can't fix...

When I open Virtual Box to use my windows apps I now get the Spawning Session window that never does anything. I have searched on Google and found the "fix." 

```
/etc/init.d/vboxdrv setup
```

After that is done it is supposed to read this:
```

* Stopping VirtualBox kernel module                                         
*  done.
* Recompiling VirtualBox kernel module            
```                             


Instead it looks like this:

```

* Stopping VirtualBox kernel module
*  done.
* Recompiling VirtualBox kernel module                                         
* Look at /var/log/vbox-install.log to find out what went wrong

```

When I attempt to view the log I can't open the location. Any ideas?

---

### Post by lkraemer on 2008-10-18
I had the same problem and I used:
sudo /etc/init.d/vboxdrv setup

to recompile.

lkraemer

---

### Post by getnripped on 2008-10-18
:guitar: I finally got it figured out! YAY! Here is what I had to do...

step 1:
```
sudo apt-get autoremove virtualbox --purge
```

step 2:
```
sudo /etc/init.d/vboxdrv setup
```

Step 3:
Re-download (AMD64) 1.6.2 version of VBox.

For some reason this last update on the Kernel threw everything off. But using the 1.6 version of Vbox on this updated Kernel works fine :)

---

### Post by ke4ram on 2008-10-18
I just reinstalled the package... worked ok, seemed the simplest. 

Anyone have any idea what caused this?

---

