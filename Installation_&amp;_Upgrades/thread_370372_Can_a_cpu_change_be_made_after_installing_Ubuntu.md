---
title: "Can a cpu change be made after installing Ubuntu?"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by Rizlaw on 2007-02-25
I just installed Ubuntu 6.10 on a Shuttle SN25P with an AMD FX-55 single core cpu. The install was a dual boot (XP and Unbuntu) with the default two Linux partitions ( \ and Swap).

I am considering changing the CPU to an AMD dual core version, but I'm not sure if doing this will cause Ubuntu to stop working since it was not initially setup to see a dual core cpu.

So my questions are:

1. If I change to a dual core cpu, will Ubuntu still boot and work?

2. If the answer to the first question is YES, then will Ubuntu automatically see the second core/cpu, or must the kernel be recompiled for SMP? I don't have a clue on how to recompile a Kernel, let alone for SMP. I've read threads in the forums that seem to indicate that Ubuntu does not recognize dual core cpu's by default.

Thanks for the help.

---

### Post by mcduck on 2007-02-25
There should be no problem, as Ubuntu 6.10's 'generic' kernel detects your CPU at boot time and then enables different features (like suport for multi-core/multi-CPU setups).

So the answer to both questions is yes, and you don't need to do anything to make things work :D

---

### Post by Cannonade on 2007-02-25
So if I have ubuntu installed on a PC, if I decide to upgrade my computer with a new processor, I don't need to have to bother with all sorts of funny stuff like you do with Windows?

Is this also the same for changing other things, like graphics cards and motherboards?

---

### Post by mcduck on 2007-02-26
Pretty much yes. If you change from Ati display card to nVidia or the other way round you should change display driver to vesa first and uninstall the old card's driver, then add the new card & install it's driver. (this is just to let you keep desktop working through the job) Other than that just about everything is recognized at boot time. :)

---

### Post by openix on 2007-02-26
I moved edgy from a pentium 2.6GHz CPU and motherboard to a dual core and new motherboard without a reinstall. I made a good backup of stuff before the upgrade just a safety measure. I had no loss of data and was on the net as soon as I logged in again after upgrade.

Oh windoze I miss you -  NOT!

---

### Post by kvonb on 2007-02-26
When my server's mainboard dies (capacitors blow) I temporarily swap the hard drives into a spare system I have, and it just works, in 10 mins I'm back up :).

The amusing thing is that my server is an Intel P4-1.6, my backup machine is an AMD XP2000!

I stick to the "vesa" video driver just to make things even easier.

As long as you have the generic kernel it will fire up straight away.

This is one of the many beauties of running Linux, all the basic hardware drivers are loaded dynamically at boot time, no messing about :).

---

### Post by Rizlaw on 2007-02-26
Thanks for all the replies. I'm suitably impressed by Ubuntu. Now if only the Ubuntu Team would get digital sound output to work on my Shuttle SN25P. Seems that those of us with SN25Ps are stuck with analog out only.

---

### Post by dasunst3r on 2007-02-26
Yes, but you will have to reactivate within 15 days.  Oh, wait... that's Windows!  Sorry!

Back when I used FC3, I had to change out an entire motherboard.  I booted it up and besides having to reconfigure X, everything was dandy!  Needless to say, I was afraid of booting into my Windows.

---

### Post by dazzerthemighty on 2007-05-20
Just a quick question what to do if you swap the graphics card before installing another make :(
Nvida -> ATI

How do you bring the system back ?
I mean repair so as to boot up

Thanks in advance;)

---

### Post by joe.turion64x2 on 2007-05-20
> **dazzerthemighty said:**
> Just a quick question what to do if you swap the graphics card before installing another make :(
Nvida -> ATI

How do you bring the system back ?
I mean repair so as to boot up

Thanks in advance;)
Once I did that in Fedora and since the X server was unable to start its configuration applet was loaded to allow me select my new card. I believe that is pretty much the same in Ubuntu.

Anyway you can always log in using text mode and edit your /etc/xorg.conf file using vim. Usually changing the line where says something like nvidia (or nv) to ati (or fglrx) solves the problem.

Joe.

---

