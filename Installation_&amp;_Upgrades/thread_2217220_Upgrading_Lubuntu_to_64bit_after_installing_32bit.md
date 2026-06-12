---
title: "Upgrading Lubuntu to 64bit after installing 32bit"
date: 2014-04-16
forum: Installation &amp; Upgrades
---

### Post by nandodnhd on 2014-04-16
Please read:

So i have a dual boot with windows 7 and lubuntu(32bit)
I accidentally installed the 32bit version of lubuntu while
i have 64bit hardware.

So my quistion is:
How do i replace the 32bit version with the 64bit version without ruining my 
windows 7 dual boot?

I have nothing special on my lubuntu so i can handle a reset.
But i do have important stuff on my windows 7 copy.


Thanks already!

---

### Post by mikewhatever on 2014-04-16
There is no way to upgrade. Reinstall, or use 32bit - works just as well.

---

### Post by nandodnhd on 2014-04-16
well i'm a noob, but i have 3gb ram, if you have more than 2gb ram isn't it a good idea to get a 64bit version?

---

### Post by nandodnhd on 2014-04-16
> **mikewhatever said:**
> There is no way to upgrade. Reinstall, or use 32bit - works just as well.
can you confirm that this is true?
[http://prntscr.com/3ahfi3](http://prntscr.com/3ahfi3)

---

### Post by mikewhatever on 2014-04-16
> **nandodnhd said:**
> well i'm a noob, but i have 3gb ram, if you have more than 2gb ram isn't it a good idea to get a 64bit version?

Personally, I don't think that idea is either good or bad. ;) Both should work about the same for an avarage user.
...but, as said above, if you have time to waste, reinstall.

---

### Post by su:bhatta on 2014-04-16
> **nandodnhd said:**
> can you confirm that this is true?
[http://prntscr.com/3ahfi3](http://prntscr.com/3ahfi3)

Your point being? 
That article puts in bold "You can reinstall Ubuntu.... Erase Ubuntu 12.10 and Reinstall"

If you installed a 32bit Ubuntu, you got to reinstall the 64bit one.

---

### Post by pfeiffep on 2014-04-16
> **nandodnhd said:**
> can you confirm that this is true?
[http://prntscr.com/3ahfi3](http://prntscr.com/3ahfi3)

The referenced screen shot presents 3 options, none of which states anything about upgrading. The first option, which I believe is the one you've focused on, will install another version which would result in 3 different OSes installed (Win 7, Lubuntu 32 bit, and the newly installed 64 bit).** @[COLOR=#000000]su:bhatta had it correct.[/COLOR]**

The 32 bit option will work just fine for you, if you have cpu intensive applications planned then the 64 bit OS will probably suit you better.

---

### Post by mastablasta on 2014-04-16
> **nandodnhd said:**
> well i'm a noob, but i have 3gb ram, if you have more than 2gb ram isn't it a good idea to get a 64bit version?

RAM (in your case) has nothing to do with it. if CPU is 64 bit you can use both versions. if CPU is 32bit you can only use 32 bit. 32 bit supports up to 32GB ram i think. 

to benefit form 64bit architecture the 64bit version is needed. however as mentioned for average user the benefit might not be noticable. 64 bit will perform better, but not by that much. 

so as they said if you have time to waste :-)

reinstall - you can just boot into Lubuntu live session, delete lubuntu partitions using gparted and then trigger another install into the available empty disk space.

---

### Post by su:bhatta on 2014-04-16
> **pfeiffep said:**
> The referenced screen shot presents 3 options, none of which states anything about upgrading. The first option, which I believe is the one you've focused on, will install another version which would result in 3 different OSes installed (Win 7, Lubuntu 32 bit, and the newly installed 64 bit).** @[COLOR=#000000]su:bhatta had it correct.[/COLOR]**

The 32 bit option will work just fine for you, if you have cpu intensive applications planned then the 64 bit OS will probably suit you better.

Thank you pfeiffep!
I believe the OP is thinking in the lines of Win 32bit OS's where the limit to 32bit OS  is using 2Gb ram.
> 
if CPU is 32bit you can only use 32 bit. 32 bit supports up to 32GB ram i think.
But, mastablasta has mentioned Ubuntu 32Bit will support upto 32Gb of Ram. 

So [**[COLOR=#000000]nandodnhd[/COLOR]**]("http://ubuntuforums.org/member.php?u=1892903"), if you want you can reinstall the 64bit OS, but not for the reason of using the 3Gb RAM properly.

---

### Post by eric13 on 2014-04-16
to be more precise about max physically addressable RAM:
- 32 bits kernel without PAE (rare today): 32 bits -> 2^32 = 4 GB, but in practice limited to 3 GB
- 32 bits kernel with PAE: 36bits-> 2^36 = 64 GB
- 64 bits kernel: currently 48 bits, but only 47bits effective -> 2^47 = 128 TB
With PAE or 64bits, the limit will be set in most cases by the hardware, first by the memory controller (earlier in the chipset, now integrated in the CPU, currently 32GB for Intel main stream cpus), then by the mainboard.

---

