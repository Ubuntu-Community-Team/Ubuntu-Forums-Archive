---
title: "What is wrong with libc6?"
date: 2009-09-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by slakkie on 2009-09-28
As per title, what is wrong with that packages and the dependencies it brings with it?

I needed to pin that package to an alpha4 release: 2.10.1-0ubuntu8
I can upgrade every part of Ubuntu, but when upgrading libc6 I get the cursor of death problem. My machine stops/hangs at booting. Which is annoying to say the least. 


Since I am recovering from surgery I don't have the energy to troubleshoot the problem (I just want to use my PC atm). I'm fully aware of testing alpha's should be done by <fill in the arguments>, but I went into surgery running karmic..

---

### Post by VMC on 2009-09-28
> **slakkie said:**
> As per title, what is wrong with that packages and the dependencies it brings with it?

I needed to pin that package to an alpha4 release: 2.10.1-0ubuntu8
I can upgrade every part of Ubuntu, but when upgrading libc6 I get the cursor of death problem. My machine stops/hangs at booting. Which is annoying to say the least. 


Since I am recovering from surgery I don't have the energy to troubleshoot the problem (I just want to use my PC atm). I'm fully aware of testing alpha's should be done by <fill in the arguments>, but I went into surgery running karmic..

Karmic's in surgery too. :) There's a fully recovered patient called Jaunty you can use in the meantime.

---

### Post by slakkie on 2009-09-28
I have backups you know ;). I am running a6 with libc6 from a4.

Like said, I pin libc6, I just want to know why it breaks ;). When I unpin (if you will) I upgrade the libc6-family and stuff breaks. 
 
Maybe I should give it a try, boot some liveCD afterwards, go through logs and see if all makes sense.. Then restore the backup and wait for an libc6 update.

---

### Post by sports fan Matt on 2009-09-28
Im not sure, but libc6 doesnt solve the install issues and bad file descriptors with programs im installing like opera and thunderbird.  libc5..just wont install.

---

### Post by VMC on 2009-09-28
> **slakkie said:**
> 
I needed to pin that package to an alpha4 release: 2.10.1-0ubuntu8
I can upgrade every part of Ubuntu, but when upgrading libc6 I get the cursor of death problem. My machine stops/hangs at booting. Which is annoying to say the least.

I don't know what you mean by "pin". I don't have any problems upgrading libc6. Maybe hardware related. What specs do you have?

---

### Post by MKdx on 2009-09-28
This's probably related.. I kept getting some error about libc6 in installing Karmic from the dailies (alternative, normal and server) and from netinstall. I'll wait for the beta and see - unless we get something here.

---

### Post by slakkie on 2009-09-28
> **VMC said:**
> I don't know what you mean by "pin". I don't have any problems upgrading libc6. Maybe hardware related. What specs do you have?

You pin your packages by using /etc/apt/preferences:

```

$ cat /etc/apt/preferences
Package: libc6
Pin: version 2.10.1-0ubuntu8
Pin-Priority: 1001

```

The Pin-Priority says what apt will do with a package, remove it, downgrade it, etc etc. 

[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)
[http://wiki.debian.org/AptPinning](http://wiki.debian.org/AptPinning)
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html) (section 3.10)

I'm running on Intel hardware (Dell Latitude D630).

---

