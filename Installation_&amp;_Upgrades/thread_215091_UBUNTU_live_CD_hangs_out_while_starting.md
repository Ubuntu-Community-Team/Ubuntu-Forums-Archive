---
title: "UBUNTU live CD hangs out while starting"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by kami on 2006-07-13
Hello 
I got Ubuntu today.
While I put cd into cd drive it hangs out on "HP Linux Printing and Imagining System" .
I have 633 Mhz Celeron, 128 mb ram, motherboard on VIA chipset and don't
have any HP printer.
Can somebody help me with this problem ?

---

### Post by dlmmsu on 2006-07-13
I had this problem as well. It turns out that the live CD installation requires at least 192 Mbyte of RAM. If you have or can 
get the Alternate install CD use the text mode install. This is meant for low memory systems (as if 128 Mbytes of memory isn't enough).

---

### Post by dlmmsu on 2006-07-13
Oh I forgot, At work had the same problem with a vanilla pentium 166, with 128 Mbytes of RAM PC104 SBC. Dropped to the Alternate install disk using text mode and the installation (while dog slow) went through with no problems. 

Good Luck 
D

---

### Post by kami on 2006-07-14
HI
I don't have cd-rw but today I might have 256 mb of ram for few days and I'll test UBUNTU
on it and let everyone know if I started with it.
Thanks.

---

### Post by kami on 2006-07-17
Hello everyone again. Unfortunetly I doesn't start with my pc. I guess it needs faster  processor or more than 256mb of RAM with 633mhz Celeron .

---

### Post by crouton on 2006-10-06
Try the server CD.  It has been much more reliable in terms of installation completion than the live Desktop CD (in my experience, and I've done a lot of installs on various machines.)

Once you've installed the Server, you can login, edit your sources (see other threads on this), do an apt-get update; apt-get upgrade and then likely an apt-get install ubuntu-desktop.  That should put you approximately at the same end result as the live Desktop install.

---

### Post by kami on 2006-10-06
Hello all

 Finally I start ubuntu live cd @ 1200 mhz celeron and 256 mb ram.

---

