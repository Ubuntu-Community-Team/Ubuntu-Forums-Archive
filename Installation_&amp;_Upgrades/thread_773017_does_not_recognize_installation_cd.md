---
title: "does not recognize installation cd"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by khbrady on 2008-04-28
Hello -- I just installed edbuntu 8.04 and came across a problem.
Trying to play a video with the movie player, it indicated that I needed to install 2 gstreamer packages. While installing I got a message "install edbuntu 8.04 hardy heron i386 cd now" the problem is I have no such CD.
If I followed the instructions properly, I started with the ubuntu desktop install and added the edbuntu add-on CD. I tried both CD's and it does not think either is the "edbuntu 8.04 hardy heron i386 cd" 

is there a way to force the package install to not look for a CD ?
this happens if I use synaptic directly or if it tries to load the codesec from the movie player directly
thanks

---

### Post by Pumalite on 2008-04-28
Go to your /etc/apt/sources.list and comment out the CD.

---

### Post by khbrady on 2008-04-28
Thanks so much. I see multiple references to the CD ROM so I suppose I comment them all out. I assume there is nothing on the CD that won't be available as a download ?

thanks

---

### Post by Pumalite on 2008-04-28
No. But if you need it in the future, all you have to do is enable it.

---

