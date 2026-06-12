---
title: "'An Error Occured' while I was upgrading my XServer"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by Ubuntu Joe on 2008-01-18
Hey all,

So, I usually let Update Manager do its thing whenever it tells me I have new updates . . . but THIS time, no dice!  When trying to install the 'Important Security Update' xserver-xorg.core from version 2.1.2.0-3ubuntu8 to 2.1.2.0-3ubuntu8.1, I got this Error Message:

```
W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.2.0-3ubuntu8.1_i386.deb
  403 Forbidden
```

Whatevs.  So I try to do it in the Terminal with Aptitude, and I get this:

```
thom@Ubuntu-Joe:~$ sudo aptitude install 2.1.2.0-3ubuntu8.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "2.1.2.0-3ubuntu8.1"
The following packages have been kept back:
  xserver-xorg-core 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
thom@Ubuntu-Joe:~$ 

```

One last time I try with apt-get, and this:

```
thom@Ubuntu-Joe:~$ sudo apt-get install 2.1.2.0-3ubuntu8.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 2.1.2.0-3ubuntu8.1
thom@Ubuntu-Joe:~$ 

```

And that's when I gave up . . . HELP!!

---

### Post by Splinter on 2008-01-18
Same thing happens to me right now, found no solution yet. Anyone else knows?

---

### Post by Panzor on 2008-01-18
[http://ubuntuforums.org/showthread.php?t=671616](http://ubuntuforums.org/showthread.php?t=671616)
NineseveN's post worked for me.

---

### Post by Splinter on 2008-01-18
> **Panzor said:**
> [http://ubuntuforums.org/showthread.php?t=671616](http://ubuntuforums.org/showthread.php?t=671616)
NineseveN's post worked for me.

Yes, thank you Panzor, worked like a charm :KS

---

### Post by Ubuntu Joe on 2008-01-18
Guys for real, I totally just restarted my machine like 5 times playing with some of my mouse settings, and then the install worked.  So weird, and YES, I did try restartin before I posted the thread . . . I think it was fixed by magic.

[SIZE="6"]**SOLVED, BABY!!**[/SIZE]

---

