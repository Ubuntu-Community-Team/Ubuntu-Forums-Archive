---
title: "Top hardware for 9.04"
date: 2009-02-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by purefan on 2009-02-04
Hey all,

I may be building a new pc soon and its purpose is for gaming, so it will have dual video cards, over 8 GBs of Ram... etc etc etc, Im just wondering whats the best line to go with now that 9.04 is about to be released. 

I realize the games for ubuntu are not so demanding (in general) but this will be a dual boot anyways, so im just wondering if its better to go with an Nvidia video card, an intel processor? and so on...

Cheers!

---

### Post by Kevbert on 2009-02-04
The Nvidia drivers have been recently updated/fixed for Jaunty and are running well for me. I have a problem running compiz in Kubuntu, but the Ubuntu version is fine, so it can't be the Nvidia driver.

---

### Post by binbash on 2009-02-04
Nvidia and intel.End of story.And what will you do with 8gb ram?If you dont use all the rams, it is a waste of time and money.8gb and more is for servers not personal use.I suggest sticking to 4gb and save some money

---

### Post by Valygard84 on 2009-02-04
For GPUs, nothing beats nVidias propertiary drivers yet. 
I don't agree with the no-to-8GB comment though - RAM is dirt-cheap at the moment (and only a small % of the total cost in such a setup anyways), and having so much RAM opens all sorts of interesting ways to toy with it, like with virtualization, Ramdisks, and such.
Be sure to use 64bit versions of Ubuntu and Windows though.

---

### Post by crjackson on 2009-02-04
> **binbash said:**
> Nvidia and intel.End of story.And what will you do with 8gb ram?If you dont use all the rams, it is a waste of time and money.8gb and more is for servers not personal use.I suggest sticking to 4gb and save some money

I respectfully disagree. With multiple desktops and virtual machines (which are very common), all the memory can and will go to good use.

---

### Post by autocrosser on 2009-02-04
Agreed--I'm building a i7 920 system right now (just waiting for the processor) & starting with 6G of ram--The i7 is tri-lane, so I'll be getting a second set of three as soon as money allows--The i7's have four cores with another four available as hyper-threading, so my Seti@home scores should climb a bit faster ;)

I'll post as soon as it goes online----

---

### Post by Spr0k3t on 2009-02-05
Go with the i7 Intel core on a good X58 chipset.  I've been extremely impressed with the rig I built.  I'm getting ready to upgrade the graphics card to an NV 285.  My previous system was an AMD X2 6400+ and the 8 virtual cores is insane for VM.

---

### Post by taavikko on 2009-02-05
I've just bought:
Core i7 920
Asus p6t-v2 dlx
corsair 6Gb (dominator) kit
xfx 9800gtx+

Just waiting for the case to put 'em in :)
(antec 902)

---

### Post by purefan on 2009-02-05
> **binbash said:**
> Nvidia and intel.End of story.And what will you do with 8gb ram?If you dont use all the rams, it is a waste of time and money.8gb and more is for servers not personal use.I suggest sticking to 4gb and save some money

I like to play chess but Im not too good at it, however there are chess programs that do very good and I like to run chess engine tournaments. With a super computer (in the broader sense) I'd put it to play online tournaments (when allowed for a computer to play, I dont mean evil here). There are also endgame tablebases called the Nalimov tablebases which can grow humongously big, and good processor and good ram help getting them before the apocalypse :P, plus, I do feel RAM memory is pretty cheap at the moment :)



> **taavikko said:**
> I've just bought:
Core i7 920
Asus p6t-v2 dlx
corsair 6Gb (dominator) kit
xfx 9800gtx+

Just waiting for the case to put 'em in :)
(antec 902)

NNNIIICEE!! :D


So the final verdict is Nvidia + Intel :D THANKS!! :D

---

### Post by Jeroen Vernooij on 2009-02-05
> **taavikko said:**
> I've just bought:
Core i7 920
Asus p6t-v2 dlx
corsair 6Gb (dominator) kit
xfx 9800gtx+

Just waiting for the case to put 'em in :)
(antec 902)

Nice.

Remember to install ubuntu 64 bits, and also install preload which is very helpful if you have that much RAM.

---

### Post by scheuri on 2009-02-05
I also disagree to the "no to 8GB" comment(s).

If using a 64bit OS (and that is really needed) I personally see no reason why only using 4GB at the current prices.
I would only pay a bit more to go from 4 to 8 GB, so no real harm done (considering that you "waste" a lot of money on a new pc anyway).

It was also already mentioned that 8 GB can be very much used. Beside the fact that the overall system may be more responsiv in general it will stay like this even when a lot of programs are open.
Using virtualisation software such as vmware or virtualbox (and xen and kvm and whatnot) also tends to use the RAM provided...and trust me, you want to provide enough RAM!

So, go for 8 GB (or even more if your board can handle it and you are willing to pay it).
Just make sure you use a 64bit OS (ubuntu, debian, sidux, whatever...)


have fun
scheuri

---

### Post by ronacc on 2009-02-05
the only thing I will add to what has already been said is make sure you have enough drive connectors, 6 SATA and 4 IDE preferably although the 4 IDE may be hard to ,find most boards only have 2 these days . and watch out for the boards that have some or all of the SATA connectors pointed sideways rather than up and down they can be a real pain in the a** to get at . and a good quality power supply with adequate capcity , a marginal power supply cost me a MOBO and 2 HD's recently .

EDIT: and one more thing an oversize case with pleanty of cooling , things can get crowded in there  with 2 gpu's and multiple HD's .

---

### Post by plun on 2009-02-05
> **ronacc said:**
> the only thing I will add to what has already been said is make sure you have enough drive connectors, 6 SATA and 4 IDE preferably although the 4 IDE may be hard to ,find most boards only have 2 these days . and watch out for the boards that have some or all of the SATA connectors pointed sideways rather than up and down they can be a real pain in the a** to get at . and a good quality power supply with adequate capcity , a marginal power supply cost me a MOBO and 2 HD's recently .

EDIT: and one more thing an oversize case with pleanty of cooling , things can get crowded in there  with 2 gpu's and multiple HD's .

Yup...  one solution for IDE/PATA disks (more then 2 ) is a cabinet.

I also cannot understand the amount of RAM discussed within this thread :confused:

When I blowed my MB, 2 weeks ago I bought a cheap new one, ASUS P5N73 and then I choosed a Intel 5200 CPU

2GB of RAM  !!

Directly raised FSB to 1000MHz and that resulted in a CPU frequency at 3.1 Ghz.  Rock solid stable (with margin) ! 

Compiled a 1000Hz kernel directly (2.6.29)


The combination nVidia/Intel is clear  .... but why blow away money on latest generation of hardware :confused: just to give away money to the hardware dragons.....  with Intel as the biggest one.

Nevertheless its a buyers market now....:D

---

### Post by ronacc on 2009-02-05
I have 4 gb  ram in 2 of my boxes and have never seen either of them above 50% ram used , but what the heck ram is cheap right now and I am one of those that believes you can never have too much ram , heck I even put 2gb in my EEE .

---

### Post by plun on 2009-02-05
> **ronacc said:**
> I have 4 gb  ram in 2 of my boxes and have never seen either of them above 50% ram used , but what the heck ram is cheap right now and I am one of those that believes you can never have too much ram , heck I even put 2gb in my EEE .

Yup, RAM is cheap but still costs money....

Give them to Red Cross or similar instead if it doesn't mean anything. ;)

Maybe we must start with stupid points as Vista....:lolflag:

10MB/s in diskspeed/ 4 points...:D

---

### Post by Martje_001 on 2009-02-05
Am I the only one who votes for ATi? The HD3xxx are already supported by open-source drivers at the moment in Jaunty and I'm sure the rest will follow.

---

### Post by taavikko on 2009-02-05
Discussion about amount RAM to use/purchase, on modern computers.

Normal desktop hardly needs more than 4Gb.
For the future needs, more the better...
Rather expencive solution still at the moment...
That dominator kit I bought 6Gb (DDR3 3*2048Mb/ pc-12800 1600MHz)
was ~250€, and I'll most likely buy another one just for future needs...
No need to upgrade, like never ever :)

When GNOME get's too bulked up, I'll switch to lighter WM's and install minimum system /w packages I need...

Software isn't getting any lighter...
Let's just hope that dev's are incorporating multicore support to code,
more and more...
that these new processors aren't waste of money...

---

### Post by MadsRH on 2009-02-05
Why not spend the extra money on a SSD harddrive? Intel has made one (can´t remember the name) and it's fast like crazy - and expensive of course. All in all, I don't thing you will notice the difference between 4 (or 6) Gb and the 8 Gb. There will be a difference, but not compaired to replacing the spinning HD with the Intel SSD HD.

Finally, I have to agree with **plun**. Buy the latest generation of hardware isn't always worth the money - especially if you're a Linux user ;-)

Just my 2 cent.

---

