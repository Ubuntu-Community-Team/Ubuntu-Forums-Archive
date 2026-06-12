---
title: "Cannot load gdm, CRASH at boot with upgrade to 9.04"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by khm on 2009-03-18
So I just upgraded to Jaunty from Intrepid (*update-manager -d*).  Everything went smoothly, except at some point in the middle, I kept getting warnings like this:

```
cannot open display: 0:0
```

I went ahead and finished the distro upgrade. I rebooted machine and I never saw a login screen. The screen immediately went to a terminal login, but very quickly crashes (not enough time to actually login).

I did see a quick message saying something like "*kdm failed to load. it is not the default display manager*".

I'm not sure why it's using kdm, because I'm using gnome.  I may have installed kde a while back, but it was not set as default.

It looks like it is not a system crash really, but more of a display issue.  I can't seem to be able to actually login blindly, but I noticed that if I press the power button on the PC, I can actually see the ubuntu logo along with the progress bar.  I actually see about 5 of them, but they are very jumbled up.

I booted to a live cd (8.04) and mounted my filesystem, then *chroot* to the filesystem.  I tried to *dpkg-reconfigure gdm*, but get the following error:

```
root@ubuntu:/# sudo dpkg-reconfigure gdm
invoke-rc.d: initscript gdm, action "reload" failed.

```

I tried running gdmsetup, but got this error:

```
root@ubuntu:/# gdmsetup --help
No protocol specified

```

Also:

```
root@ubuntu:~# xauth list
kmonday-desktop/unix:1  MIT-MAGIC-COOKIE-1  c53373a98d2c433a7eda7a857c43aa23
kmonday-desktop/unix:4  MIT-MAGIC-COOKIE-1  19915c1994ca0e1e16f67cf21a4c052b
kmonday-desktop/unix:5  MIT-MAGIC-COOKIE-1  7e63febf36af80de0507651967b98004

```

NOTE: I did try *export DISPLAY=:0.0*, but the results were the same.


Any ideas?

---

### Post by markbuntu on 2009-03-18
You really should have upgraded to Intrepid and been fully updated before upgrading to jaunty. You need a jaunty live cd to fix it.

---

### Post by khm on 2009-03-18
> **markbuntu said:**
> You really should have upgraded to Intrepid and been fully updated before upgrading to jaunty. You need a jaunty live cd to fix it.

Oops, that was a mistake... I actually did upgrade from intrepid. (my mind's still stuck in the past)  Fixed the original post.

---

### Post by markbuntu on 2009-03-18
You can try, from recovery boot

apt-get update

that may update your gdm but it looks like you have some other issues. A jaunty live cd might be your best bet at this point. (alpha 6 just came out)

---

### Post by Rolle_Pollie on 2009-03-18
This sounds like what I had happen to me today (somewhat).  

I already had updated everything since 2 days ago or so.. so should have been running 9.04.06

Did a sudo apt-get update (it fetched about 180)
sudo apt-get dist-upgrade

asked to restart.

Computer restarted, saw the new Ubuntu loading screen (which is aesthetically pleasing) then after the computer freezes between the ubuntu loading and when then splash screen should show up.  

Couldn't take a screen shot--but this is the best picture i could come up with.

[http://s5.tinypic.com/14lh4s0.jpg](http://s5.tinypic.com/14lh4s0.jpg)  
(of course the background is black, the 5 small things at the top look like very minature ubuntu loading screens-blurred of course)

Attempted to go back to previous kernels--result was unsuccessful.  All kernels froze at the time the splash screen should have appeared.  

Attempted to recover--result was that was able to log in as root, however, not sure exactly how to connect to an access point and download any new updates that may fix this problem.  

Attempted to boot from 8.04 live cd--result was successful (obviously).  Copied a couple files from the filesys to windows...but not sure which files i should really check out.  

I did see some error about synaptics... wrote it down:

Synaptics was reset on resume.
See synaptics-resume-reset

also:

MMC0: Unknown controller version(2)

---

### Post by khm on 2009-03-23
Well, I did a clean install after backing up and everything is fine now.

---

