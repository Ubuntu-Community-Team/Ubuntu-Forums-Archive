---
title: "Ubuntu 6.06 Install Hang"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by p1r0 on 2007-01-07
Hi.

I have a new system and want to install Ubuntu on it. I have installed it many times before on differnt machines but now I get a very rare "error" and don't know what to do.
When I boot from the DVD (then the CD in case the DVD was bad) and I choose the "Start or Install Ubuntu" option it shows me Uncompressing the kerel....Booting the Kernell OK msg and then just hangs there. Not Even de reset button works I have to shut the systeme down.

Any Ideas???

My system:

Intel Dual Core 3.4
Intel DesktopBoard DQ965GF
1GB Kingston DDR2
HD Samsung 120GB IDE 7200rpm

Thanks in advance,
p1r0

---

### Post by andyrobo60 on 2007-01-07
You said that your system is new. Do you mean brand new. If so it may be a problem with your hardware. 

Try testing your ram by downloading and running memtest86.

---

### Post by teejay17 on 2007-01-07
Yeah, I'm having similar problems on my system, both with 6.06 and 6.10. [http://www.ubuntuforums.org/showthread.php?t=330118](http://www.ubuntuforums.org/showthread.php?t=330118)
I'm interested in seeing how this discussion develops; maybe there'll be a solution.

---

### Post by p1r0 on 2007-01-07
Yeap the system is brand new but I have already tested the RAM with memtest and nothing. And also I have WinXp SP2 running on it with no problems....

I saw a post about this probem being chipset related but with core 2 duo so I think it's no the same problem. 

I really hope to find a solution because I love Ubuntu but I also use Linux for work so if I can't get it up I'll have to install another one.

---

### Post by teejay17 on 2007-01-09
> **p1r0 said:**
> Yeap the system is brand new but I have already tested the RAM with memtest and nothing. And also I have WinXp SP2 running on it with no problems....

I saw a post about this probem being chipset related but with core 2 duo so I think it's no the same problem. 

I really hope to find a solution because I love Ubuntu but I also use Linux for work so if I can't get it up I'll have to install another one.
Same here. Everyone's been thinking it's a duo core problem, but I have AMD and ATI graphics card, but basically carbon copy of your complaint. Because of this little glitch I can't be on Ubuntu 100% of the time.

---

### Post by Volkster on 2007-01-09
this is my first time installing ubuntu on any computer.  i have a new system with a core duo/ati card.  i had the same problem, and while i was browsing the support forums, i left the install frozen where it was.  about 15-20 mins later, without touching it, it booted into the environment and the install was successful.

i cant offer anything other than that :(

---

### Post by teejay17 on 2007-01-09
> **Volkster said:**
> this is my first time installing ubuntu on any computer.  i have a new system with a core duo/ati card.  i had the same problem, and while i was browsing the support forums, i left the install frozen where it was.  about 15-20 mins later, without touching it, it booted into the environment and the install was successful.

i cant offer anything other than that :(
Hey, no problem. Welcome to the forum, and your input is appreciated. Now, a quick question: were you installing at the point it froze, or were you trying to just boot into live CD. The problem I'm running into is when I boot into LIveCD, just trying to see how Ubuntu works with my hardware.

---

### Post by p1r0 on 2007-01-10
So it's a Core 2 DUO, Dual Core and some AMD also.... GREAT!

It's a shame tha I can't even install it... And the problem is that I like it but once I install a different one I'm going to intall Ubuntu once they fix the bloody problem (if the they ever do)...

I'm really upset [-(

---

### Post by p1r0 on 2007-01-23
Just to let you know I've just finished downloding debian sarge (9GB) and guess what.....can't install it either.

This thing is really anoying.

---

### Post by teejay17 on 2007-01-23
> **p1r0 said:**
> Just to let you know I've just finished downloding debian sarge (9GB) and guess what.....can't install it either.

This thing is really anoying.
I'm just wondering what kind of video card you have? Would it be an ATI card by any chance?

---

### Post by p1r0 on 2007-01-24
> **teejay17 said:**
> I'm just wondering what kind of video card you have? Would it be an ATI card by any chance?

No, I have the Intel Graphics Cards that's onborn with the mobo.

I'¡m going to try mandriva this days and I let you know how it went.

---

### Post by teejay17 on 2007-01-24
> **p1r0 said:**
> No, I have the Intel Graphics Cards that's onborn with the mobo.

I'¡m going to try mandriva this days and I let you know how it went.
Oh, okay. Yeah, see how Mandriva goes and let me know; I might have to try that.

---

### Post by p1r0 on 2007-02-22
I'm posting to let everybody know that I've found a partial solution to my problem.
I've got Mandriva 2007 installed. To do so you have to add "all-generic-ide" (without the quotes) to the command line. And after installed you have to start the recue disk with the same option and edit the lilo.conf file and add all-generic-ide to the boot parameters and then re-install lilo.

Hope this helps-

---

### Post by teejay17 on 2007-02-22
> **p1r0 said:**
> I'm posting to let everybody know that I've found a partial solution to my problem.
I've got Mandriva 2007 installed. To do so you have to add "all-generic-ide" (without the quotes) to the command line. And after installed you have to start the recue disk with the same option and edit the lilo.conf file and add all-generic-ide to the boot parameters and then re-install lilo.

Hope this helps-
That's way too complicated! What happened to "it just works" and putting the CD in and everything just works out all right?

---

### Post by forrestguide on 2007-02-22
> **teejay17 said:**
> Hey, no problem. Welcome to the forum, and your input is appreciated. Now, a quick question: were you installing at the point it froze, or were you trying to just boot into live CD. The problem I'm running into is when I boot into LIveCD, just trying to see how Ubuntu works with my hardware.

I'm finding a similar problem.  Actually, this is something of a cross post - I'm sorry for that.  Before I mentioned that my 700 mhz with 128 (Compaq Armada 700 notebook) was hanging up but apparently many lesser computers run it. 

I tried it on my 450mhz w/ 256 meg (Compaq) and it looked different when it hung up.  Maybe I'll try it and just walk away as a previous person did and maybe it'll work.

---

### Post by p1r0 on 2007-02-22
> **teejay17 said:**
> That's way too complicated! What happened to "it just works" and putting the CD in and everything just works out all right?

I think the same way. And that was exactly what I liked the best about Ubuntu, it jus worked.

The thing is that I neede Linux for work so I wrote an e-mail to Intel and they gave me the "all-generic-ide" tip for the install, the rest was a lucky guess. But I wouldn't have done this just for the fun.

I hope that they fix this (bug ???). I don't want to see window$ wining more market.

---

### Post by 1doeish1 on 2007-02-23
> **teejay17 said:**
> I'm just wondering what kind of video card you have? Would it be an ATI card by any chance?
It seems that most of us with this problem have ATI vid cards. I have not tried the "wait" method but I did download a cd of KNOPPIX and it loaded the Live OS just fine-Go figure. This was a better choice for my boyfriend as he is new to computers and I got tired of fixing and reinstalling windows because he would go into network settings and mess things up. With the live CD if he messes anything up he can just re-boot. KNOPPIX is easy for him to learn also. He is 55 and never had a computer. Linux had made it easier for the both of us!
Hope this helps a little as  this is a frustrating topic.

PS
I also tried install with noapic & nolapic-no go-hangs at the end just before the Live cd should start up. It loads the alternate OK, but this does him no good. Runs great on my machine, I have a GeForce vid card. I tried 64bit Ubuntu 6.06, and 6.10 , I tried Kubuntu 6.06 and 6.10 and 64bit 6.10 does the same on all of them at the same place and never loads the OS.

---

### Post by ForsakenSoul on 2007-03-13
Well it`s a bit late but what the hell ... It`s all comming from the motherboard or DesktopBoard in this case ... Intel DesktopBoard DQ965GF is giving me the same problems ... i`m still a begginer ... i haven`t even had the chance to install my ubuntu :( but for 2 days and a lot of reading in this forum i noticed the same problem on all Intel DesktopBoards DQ965GF ... so for the develepors of ubuntu please try it on the new Intel DesktopBoards and see what you can do ... i want ubuntu i liked it from the begining i don`t want any other linux :)

---

### Post by patlew on 2007-03-13
I have exactly the same problem. Tried everything Noapic ... some guys told me to burn with less speed.........
I found a lot of thread talking about the same problem.

The only solution I found is ubuntu feisty 7.04
It is not the best solution because in case you are not an expert you will probably have to reinstall once.
I would really prefer to install 6.10 but I am hopeless.

---

