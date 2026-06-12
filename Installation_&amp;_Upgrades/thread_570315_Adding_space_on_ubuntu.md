---
title: "Adding space on ubuntu"
date: 2007-10-08
forum: Installation &amp; Upgrades
---

### Post by Meomix on 2007-10-08
i have 2 Hard disks 
A New one thats 80GB
And a Old one thats 75Gb 
the operating systems im installing are Solaris Windows and Ubuntu on the 80GB disk
the space has been split like this
Windows: 20GB
Ubuntu: 14GB at the moment ( 40 gb currently at a standstill )
Solaris: has taken the entire 75GB HD

I installed windows then ubuntu the ubuntu saw the windows partition and installed smoothly, then on to solaris solars saw windows but NOT ubuntu, the high risk that solaris would kill the ubuntu partition we installed solaris on the unstable 75GB
ubuntu and solaris are at a conflict they seem to think they are one partition which is causing chaos, solaris is installing at the moment on the 75GB HD it still seems to want to interfere with ubuntu on the 80GB disk
should i have installed solaris first if i did would ubuntu see it?
if ubuntu didnt see it should i put windows and solaris on the 80GB disk then have ubuntu take over the entire 75GB disk i need help as DAD that is fixing my computer is soon going to permanently delete ubuntu from the system!

---

### Post by jnorthr on 2007-10-08
just a wild guess here, is it possible that solaris 'sees' the ubuntu root partition on hda and tries to use it thinking that it is the root for solaris ? Do you really need solaris ?
Here is a howto that may give you some ideas : [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by Meomix on 2007-10-08
yes we need solaris installed for business work
it seems i was unsuccessful on installing ubuntu at all on the harddrive dad has gotten tired and has replaced the 80GB hard disk with only windows and solaris

i can only pray that the 75GB hard disk is still in my computer so i can install ubuntu there instead dad has given me strict rules that i cannot use the windows OS for "playing" the solaris OS i would have to spend hours hacking code just to get something to work there and so on and so on =;

---

### Post by jnorthr on 2007-10-08
Ouch !!
You can still burn a liveCD of ubuntu and you can then insert it into the Cd drive and reboot. Then you will have a taste of what ubuntu is like without installing it. Yes, it will run more slowly but everything will work enough for you to see if you like it before installing it on your machine, and you will not destroy any of your dad's work.:)

---

