---
title: "bootup/installed boot up problems"
date: 2006-09-24
forum: Installation &amp; Upgrades
---

### Post by mender of fences on 2006-09-24
Yo, 

AMD Sempron 3000+
NVIDIA GeForce 6600 GT
1 gig ram
uhhh, some old daytek monitor
and a bunch of this 'n' that, which includes 1 cd/rw and 1 dvd/rw

Anyways...
I don't think this problem has been posted here yet, and I hope it is a unique one so that no one gets upset with this post being at the top *again*. The problem is that on the live cd boot from my normal windows xp( >:x ) I would get up to the first screen of the start up where you see the black/orange/brown backdrop and that loading window pops up... I don't get much out of that because it freezes at that point, no movement whatsoever... So anyways, I figure it is just this live cd dealy and I install it.. (I hate windows)
So I get through the install in OEM fashion with no hangups, and I make up the password, etc... I figure it just does a lot of the hardware stuff on its own.. (may be the problem?) So I have a parition of Windblows and Ubuntu, I start up the Ubuntu (non-recovery/non-kernal) and I give that a whirl, poof, freezes at the login screen. No mouse reaction or anything... 

And that is where I stand, now, if you would be so kind? :x

---

### Post by whizbaby on 2006-09-24
Let me guess: your HD is a SATA?

---

### Post by mender of fences on 2006-09-24
I figure it is, an ATA...?

---

### Post by whizbaby on 2006-09-24
O.K. then it's another problem.
When seeing the frozen login screen, does *ctrl-alt-F1* give you a terminal? If not, can you start another live system (e.g. knoppix 5) and access your HD to post your /etc/X11/xorg.conf (not this of the live system of course)? I suspect your monitor...

---

### Post by mender of fences on 2006-09-24
Everything becomes non-responsive, and yes I to think it is the moniter or the vid-card.. Mostly because of the fact that on the boot up off the live cd the res was pretty high, I can only go up to 1280x1024.. And I believe that the starting res is 17xx something, yes?

---

### Post by mender of fences on 2006-09-24
So I hooked up a slightly older(could be newer) monitor that I had stashed away, a Samsung SyncMaster 15GLe.. Pretty much the same results... I figured the brand might be better recognized :x

---

### Post by whizbaby on 2006-09-24
Can't find this monitor on any linux hardware compatibility list (your graphics card is). The xorg.conf still is of some interest.

---

### Post by mender of fences on 2006-09-24
I will try it then, but just to clarify, I only freeze up or choke up on graphical pages... So I think it is pretty straight forward that something is wrong there, but, that might be the case... I will update you with the info in a few

---

### Post by mender of fences on 2006-09-24
It appears it may be a while before I can try a different Distro -or live cd, rather- so to make use of them time I will name off the other odds and ends... The hard drive is Maxtor ATA 120GB, the cd/rw is some cheesey 'compact disc [rewritable] Ultra Speed', (is what it says on the thing) and the DVD/rw is an LG so n' so. -EDIT- Forgot, keyboard is a media dealy by logitech, and the mouse is a gaming logitech mx518... Also by logitech. Lastly, my motherboard is a winfast K8S 755A. :x

Also, is it possible to access this info in the ubuntu terminal? or even something I was wondering is if I can change the resolution before the boot up in that command prompt?

---

### Post by mattbatt on 2007-12-02
So i just had to replace my mobo from an asus k8v se deluxe (agp slot died !?!) and I got the winfast k8s 755a and now I get the exact same problem as this guy.  It hangs on boot with the live cd even the newest ubuntu.   I had ubuntu on this computer before I changed the mobo and now I cant even get the live cd to boot.  the only thing that I have changed is the mobo.

---

