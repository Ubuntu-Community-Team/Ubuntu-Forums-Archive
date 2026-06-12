---
title: "Crash during install of Ubuntu 8.1 Ibex"
date: 2008-09-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dakkar9999 on 2008-09-22
Hello,

as I was getting my feet wet in the linux world, I had installed Ubuntu 8.04 through wubi.  It was working fine, except it hanged a few times.  I suspect the video card (ATI X1650) but I do not know if there is a way to prove it.  Fast forward to version 8.1

I followed the instruction to upgrade using the command line.  No problem.  While it was installing, I went ahead and tried to close a program that was still open (Firefox I believe).  It caused the computer to hang.  I still suspect the video card because there seemed to be a few corrupt pixels.  

Now my problem is as follow.  It does not boot properly.  I tried to boot in safe mode which takes me to a prompt (ask for user/password), but I don't know how to load the graphic interface.  If I try the fix boot, it does not seem to pick up any error.

Any suggestion either to roll back to 8.04 or to salvage 8.10?

Thanks!

---

### Post by overdrank on 2008-09-22
Moved to Intrepid Ibex Testing and Discussion :)

---

### Post by Tatty on 2008-09-22
> **dakkar9999 said:**
> Any suggestion either to roll back to 8.04 or to salvage 8.10?

If you want a stable system then I would recommend going back to 8.04 for now, and trying ibex again after it has had a final release (end of october).

Either way, it would be a good idea to back up any of your valuable data now before doing anything else.

As it crashed halfway through an upgrade, I suspect that you may struggle to get this up and running again without a re-install.  However you might want to try running:
```

sudo apt-get install -f
``` and see if that picks up where it got lost....

---

### Post by dakkar9999 on 2008-09-23
Did not help.  Ok, here a re a few error messages I could pick up.

"Cannot remove /var/lib/apt/lists/partial/* no such file or directory"
"Cannot remove /var/cache/apt/archives/partial/* no such file or directory"

when I tried the "sudo apt-get install -f"  I get could not resolve us.archive.ubuntu.com

when booting i also get "no final line in etc/fstab

then just a black screen.

If I do Ctrl-alt-del, it goes, "stoping gnome display manager" and goes on to a proper restart.

Should I just go back through the wubi install?

---

### Post by dakkar9999 on 2008-09-24
Well.  I did it again.  I started back from a fresh install of ubuntu 8.04 (using wubi) then did the upgrade to 8.1

Again, it hangs on startup.  First, it takes a long time when it hits activating swapfile (+-1min) but then continues.

After it gives an error message with "no final newline at the end of /etc/fstab"  but still contines

But, instead of going to the gui desktop, I get the user/password asked from the command line and it stays at the command line at the root of c:\

Any idea?

---

### Post by alphacrucis2 on 2008-09-24
> **dakkar9999 said:**
> Well.  I did it again.  I started back from a fresh install of ubuntu 8.04 (using wubi) then did the upgrade to 8.1

Again, it hangs on startup.  First, it takes a long time when it hits activating swapfile (+-1min) but then continues.

After it gives an error message with "no final newline at the end of /etc/fstab"  but still contines

But, instead of going to the gui desktop, I get the user/password asked from the command line and it stays at the command line at the root of c:\

Any idea?

How about typing init 5 or maybe startx?


You could try downloading the 8.10 ISO and installing from scratch.

[http://www.ubuntu.com/testing/intrepid/alpha6](http://www.ubuntu.com/testing/intrepid/alpha6)

---

### Post by dakkar9999 on 2008-09-25
Maybe Ibex is not fonctional with wubi at the moment?

---

