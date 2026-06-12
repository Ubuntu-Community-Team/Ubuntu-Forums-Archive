---
title: "Failed to fetch...error. Help"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by GARoss on 2009-10-02
Failed to fetch [http://ubuntu.osuosl.org/ubuntu/pool/main/t/totem/totem-common_2.28.1-0ubuntu1_all.deb](http://ubuntu.osuosl.org/ubuntu/pool/main/t/totem/totem-common_2.28.1-0ubuntu1_all.deb) 404 Not Found

I get this error (twice) while trying to update from Ubuntu 9.04 AMD64 to Beta Karmic Ubuntu 9.10 AMD64 using the terminal. Whatever it is, it's only 224k or so but it's a show stopper.

Any ideas?
Thanks

---

### Post by hotstovejer on 2009-10-02
Right now, the repositories are slammed. I would try updating/upgrading a little later today. On any day where there is a release, and lots of updates around it (Which seems to be the case today, since the beta dropped yesterday, but I didn't start getting updates until today), you will get this.

Hope this helps!

Jeremy

---

### Post by GARoss on 2009-10-02
It seems to of downloaded everything except that & it's a very small file. It just seems weird.

---

### Post by kansasnoob on 2009-10-02
I'm reasonably certain that the servers are just swamped!

---

### Post by GARoss on 2009-10-02
Okay. I'll try tomorrow.

BTW. 
Will I need to re-write GRUB for my dual boot or will it be re-write during the upgrade? Right now it says Ubuntu 9.04, etc & XP.
Thanks

---

### Post by kansasnoob on 2009-10-02
> **GARoss said:**
> Okay. I'll try tomorrow.

BTW. 
Will I need to re-write GRUB for my dual boot or will it be re-write during the upgrade? Right now it says Ubuntu 9.04, etc & XP.
Thanks

If you're upgrading a Jaunty w/legacy grub it'll still be legacy grub so you should see little change other than the updated Karmic kernel.

If you're upgrading a Jaunty w/grub2 you'll still have grub2 and I haven't tried that yet, but you may have to run "sudo update-grub" to grab Windows, but I doubt it.

---

### Post by kansasnoob on 2009-10-02
Oh, you may be presented with a prompt asking if you want to keep your old menu.lst (or grub.cfg) and you'll have options. I always choose to compare before I decide.

I'm still just learning grub2!

---

### Post by GARoss on 2009-10-03
Success! The update picked up where it left off without a glitch this time & all went well.

As for my concerns about my dual boot & GRUB; GRUB was re-written for Karmic 9.10 & I had no problem re-booting. 

So far, so good.:)

---

