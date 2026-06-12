---
title: "Did recent updates kill GTK/Gnome?"
date: 2009-11-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-11-11
Ubuntu is unusable!

[http://img260.imageshack.us/img260/4760/unusable.png](http://img260.imageshack.us/img260/4760/unusable.png)

---

### Post by Kevbert on 2009-11-11
Not here...which ones ???

---

### Post by Starks on 2009-11-11
No clue. I recall seeing  a pixbuf update last night. I doubt that's it though.

If anything, it might be something sour from karmic-proposed.

---

### Post by zika on 2009-11-11
Is this a question about Lucid or not?

---

### Post by Starks on 2009-11-11
> **zika said:**
> Is this a question about Lucid or not?
Yes it is. I would've posted elsewhere if it wasn't about Lucid.

---

### Post by zika on 2009-11-11
> **Starks said:**
> Yes it is. I would've posted elsewhere if it wasn't about Lucid.Sorry, I've seen You're using karmic-proposed and I've seen Karmic under Your avatar and presumed wrongly ... Mistake is solely mine.

---

### Post by Kevbert on 2009-11-11
If you can take a look at the bottom of your /var/log/dpkg.log file you should be able to find the problem package(s) (providing you have a means of navigating to the file, maybe via karmic?).  I've just upgraded to kernel 2.6.23-3 and still OK (touches head/wood...)

---

### Post by Starks on 2009-11-11
Meh. Too much effort. I'd do it if I didn't have to worry about using my laptop for class today. It's a lot faster to simply do a 15 minute root reinstall with my USB key.

---

### Post by dino99 on 2009-11-11
hi all,

wonder where i can view the last updates installed: is there a history logged ?

---

### Post by Kevbert on 2009-11-11
> **dino99 said:**
> hi all,

wonder where i can view the last updates installed: is there a history logged ?

See my previous post. All lines are time stamped.

---

### Post by Sarvatt on 2009-11-11
Looks like you're using intel graphics on xorg-edgers right now to me, theres a problem rendering alpha channels right now with the latest git version. Just grab the 11/06 deb from here if thats the case

[http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xserver-xorg-video-intel/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xserver-xorg-video-intel/)

edit: i reuploaded the 20091106 release as xserver-xorg-video-intel_2.9.0+git20091111.dbb68168-0ubuntu0sarvatt, let me know if that doesnt fix it.

---

### Post by VMC on 2009-11-11
> **Kevbert said:**
> See my previous post. All lines are time stamped.

Thanks for that tip. I don't think I have ever thought of looking at that log before. I like the time stamp. dpkg -l doesn't have one.

---

