---
title: "Problem upgrading to 8.10 with dual nvidia cards"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by Mikeyp926 on 2008-11-18
Hi everyone,
  I've been using 8.04 without any major problems for a few months now and really enjoying it.  A few days ago I decided to upgrade to 8.10.  I did this through the recommended "network" upgrade.  Everything seemed to go smoothly, and there were not any errors during the installation.  My pc rebooted fine and grub worked normally.  I selected the newest kernel, and the loading screen with the orange bar worked fine as well.  However, once that was complete instead of seeing a login screen I was faced with a black screen and a login prompt on a command line.  I can login fine, but no matter what I do I can't get any type of graphical interface.
I've spent the last couple of days looking stuff up online and trying to figure out what to do, but still no luck.  Any help/advice/ideas would be greatly appreciated.
Whenever I try to run "startx" from the cm, I get "(EE) No devices detected"  When I look in the log file, there are two lines listing both my video cards and saying something like "two possible primary devices" or something like that.
I've read some stuff online about changing the xorg.conf file, and have tried a few suggestions but they have all failed.  
When I run "lspci" both of my video cards show up correctly and are identified correctly.
My system info,
    Athlon 3800 x2 dual core, 2 gigs of ram, 2 nvidia 7600 vid cards.  I have been triple booting with xp, vista, and ubuntu, and that has all been working fine.  8.04 ran without a problem, so I don't think it's an issue with my setup.  Also, I think i'm using the 177 nvidia drivers, but i've tried using other ones but they haven't worked either.
Alright, thanks again for reading and for your help!   Is there any more information you guys need?
Thanks!
  Michael

---

### Post by Mikeyp926 on 2008-11-19
Anyone have any ideas?
Is this the right place to post this? or should i ask somewhere else?
Any help at all would be much appreciated.
Thanks!

---

### Post by Mikeyp926 on 2008-11-19
I've been stuck working on this for a few days now and am getting kinda frustrated.   Does anyone have any ideas for what I should try?

I've seen alot of similar problems, but usually the solution involved specifying the BusID in the xorg.conf file.  I've tried all these different solutions, but nothing has worked.  I'm not real familiar with the structure of this config file tho, so any help there would be much appreciated.  Has anyone had a similar problem and fixed it?  An example xorg.conf file that works for dual nvidia cards would be awesome.
I'd appreciate any response at all.

---

### Post by October_V on 2008-11-19
I wish I could help you Mikeyp926.
I have re-installed 8.10 3 times now, when I get the vid drivers updated it gives me the text only log in.
All teh methods I have tried have not helped. I have a pair of the 8800gts 640's.
I hope this gets picked up too.

---

### Post by Mikeyp926 on 2008-11-19
Thanks for the reply!
I've been doing quite a bit of research into this problem online, 
one site I found that seemed helpful is 
[http://lenss.nl/2008/11/ubuntu-810-nvidia-driver-trickery/](http://lenss.nl/2008/11/ubuntu-810-nvidia-driver-trickery/)

Unfortunately even after I manually changed my xorg.conf file I still recieved the same error as before, but I've read about alot of people
that were able to get things working by following the instructions in that website.  Maybe this will help you?
Otherwise I'll guess we'll just have to wait until they get this sorted out.  but again, thanks for the reply.

---

