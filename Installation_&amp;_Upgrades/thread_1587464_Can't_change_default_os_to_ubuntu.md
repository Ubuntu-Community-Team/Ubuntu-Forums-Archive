---
title: "Can't change default os to ubuntu"
date: 2010-10-03
forum: Installation &amp; Upgrades
---

### Post by SnedSneeden on 2010-10-03
So i upgraded my windows partition by doing a fresh install over the old one, but now it made windows the defualt os to boot on start up.. i cant figure out how to get to my ubuntu partiton to change this..

---

### Post by davec64 on 2010-10-03
> **SnedSneeden said:**
> So i upgraded my windows partition by doing a fresh install over the old one, but now it made windows the defualt os to boot on start up.. i cant figure out how to get to my ubuntu partiton to change this..


That's the trouble with Windows, it thinks it's the only OS!

Follow this tutorial and you can install Grub2 from a live CD:[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html")

I've assumed you're using 10.04 which uses Grub2.

Hope that helps!

---

### Post by SnedSneeden on 2010-10-03
Thanks a lot man, this worked like a charm!

---

### Post by davec64 on 2010-10-03
Glad to be of help! :)

---

### Post by shuhail555 on 2010-10-03
Hello all,
I just installed ubuntu 9.10 and facing the same problem mentioned above.
but the procedure didn't work for me.

Problem:
[COLOR=DimGray]*I use XP, now I installed UBUNTU successfully, but after rebooting the pc, it directly open with the xp. How can i get into my ubuntu?*[/COLOR]

---

### Post by drs305 on 2010-10-03
> **shuhail555 said:**
> Hello all,
I just installed ubuntu 9.10 and facing the same problem mentioned above.
but the procedure didn't work for me.

Problem:
[COLOR=DimGray]*I use XP, now I installed UBUNTU successfully, but after rebooting the pc, it directly open with the xp. How can i get into my ubuntu?*[/COLOR]

Welcome to the Ubuntu forums shuhai !

Please boot from a LiveCD, run the boot info script found below and start a new thread. Restate your problem and copy the RESULTS.txt into the post.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

If you are already on the LiveCD you can run the script and post it here. As a forum staff member I can start the new thread for you.

---

