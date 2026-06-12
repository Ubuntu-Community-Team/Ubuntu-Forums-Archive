---
title: "SSD and Swap in my laptop"
date: 2015-07-04
forum: Installation &amp; Upgrades
---

### Post by ckrles on 2015-07-04
Hi, I'm not very knowledgeable about ubuntu. I've been using it for three years or so. I'm intending to buy an SSD (Samsung Evo 850) to upgrade my laptop.
My main concern is with the RAM memory and Swap. My laptop is 32bits and it has 3Gb or Ram, so if I'm not wrong it is useless to upgrade to more RAM since it won't be detected by the system. I just don't know how much my laptop with use swap memory, which is quite relevant since extensive use of it doesn't seem to be very good for SSD's in term of their endurance and durability. Please, correct  me if I'm wrong.

The point is that I don't know how often my laptop uses Swap with my current use: specially browsing, vewing pdf's, libreoffice, youtube, rarely watching an mkv video, etc  not very ram demanding tasks I think.

I know I can clone my current drive but I'd rather reinstall Xubuntu 14.04 (dual boot with Windows 7).

So, according to my use, what should I do with swap? Should I figure out a way to locate on other drive (I could use the dvd bay to install my hdd and locate swap there if really necessary)? or could I install it on the SSD because my laptop usage will hardly ever need swap, so the ssd won't be "stressed"? How many gb's should I assign to swap?

How could I know how often my laptop needs swap?

My laptop (bought in 2008) specs are:

Toshiba Satellite A300
Intel Core 2 Duo T5750 2.0Ghz
3Gb Ram
250Gb Hdd (I intend to change to a Samsung Evo 850 SSD)

I think it's Sata I (not sure and don't know how to check it), but I guess a SSD would make a great different, wouldn't it?

Thank you very much.

---

### Post by howefield on 2015-07-04
> **ckrles said:**
> How could I know how often my laptop needs swap?

Running top in a terminal will give you an idea of how much, if any at all swap is being used.

---

### Post by ckrles on 2015-07-04
> **howefield said:**
> Running top in a terminal will give you an idea of how much, if any at all swap is being used.

I don't know what you mean, sorry. Could explain with some more detail.

Thank you.

---

### Post by howefield on 2015-07-04
When you are using Ubuntu, open a terminal and type the command

```
top
```

and press enter, this will give you information about the running processes on your computer including how much swap is in use which may better enable you to decide how to proceed.

Fwiw, I have a similar setup to yours and have the (almost never used)  swap partition on a regular HDD.

---

### Post by ckrles on 2015-07-04
Thank you. I didn't know the top command. I'll check it out.

---

### Post by oldfred on 2015-07-04
You have a 64 bit system with Intel Core 2 Duo.

My laptop from 2006 has an old Core 2 Duo, but  only 1.5GB of RAM. I do install Ubuntu 64 bit, but Intels video in that laptop is too weak for Unity, so I install fallback which is lighter  weight like Lubuntu or Xubuntu. But if I load more than one large app and a couple of smaller apps, screen turns grey for a couple seconds, so I know it is using swap.

You can load all the apps you normally run and run this:
This is my new Desktop so It has lots of RAM, and does not use swap.
```
fred@trusy-ar:~$ free
             total       used       free     shared    buffers     cached
Mem:       8118308    2161716    5956592      16856     263324     984296
-/+ buffers/cache:     914096    7204212
Swap:      1952764          0    1952764

```

With 3GB of RAM, it will depend a lot on how many apps you load at once, but you should not use swap often.

Newer SSD now have lives similar to hard drives. Of course some fail earlier whether a HDD or SSD.
       SSD life test 2015 final
[http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead](http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead)

---

### Post by ckrles on 2015-07-04
My laptop from 2006 has an old Core 2 Duo, but  only 1.5GB of RAM. I do install Ubuntu 64 bit, but Intels video in that laptop is too weak for Unity, so I install fallback which is lighter  weight like Lubuntu or Xubuntu. But if I load more than one large app and a couple of smaller apps, screen turns grey for a couple seconds, so I know it is using swap.


What a surprise!!! I've always thought that my cpu (core 2 duo t5750) was a 32-bit system. I don't know how I was convinced it was 32-bit and never had a doubt. Since you told me, I checked it out and I'm glad I was wrong.
o open
I tried to force my laptop into using swap and it's been quite hard since I had to run: Firefox, Chrome playing a youtube video, Chromium, Software centre, transmission, jdownloader, gimp, spotify, clementine, pdf viewer, vlc playing a 1080 5.4gb video, and libreoffice writer. This way it has used my 3gb of ram and 24mb of swap.

Obviously I couldn't make all the apps run at 100%, but I never run so many apps at the same time, so I guess I've probably never used swap memory.

I've always used 32-bit systems. Will the ram demand increase if I move to 64-bit system? Will it be enough with 3gb of ram in 64-bit Xubuntu? I mean in terms of not using swap too often in order not to stress the ssd?

---

### Post by kerry_s on 2015-07-04
install zram-config it will use swap in ram first. save real swap for when it really needs it.
i use swap & unpartitioned space on mine, i've also trying btrfs on this install, i've read it has good ssd features.

your specs are better than mine so you should be fine.

---

### Post by ckrles on 2015-07-04
I'll give those programs a try. I've monitored ram usage with terminal and top. I guess it will be enough since I don't think I will be using swap too often.

---

