---
title: "no support for asus m2v mainboard"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by enchesss on 2007-04-19
Have tried several versions of ubuntu for the asus m2v mother board and non work:

Mandrake works but is unable to detect a network

have tried these versions of ubuntu: they all stall during installation so there is no chance to download drivers or patches.

Worse is that there is often no error massage or log.

systen is:

AMD athlon64  X2
asus m2v main board
nvidia 6200 graphics
 
(errors or the result is in brackets)


Dapper 6.06 kubuntu: - stalls at network detection can not find it and wont settel on firewire.

Edgy 6.10 cd version: - stalls after initall kubuntu symbol then black screen with words "not supported" in yellow.

Edgy 6.10 alternative dvd - stalls at a kernel promt but does not allow input.

Ubuntu 6.10: - get initial sound after balack installation screen but then stalls,


Can anyone help ? im a newbie !

p.s. have used ubuntu install on intel D with asus p5 motherboard and it works like a dream so teh installation dvd is ok for intel mainboard/s but will not work with AMD Asus m2v mainbpard!!!!!!!!


cheers iain

---

### Post by Toadmund on 2007-05-06
My brother just got this board in the goal of making himself a dedicated Linux box, it's being a big fight every freakin' step of the way. ](*,) 
First there was no internet, he got it solved through his ISP somehow.
Now he has no sound (ALC660) ](*,) 

What next? I don't know, but he's got a useless box and M$ is looking good to him right now.

How does he solve his audio problems? I have been looking everywhere.
](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by guillaumeavril on 2007-08-15
Hi!

There with a bug with the m2v motherboard, linux will freeze after a certain amount of time.
The solution is to add pci=nomsi at the end of the kernel boot line.
I hope that it will help you :)

---

