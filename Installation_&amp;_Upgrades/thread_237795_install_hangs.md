---
title: "install hangs"
date: 2006-08-16
forum: Installation &amp; Upgrades
---

### Post by Mengus on 2006-08-16
Im trying to install kubuntu and the install hangs. first i tried to use the install cd. it hanges on 79% when configuring apt.
then i tried the alternate cd it hangs right after the choice of network card. so I then tried to install server. same thing. 
what can I do? help

---

### Post by zxee on 2006-08-16
What hardware are you trying to install this on? Processor, memory, hard drive space, video card...

---

### Post by Mengus on 2006-08-16
Im using an LW70 express laptop.

grafix: ATI radeon mobility x600
network card: Marvell/yukon 88E8036 PCI fast ehernet controller
Processor: Intel(R) Pentium(R) M proccessor 2.00 GHz
Ram: 1gb (not shure of vendor etc.)

I installed gentoo before and could not make my radeon card work. could it be the reason? 
my network card also seems to be tricky to get working.

---

### Post by Mengus on 2006-08-16
oh. harddrive space in the linux partition 11 gb

---

### Post by zxee on 2006-08-16
Your hardware seems ok, and even if the installer can't set up the network it shouldn't stop it (IMO). Can you use expert mode at the start screen or try with the noapic option? 
I think u(k)buntu can use some of the knoppix cheatcodes but it's hard to verify that.

---

### Post by Mengus on 2006-08-17
i tried the noapic option. then i tried noapic nolapic. still ita hangs while configuring agp. My network and internet is working fine when I boot the livecd so I blame the grafix card but i really dont have a clue. what is this  agp? I really want ubunt so please help me.

---

### Post by Mengus on 2006-08-17
someone told me I can do it expert mode. is this true? how?

---

### Post by zxee on 2006-08-17
Expert might not be the answer. You should be able to see some boot parameters/options by pressing the F1 key before the installer starts. 
If your agp slot is the problem you're going to have problems getting a useable screen, but try noagp at the start up boot prompt.
Also try either with the previous command or seperately xmodule=ati
Let the thread know how that goes.

---

### Post by bitziz on 2006-09-13
try the following when it hangs to see if it helps at all:

- Hit Ctrl+Alt+F2
- Type "sudo killall http"
- Hit Ctrl+Alt+F7

See if your installer starts again. It hangs because it tries to download security updates from apt. Once you installed the system this way, remember to download the security updates later.

---

