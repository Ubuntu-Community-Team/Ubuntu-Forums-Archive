---
title: "Partitioning troubles I guess... All i se is grub, but WHAT is it?"
date: 2005-05-07
forum: Installation &amp; Upgrades
---

### Post by muted on 2005-05-07
Hello! I have been using fedora for some months, got tired of it and wanted to try something else... Well then, i have just been trying in about 5 different ways to partition my 2 HD's in order to get ubuntu working. Now, since i am new to this, could someone please tell me: Every time im done with the installation i get this sort of grub terminal thing when the system reboots, like this: 
Code: 
grub> 

I have no idea if it is supposed to be like that, but i was expecting something graphical... 

Now, i have 2 HD's: 
1: 120 GB 
2: 12,5 GB 
Now i would like the whole system to be in the 12,5 GB HD, and only the 120GB to be my /home.... 
This means I have to chose some specific options for my partitioning... WHICH?? 

Whats the startup flag and should i agree to install one on my system??? 

Whats this whole grub thing?? 

I have nothing else on these HD's, going solo ubunto 


thanks (PC is about 450 mhz some 300 mb ram pentium 2 thing...)

---

### Post by kvidell on 2005-05-07
[QUOTE=muted]Whats this whole grub thing?? [/QUOTE]That's the only part of your dilemma I know how to answer.

GRUB is the **GRand Unified Bootloader**.[1]
It's an alternative to say.. LILO (LInux LOader).[2]

That little terminal you're getting, and I don't know why you're getting it, is the GRUB config terminal. It's good for dropping last minute changes in to a config, or install grub to a raw MBR (Usually I only see that from a grub floppy, or running "grub" from a terminal).

Sorry I can't answer the more pertinant portion of your question :-\
- Kev
[1]: [http://en.wikipedia.org/wiki/GRUB](http://en.wikipedia.org/wiki/GRUB)
[2]: [http://en.wikipedia.org/wiki/LILO_%28boot_loader%29](http://en.wikipedia.org/wiki/LILO_%28boot_loader%29)

---

### Post by az on 2005-05-07
It does not sound like grub is properly installed.  Did you switch the drives around after the install.  Did the install finish gracefully?

---

### Post by GTvulse on 2005-05-08
muted,

if both drives are chained in the same IDE controller and the 12.5 GB HD is a slave, you won't be able to boot up from it with grub, not even sacrificing a goat (been there, done that). You will need to swap the drives so that the small one is the master and the big one is the slave if they are chained, or put them as masters in different IDE controllers and select the booting drive in the BIOS (improbable, most DVD devices require to be IDE masters and most mainboards have only two IDE controllers these days).

If both HDs have their jumpers set to auto-sensing, you should be able to set the booting HD in the BIOS, else, you'll have to grab copies of the HDs manuals (most HD manufacturers publish them in their web sites these days) and figure out how to program the HDs jumpers so that the 12.5 GB is a master and the 120 GB is a slave. Then, when you install Hoary, select the 120 GB as your home and let the installer place GRUB in the master disk MBR sector. 

That should do it.

Let us know if this worked.

---

