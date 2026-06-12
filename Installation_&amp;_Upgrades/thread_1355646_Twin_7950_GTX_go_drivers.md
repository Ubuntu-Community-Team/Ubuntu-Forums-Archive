---
title: "Twin 7950 GTX go drivers"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by mahorrocks on 2009-12-15
Hi

I am very new to the Linux experience

I have downloaded and installed Ubuntu after a marathon 5 days where I completely lost everything on my hard disks 

Its finally on, I have the 64 Bit desktop version, which is great BUT I have a problem installing nvidia drivers for my laptop, it is Geforce Go 7950 GTX and are twin sli. Everytime I install the drivers that are in the hardware part the screen flashes and the tells me to start in a low resolution as the video mode could not be used. It is fine in Vista and they work SLI but I would like to get this fully up and running so I can go Linux 

Any I ideas??

I downloaded the drivers from nvidia and  tried an install via Terminal using sudo su, but it either opens in a web browser or says that the permission is denied although I am in root


Can someone please help and end my agony

Mark

---

### Post by audiomick on 2009-12-15
Hi.
Have you read this?
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

It is a bit old, but I think it still applies.

I haven't had a problem for a while, but had to mess around with the nVidia setup on my old laptop.

Try installing from the hardware drivers, let it go to low resolution, then do
```
sudo nvidia-settings
```.

-You might find some stuff in here. Your card is mentioned as being supported
[http://ubuntuforums.org/showthread.php?t=1303982&highlight=sli+nvidia](http://ubuntuforums.org/showthread.php?t=1303982&highlight=sli+nvidia)

Also this. Be warned, it is a very very long thread.
[http://ubuntuforums.org/showthread.php?t=990978&highlight=sli+nvidia](http://ubuntuforums.org/showthread.php?t=990978&highlight=sli+nvidia)

When I set up my desktop around 18 months ago, Ithink the sli thing was just new an didn't work, but it must work by now.

---

### Post by mahorrocks on 2009-12-15
Wow,

Thanks Michael, it worked a treat and the graphics drivers are now in SLI. Im a happy bunny. That was a great help.

How do I get my Sound drivers and Bluetooth? Should I contact Rock direct to ask them what they are?

Loving Linux alot. Its alot faster, and looking forward to finally utilising my twin processors finally as I was too scared to leave the 32 bit Vista
:KS:popcorn::KS

---

