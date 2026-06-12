---
title: "Problem with DAAP share in Rhythmbox/Karmic"
date: 2009-08-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by WonderStivi on 2009-08-26
I've installed Karmic Koala on two of my computers. Since 8.04 I've been using Rhythmbox with the built-in DAAP plugin. So far, this has worked without a hitch, but problems have emerged after upgrading to Karmic. I realise this is an alpha, but I'd still like to try to solve this problem. Well, if anyone here can help me, that is :P

All my music is stored on my "server". This is actually a regular desktop in my home office with all my music and movies. I play music on this machine on a regular basis, and use the ratings feature in Rhythmbox to create smart playlists. With the DAAP plugin enabled, I get my favorite music on all the other computers without having to pick them out on every other machine, as the smart playlists are shared over DAAP as well.

Now, since upgrading to Karmic on the server, I've had problems sharing my music. I have one other machine with Karmic, and have two running Jaunty. After upgrading to Karmic on the server, none of the machines have been able to play music from the server. The share is listed, but when trying to access it, Rhythmbox says "Retrieving songs from music share", and nothing more happens.

I've tried to create a new share on one of the Jaunty machines, and all the PC's in my network plays them fine. It's obviously something with Karmic, and on the server side, not the client.

I'd really appreciate it if someone would help me solve this problem. I've grown accustomed to using Rhythmbox, and while there probably are better alternatives, habits are hard to change.

Thanks.

---

### Post by ibuclaw on 2009-08-26
Thread Moved. :)

FYI, Karmic Koala isn't supported in the main channels until it is released in October.

---

### Post by WonderStivi on 2009-08-26
Sorry, didn't see the Karmic category. Still hope someone can help me :P

---

### Post by ViRMiN on 2009-08-27
I use Firefly Media Server (packaged under the old name, "mt-daapd") to stream my music to other machines on the network.  The clients are all Rhythmbox on a mix of Jaunty and Karmic and have no problems.  Worth a look, especially as it runs as a daemon.

---

### Post by LavianoTS386 on 2009-10-15
I'm also experiencing this problem on my computers. Anyone else?

---

### Post by motang on 2009-10-24
> **LavianoTS386 said:**
> I'm also experiencing this problem on my computers. Anyone else?
Me too, Laptop on 9.04 and Desktop on 9.10 and Tangerine won't connect up from 9.10 to 9.04 or from 9.04 to 9.10. :(

Found out you can setup a DAAP within Rhythmbox, but it's still not compatible between 9.10 and 9.04.

---

### Post by motang on 2009-10-24
Figured it out. If you have firewall then it will be blocked so you need to add port # 3689 to the firewall and allow the traffic in. It worked for me with the built in DAAP plugin for Rhythmbox, next I shall try it out with Tangerine.

---

