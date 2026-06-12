---
title: "New kernel headers messes up my menu.lst"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by Luggy on 2007-05-25
I had two harddrives in my computer, hd0 Gentoo on sda and hd1 Ubuntu on sdb. At one point in time I removed my Gentoo harddrive making Ubuntu hd0 and sda. I also got k7 kernel headers.

Now, everytime I update to new kernel headers my menu.list changes and tries to load Ubunto off of hd1 and sdb. If I forget to make the change before I reboot I have to use a live cd to fix the menu.lst.

What can I do to fix it so that I don't have to manually change my menu.lst anymore?

---

### Post by n8bounds on 2007-05-25
edit the menu.lst file and change the line from
```
 # groot=(hd1,0) 
``` 

to something that makes sense for your new setup, like (hd0,0) or something

then do a 
```
 sudo update-grub 
```

shouldn't happen anymore

---

