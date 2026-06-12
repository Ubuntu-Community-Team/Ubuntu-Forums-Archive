---
title: "Computer turns off when trying to install 7.10"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by justinhj on 2007-10-20
I tried to install from the 7.10 live CD. I booted up the live CD and everything seemed to function ok. 

I clicked the install icon, and started filling out install options. 

It got to the stage "loading partioner" and after a while the computer just turned itself off.

I turned it back on, and when booting the live CD it now just goes dead. The computer is running but there's no monitor output. 

I can remove the CD and boot into Windows XP no problem. 

Is it possible to do the install process in a terminal so I can see what's happening?

Here's some info on my system


   Operating System: Windows XP Professional (5.1, Build 2600) Service Pack 2 (2600.xpsp_sp2_gdr.070227-2254)
           Language: English (Regional Setting: English)
System Manufacturer: ASUS 
       System Model: A7V400-MX
               BIOS: Phoenix - Award BIOS v6.00PG
          Processor: AMD Athlon(tm) XP 2400+,  MMX,  3DNow, ~2.0GHz
             Memory: 512MB RAM
          Page File: 506MB used, 743MB available
---------------
        Card name: MSI NX 6600 (NVIDIA GeForce 6600)
     Manufacturer: NVIDIA
        Chip type: GeForce 6600

     Name: VIA Rhine II Fast Ethernet Adapter
     Name: Sound Blaster Live! 24-bit

---

### Post by Craigus on 2007-10-20
I hesitate to say "bad CD burn" to everyone who has a bizarre problem like this, but it is a possibility. Have you tried making another one ?

Getting the alternate installation iso is an option, but it shouldn't be necessary on a vanilla system like yours.

---

### Post by phil90 on 2007-10-20
Hello


I have the same problem I just cant install Gutsy the computer turn off by itself everytime


I tried both the desktop and the alternate cd and they both do the same. The Cd was burned correctly Ive verfied both it just seem the installer wont proceed to an installation it starts and everything is alright until about  94% I think and then it turn off everytime.


Please let me know if you know how I can install Gutsy

---

### Post by justinhj on 2007-10-20
It could be the CD, it did verify correctly after writing but doesn't seem to read smoothly all the time. 

I'll try another one.

Justin

---

### Post by justinhj on 2007-10-21
Ok I made another disk and checked it at the boot menu. No problems. 

The same problem occurs. The disk partioner runs and as soon as it does the system shuts down and then will not boot the live CD again. If I remove the CD then I can boot into XP with no problems.

---

### Post by phil90 on 2007-10-21
Its so weird after the thousand of failed installation I boot my computer and I did not have the cd in so the computer did boot in Ubuntu which is kind of weird since it did shutdown while it was intalling.


Now when I am in Ubuntu the computer stil turn off for no apparent reason. 

It really is annoying.

---

### Post by Craigus on 2007-10-21
Ack. This is a pretty serious bug then - I think you should both file a bug report.

[http://www.ubuntu.com/community/reportproblem]("http://www.ubuntu.com/community/reportproblem")

---

### Post by kehil on 2007-10-21
I also had a similar problem just today when I was installing Gutsy.
Just as I configured everything before installation, and clicked "install" my screen turned back, and the signal led on it showed that it doesn't receive any signal from the computer.
But then I pressed Ctrl+Alt+Del, and I got back my screen, with the installation running, So perhaps that's why you were able to start ubuntu after rebooting.
I also have Geforce 6600, so I thought it may have some connection with the problem...

Cheers,
Balázs

---

### Post by phil90 on 2007-10-21
Hello

I  did try something else I installed Feisty back and upgrade to Gutsy. I am in Gutsy and until now it does not turn off by itself. I don't understand why would the ugrade work but not the regular install

Gutsy still turn off by itself I might just go back to feisty at least it was not turning off by itself

---

### Post by justinhj on 2007-10-21
I installed from the alternate. I got much further that way. My machine is powering down now every 10 minutes or so. 

Everything seems fine, and then it fades the screen out and just goes dead.

---

### Post by justinhj on 2007-10-22
I looked in /var/log/syslog to see what may have happened last time it turned off and I saw 

Oct 21 20:14:55 ubuntu gnome-power-manager: (justinhj) Hibernating computer because the suspend button has been pressed
Oct 21 20:14:56 ubuntu dhcdbd: Unrequested down ?:3

Except I'm pretty sure I didn't press the button, since I wasn't at the computer.

Anyway, I set the suspend (sleep on my UK keyboard) button to do nothing, and I've been running for 2 hours with no shutdown. So fingers crossed that has fixed it.

Justin

---

### Post by justinhj on 2007-10-22
I'm thinking this is a simple hardware issue now. It does still power off occasionally. In one instance I booted the safe mode Ubuntu and the log said that a critical temperature has been reached, and shut down. 

My guess is my fan is broken or come off the CPU, something like that, and windows may be set up to be less sensitive.

---

### Post by phil90 on 2007-10-23
JustinHj was it doing that in Feisty or even windows.

I've reinstalled Feisty and I have no poblem anymore. my problem cames from Gutsy. It's really too bad I was counting the seconds for the gutsy realease since I started using Ubuntu each time there is a release I am like a little kid counting the seconds before christmass. I hope the hardy release is stilll going to get my excitement

---

### Post by justinhj on 2007-10-26
Hi Phil

Yes apparently was happening was windows was ignoring the overheating. I've got a software monitor now on WinXP so I can manually turn off. if it gets too hot.

Justin

---

### Post by phil90 on 2007-10-30
Well your problem might be coming from something else.

I don't know if my computer is overheating but still it should cause to turn off on gutsy for no reason.

Well I am using feisty and it did never turn off by itself

I am going to verify for temperature to see if my computer is overheating just in case it is the saem problem


Good luck

---

### Post by phil90 on 2007-11-27
Hello does anyone know how to fix this issue.

I've reported it a month ago and still I have no answer

---

