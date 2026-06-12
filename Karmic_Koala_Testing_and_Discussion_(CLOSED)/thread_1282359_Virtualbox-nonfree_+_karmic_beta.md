---
title: "Virtualbox-nonfree + karmic beta?"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by chinamusic on 2009-10-04
Anyone have any luck integrating the non-free version of virtualbox with the latest Karmic (9.10) beta?  The opensource version doesn't work for me since I need USB support.

---

### Post by Beyecixramd on 2009-10-04
Thank you. I wish you luck too.

---

### Post by chinamusic on 2009-10-13
Update:

Ultimately, I had zero luck trying to get the non-free version working with Karmic beta.  So I switched back to Jaunty (9.04) and used the canned binaries from the virtualbox site.  I suppose I'll try again once Karmic actually releases and hope that virtualbox binaries become available.

---

### Post by sparky64 on 2009-10-13
I'm running 64 bit version. everything works perfect including 3d support.
usb works as well as picking up my home folder ( had trouble in jaunty).

---

### Post by howefield on 2009-10-13
> **chinamusic said:**
> ..I had zero luck trying to get the non-free version working with Karmic beta.

Like others here, my install seemed to go fine, maybe someone can help if you describe the problem.

> I suppose I'll try again once Karmic actually releases and hope that virtualbox binaries become available.

That'll fix it :)

---

### Post by ChrisGaeth on 2009-10-13
Works fine here as well on 64-bit.  What kind of issue are you having?

---

### Post by chinamusic on 2009-10-14
How are you guys running it on Karmic?  There are no binaries for the non-free version available yet.  The free version does not support USB.  That's a show stopper for me.  The free version did indeed run on my 64-bit karmic install, though.

---

### Post by xebian on 2009-10-14
> **chinamusic said:**
> How are you guys running it on Karmic?  There are no binaries for the non-free version available yet.  The free version does not support USB.  That's a show stopper for me.  The free version did indeed run on my 64-bit karmic install, though.

Just get the jaunty version and installs fine in karmic.

---

### Post by howefield on 2009-10-14
> **chinamusic said:**
> How are you guys running it on Karmic?

As soon as the download for Karmic is available, I'll use it, in the meantime, the Jaunty version is running sweet as a nut.

---

### Post by benjamimgois on 2009-10-14
> **sparky64 said:**
> I'm running 64 bit version. everything works perfect including 3d support.
usb works as well as picking up my home folder ( had trouble in jaunty).

I'm running Karmic 64bits too, and almost everything works fine with virtualbox. My only problem is to access my shared folders, it simple doesn't work. Can you give me some instructions ?

---

### Post by howefield on 2009-10-14
> **benjamimgois said:**
> My only problem is to access my shared folders, it simple doesn't work. Can you give me some instructions ?

Host and Guest Integration video at [http://www.virtualbox.org/wiki/VirtualBoxTV](http://www.virtualbox.org/wiki/VirtualBoxTV) explains how to do this.

Have you installed guest additions ?

---

### Post by surfed on 2009-10-14
debs are up for karmic:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by benjamimgois on 2009-10-14
> **howefield said:**
> Host and Guest Integration video at [http://www.virtualbox.org/wiki/VirtualBoxTV](http://www.virtualbox.org/wiki/VirtualBoxTV) explains how to do this.

Have you installed guest additions ?


Thanks for the Video, now it's working just fine. I wasn't looking for \\vboxsrv\

---

