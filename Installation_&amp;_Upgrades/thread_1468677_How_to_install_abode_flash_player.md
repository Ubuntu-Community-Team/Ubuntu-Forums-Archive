---
title: "How to install abode flash player"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by James161324 on 2010-05-01
Sorry for the noob question. But how do i install abode flash player on Ubuntu 10.04. I was on able to figure out how to do it. 

Thanks in advance

---

### Post by jumbotron on 2010-05-01
hi there...
 
```
$ sudo aptitude install flashplugin-nonfree
```

---

### Post by Mutt77 on 2010-05-01
Or for the noob, Ubuntu Software center in the search type flash. Then install Flash player 10.

---

### Post by kamikazepsi on 2010-05-01
if you're on a 64 bit machine, you'll want to install the 64 bit version for the best results. 

-Remove any current versions of flash
-Download the 64 bit flash from adobe and note the folder location
-Open terminal and navigate to that folder:
> example: cd /home/acer/Downloads
-Untar:
> sudo tar xzf libflashplayer*
-Move the file:
> sudo cp libflashplayer.so /usr/lib/mozilla/plugins/

Then go test in youtube or something.

---

### Post by Sef on 2010-05-01
Before downloading from the Ubuntu Download Center make sure that multiverse is ticked.  (Edit > Software Sources)

---

### Post by James161324 on 2010-05-01
Thanks everyone.

---

