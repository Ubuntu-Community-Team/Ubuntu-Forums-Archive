---
title: "Help with Dual-Boot"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by ^^Snoop^^ on 2007-10-23
I've just installed Gutsy Kubuntu and got it set up pretty nicely, but I'd like XP on there too so I can play some games.

I've tried dual-booting when I just had XP installed, but no matter which version of Ubuntu I used, even GParted, I received a message saying there was an error and I couldn't change the drive partitions. So my only option is to have the one OS on my HDD.

Is there a way of installing XP as well as keeping my current Kubuntu setup?

Or failing that, I suppose I could completely clear my HDD and create seperate partitions from the off. Then install XP, and I'll already have partitions available for installing Kubuntu into. If that's the case, which paritions do I need to create? I have a 230Gb HDD, I'd like to keep 50gb for Windows and installing some games, otherwise the rest can go to Kubuntu. I think I'd need four paritions (one for XP and three for Kubuntu), right? Which sizes should I create my partitions for Kubuntu? Isn't it better to have /home installed on a seperate partition?

If it was easier to start from scratch again, I wouldn't mind too much. I just want the easiest option :)

Thanks for your help :)

---

### Post by reylafo on 2007-10-23
Your best bet will be to start from scratch. The GParted live .iso is very helpfull for this and many other things. Downloadit, burnit, useit.
You may want to make the following partitions: NTFS for windows, EXT3 for / (your linux distro), EXT3 for /home (your documents,files and preferences), and a small partition for SWAP (required).

Then install Windows. Install Ubuntu using your selected partitions. You can read and write to your Windows partitions using the NTFS configuration tool from the repos.

For more details read this article from the smart cats of:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

enjoy Ubuntu.

---

### Post by ^^Snoop^^ on 2007-10-23
Cheers reylafo.

If I have 180gb for Kubuntu, what sizes should I set my /home and SWAP partitions to? EXT3 would be the largest partition?

Edit: Just read to use 5-10gb for /home, SWAP 1.5/2x your RAM. I've got 2Gb so 4Gb SWAP? Nice, I'll get to it tonight then :)

---

### Post by reylafo on 2007-10-23
/home should be your largest partition. This is your "playground" with all your personal files, downloads, stuff.
The / (root) partition is ok with 10 Gig. If you need to re-install or upgrade this is where is done, the /home partition is left untouched, this is great!

The Swap don't need to be so big. 512Mb-1Gig is ok. It is hardly ever used, it just needs to be there.

---

### Post by ^^Snoop^^ on 2007-10-23
Thanks for all your help reylafo, much appreciated :)

---

