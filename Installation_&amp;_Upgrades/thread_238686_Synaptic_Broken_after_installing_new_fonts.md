---
title: "Synaptic Broken after installing new fonts"
date: 2006-08-18
forum: Installation &amp; Upgrades
---

### Post by Aljn on 2006-08-18
Hi everyone,
Earlier today I enabled the "universe" and "Multiverse" repositories (as per the repository how-to) which was all cool, but after my computer updated, my fonts looked like crap (which I know now it's an issue with my compiz/XGL) so, I went to the thread [ HOWTO: quickly improve X11 font rendering]("http://www.ubuntuforums.org/showthread.php?t=180647") 

Now, after I completed those steps, I noticed that Firefox,Gaelon and Synaptic had been removed and that the "Add/Remove Program" option was gone from my Applications menu (I'm sure it uninstalled other things as well) Ironically, my fonts still look like rubbish and now my linux is pretty broken.

I managed to install firefox again (which is how I'm making this post) but I tried installing synaptic and the terminal said it was already installed, so I removed it, then reinstalled it, that worked, but it still won't launch when I click on it in the Admin Menu, I have rebooted numerous times to no avail and am at a loss as to why it happened and how to fix it.

I'm really quite annoyed by this and would like to know how/if I can roll back my ubuntu to before I updated (because it didn't add a new image, just altered my packages) or at the very least, get my Synaptic, the Add Remove Programs, my "software options" and all that other stuff working again.

Edit: Also, I tried the following in the terminal and this is what I got:
```
alan@alan-desktop:~$ sudo synaptic start
synaptic: error while loading shared libraries: libvte.so.4: cannot open shared object file: No such file or directory
```


Thanks in advance.

-AP

---

### Post by Robin Mulder on 2006-08-18
Try this:

```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```

See also [http://www.ubuntuforums.org/showthread.php?t=238668](http://www.ubuntuforums.org/showthread.php?t=238668)

---

