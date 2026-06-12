---
title: "My System uses always ca. 30% for Software Interrupts"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by Tikalix on 2007-05-09
Hello.

I'm not new to Linux and normaly I find my answers with google, but this time I go crazy.
 
I "tuned" my little MultmediaPC from Suse 10.0 to kubuntu 7.04 and everythig works well. There is only one thing I do not understand. Why is my PC never idle even if nothing is to do?

top always look like that:
0.3%us, 5.3%sy, 0.0%ni, 59.3%id, 0.0%wa, 0.0%hi, **35.1%si**, 0.0%st 

**si** appears to stand for *"The amount of time the CPU has been servicing software interrupts"*. But why does my system **always** need around 35% to do that? My other PCs alwas have 0% si.

I looked in dmesg and every logfile I could imagine but didnt find something suspicious. Is there a way to find out which software causes this behaviour?

I already tried to stop some programs by hand. If I stop kdm the value for si goes down to 4% but [B]never[B] to 0. So i suggested, that my graphic could be the problem and i tried "dpkg-reconfigure xserver-xorg" but this didnt change anything.

Now I dont know anymore where to look... Please help. What can I do?

---

