---
title: "Dash"
date: 2017-06-17
forum: Installation &amp; Upgrades
---

### Post by Reddoug on 2017-06-17
Hello

I have installed 17.04 server and I used sudo apt-get install --no-install-recommends ubuntu-desktop to have GUI. I didn't want office suite and other unnecessary programs. I have been tweaking things but the one thing I am having trouble getting to work is when I try to search in dash it will not find anything, "Sorry there is nothing that matches yur search"  If I want to start gedit, I have to start it from terminal. 
I have been doing a lot of web searching but not able to find a solution. 

Thank you for any help, Doug

---

### Post by ubfan1 on 2017-06-17
gedit is an X program. Servers do not come with X installed.  What are you trying to do?

---

### Post by Frogs Hair on 2017-06-17
There may have been recommended package/s that facilitated the search function in dash.   Zeitgeist comes to mind , but I can't be sure without knowing all the recommended packages.

---

### Post by oldos2er on 2017-06-17
If you want a minimal desktop environment, try lubuntu-desktop.

---

### Post by deadflowr on 2017-06-17
Try reinstalling just unity.
```
sudo apt-get install --reinstall unity
```
that should pull in all packages only related to unity including the dash.
perhaps somewhere along the lines of running the no-install-recommends on the ubuntu-desktop meta-package caused it to omit a key package or two for unity.
(I think it's not likely, but you never know)

---

### Post by Reddoug on 2017-06-17
Thank you for the replies.

I had done the same installation with 16.04 server with --no-install-recommends and did not have to do anything to get dash to work. I had upgraded to 16.10 and then went to 17.04 and caused problems so I did a fresh install of 17.04 and trying to get it to work like 16.04 did. Maybe something changed with 17.04 that I haven't figured out causing my problems. I just like working with the server version better and do not need all the extra programs that come with a full install. This isn't a production server, I do have my personal home website running on it back ups and I have back ups backed up to a Samba server also so if I crash this I still have my files and not out anything but time. 

Thanks again for the replies, Doug

---

