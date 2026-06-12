---
title: "LAMP install from 6.06 LTS ?"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by fulltilt on 2006-07-06
Hi,

I got my CDs in the mail the other day (5 x v.6.06 LTS for your PC), but I don't seem to have an "install server from cd" option that I have read about.  I just checked my ordering and there only seems to be one version of 6.06 that you can order, but there are 2 different images you can download - is this right ?

Can I only get workstation CD's in the mail ?

I want to install Ubuntu on an intranet where internet access is difficult to come by, so the apt-get doesn't work well.

Can I install all the server components from the CD ?


I've been googling for a few hours and been searching these forums as well, but to no avail.


Ubuntu/Linux newbie needs help !!!

---

### Post by jonrkc on 2006-07-12
(I commented on your comments about "zero reply" a while ago, so I thought I'd look up your own zero-reply post.)

I'm almost 100% sure you can install all the server components from the basic Ubuntu CD.  The server version is of course much smaller.  I've seen several posts where users with limited hard-drive space have got the suggestion to use a server installation and then add just whatever else they need/want (such as X Window system) after that.

Not running a server myself, I don't know what configuration you'd have to make, but you probably know already.  

In other words, I think you have the server package already, but it's encumbered with all the desktop stuff.  

I don't know if that's even helpful, but it's about the best I can do, with no server experience.

---

### Post by fulltilt on 2006-07-12
Thanks for the reply jonrkc :)

To answer some of my own questions ... 

> 
Can I only get workstation CD's in the mail ?
I went over the options a few times and it seems like you can only get the workstation version

> 
I want to install Ubuntu on an intranet where internet access is difficult to come by, so the apt-get doesn't work well.

I downloaded the server CD and installed it.  I'm not too keen on the "command line only" interface, but I do see that apache and mySQL are running ... 

> 
Can I install all the server components from the CD ?
I couldn't get apache to install from the workstation cd at all. I got the feeling that apt-get couldn't find the packages on the cd so tried the internet and couldn't get access.


And on to jonrkc's suggestions ... 

> In other words, I think you have the server package already, but it's encumbered with all the desktop stuff. 

Yeah, I would really like an Xwindows/workstation style desktop with Apache, mySQL, PHP web services running in the background. Basically so I can work on the machine and serve webpages at the same time <- that answer is probably posted here but I haven't looked yet.

I think with both the workstation and server cd's I will have all the components I need without the need for internet access.

---

