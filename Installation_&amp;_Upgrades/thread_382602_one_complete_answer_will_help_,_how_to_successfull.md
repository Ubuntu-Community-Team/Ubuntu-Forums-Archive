---
title: "one complete answer will help , how to successfully install ubuntu 6.10 on core duo ?"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by quedigg on 2007-03-12
hi folks, 
could any one write a complete guide for installing ubuntu on core duo/core 2 duo systems ?
please thread it step by step , all posts are missing or not targeting novice users .

many thanks in advace

---

### Post by Kateikyoushi on 2007-03-12
It is not the CPU what is the problem but the chipsets, and ide,sata controllers of the motherboard.
Because those are different for the motherboards can not generalize the steps enough in my opinion.
Your best bet is to try the alternate cd if the live does not work.

---

### Post by Belyel on 2007-03-12
Installing on a core duo or a core 2 duo is pretty much exactly the same as installing on any other architecture.  In fact, the only difference is that with the core 2 duo (if that's what you have), you can choose to install either the Desktop version or the AMD64 version.  The AMD64 version will work on any 64-bit architecture, but it is named AMD64 because they were the dominant force and basically only choice for 64 bit processors at the consumer level.

The **first** step is to download the cd image for a standard desktop install.  Burn it to a CD and put it in your CD rom.  Your computer will boot from it, and you can test Ubuntu without installing it.  This will run MUCH slower than normal, because your CD-ROM is not as fast as a hard drive.  However, you can get a feel for what hardware will work and what might not.  

The **second** step is to play with the live session (what you booted into from the CD) and make sure enough of your hardware is working to make you happy.  Chances are, if it is not working fully on the live CD, it won't work immediately after installing Ubuntu.  However, this does not mean that it won't work in Ubuntu.  There are literally hundreds of guids on this site (and others) for getting hardware to work.

**Third**, double click on the icon on the desktop of the live session to begin installing.  Follow the directions.  If you still have problems, check out [This link that explains it in great detail]("https://help.ubuntu.com/community/GraphicalInstall")

When you install using the desktop CD of 6.10, the generic kernel is installed.  This automatically supports SMP, the protocol for multiple processors.  I have this installed on two dual-core systems, and it screams, even without the 64 bit instruction set for my AMD system.  If you are set on using the 64 bit version, please understand that there are a LOT of programs that do not work yet on the 64 bit architecture.  I would STRONGLY advise someone who is not 100% comfortable with compling their own programs and using the command line to avoid AMD64 for the time being.

Hope this helps.  Remember to search the forums for more help.

---

### Post by andreas64 on 2007-03-12
Hi,

that's a really common question. What kind of problems do you have?

Normally there's nothing special with installing on a DualCore/Core2Duo system. The generic kernel  supports SMP out-of-the-box.

Andreas

---

### Post by quedigg on 2007-03-12
many thanks for all your quick replys !
you have solved some issues in your posts , my be the motherboard on some firmware.
here is a brief description of my laptop :
 compaq Presario C300 with core duo T2050 .
nothing special about it , Mandriva 2007 was installed smoothly.  ubuntu 6.10 live cd runs and installed successfully,though on the 1st boot i get jfs error ,so i resart manually and select rescue mode, i get an error about cpu or processor #0 !.

Thanks again

---

### Post by jhenager on 2007-03-14
The only 'problems' I noticed is that the processing isn't symmetrical at all. When CPU0 is at 95%, CPU1 is at 5%, and vise versa. 
I would expect that the load would be distributed equally between the two.
However, this output seems to indicate that SMP is running, in some fashion.
jeff@jeff-desktop:~$ uname -a
Linux jeff-desktop 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

Just seems a bit odd, that's all. Using gkrellm, if you took the graph from CPU0, and flipped it 180 degrees, the hills and valleys would fit perfectly into CPU1.

---

### Post by Kateikyoushi on 2007-03-14
The load won't match in many cases because if the given program can not use more than one core.
Let's say you run something what can utilise only one core and puts a large load on it and the other is just running the system, that's what you get.

---

### Post by quedigg on 2007-03-15
[Poineer]("http://distrowatch.com/table.php?distribution=pioneer") ,which is ubuntu-based got me back to linux on my laptop !. it supports my built-in buttons, that i was not expecting from any distro, also the installation ran smoothly , very pleasing !

---

### Post by Death_Sargent on 2007-03-15
The only problem I encountered with a dual core system is the fact that processes tend not to be optimized to one processor or another and tend to just bounce between the two available processors. 

When I had vista There was a program for setting affinity perminantly so processes would not waste clock speed. 

A program like this for Ubuntu would rock.

---

