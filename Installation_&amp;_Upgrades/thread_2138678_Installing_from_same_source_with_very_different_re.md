---
title: "Installing from same source with very different results"
date: 2013-04-24
forum: Installation &amp; Upgrades
---

### Post by wilox on 2013-04-24
[COLOR=#333333][FONT=Ubuntu Beta]I also posted this on askubuntu.com, with little response so far. Thought I'd try here ;-)

I tried Ubuntu QQ from a Live USB (done with Linux Live USB Creator) and everything worked fine. But obviously the amount of persistence data is not enough.
So I installed it off the same USB on to a partition on my netbook ([COLOR=#444444]Asus Eee PC Seashell [/COLOR]bought 2011). 

Some unpleasant surprises: Trackpad not working, Mouse keys not working, Wireless not recognized. USB mouse does not work. Ethernet does not work. 

Again: running it off the stick everything works.
I mean this is supposed to be the same installation data as is on the stick?? How can there be so many errors on - what I would think in this day and age - basic computer functions?
How can I transfer the settings that work off the USB onto the hard drive installation?


[/FONT][/COLOR]

---

### Post by fantab on 2013-04-24
Does that ASUS use Cedar Trail chipset? Exact model or netbook specifications can help us help you.

---

### Post by wilox on 2013-04-25
> **fantab said:**
> Does that ASUS use Cedar Trail chipset? Exact model or netbook specifications can help us help you.

Model: 1015PE
[http://www.asus.com/Notebooks_Ultrabooks/Eee_PC_1015PE_Seashell/#specifications](http://www.asus.com/Notebooks_Ultrabooks/Eee_PC_1015PE_Seashell/#specifications)

Some output from [FONT=fixedsys]dmidecode[/FONT] :

Handle 0x0004, DMI type 4, 42 bytes
Processor Information
    Socket Designation: CPU 1
    Type: Central Processor
    Family: Core Solo
    Manufacturer: Intel 
    Signature: Type 0, Family 6, Model 28, Stepping 10

Version: Intel(R) Atom(TM) CPU N570   @ 1.66GHz



But again, I fail to see how that would matter. It is exactly the same hardware. I installed U QQ from the exact same source. I just don't get it.

---

### Post by fantab on 2013-04-25
You don't have Cedar Trail. Cedar Trail based processors don't have good opensource/linux support. I have this and I had to go through hell before I got it all working with Fedora. Anyways.

The netbook you are using has relatively very low specs. So you will be better off installing either XUBUNTU or LUBUNTU. My suggestion will be to go with Lubuntu. 
Even if we get all those things working your Ubuntu will be slow to run.

Good Luck...

---

### Post by wilox on 2013-04-25
Thank you for your reply.

You see, I use it just fine off the Live-USB. Speed is good using LXDE - no complaints. I would expect it to be even better off a hard disk. Really, no problem.

The issue I got is that I install the same distro off the same "source" and one is fine and the other has these massive and basic errors.


I could go ahead and install Lubuntu, but who's to say I will not run into the exact same problems again? How many distros are out there for me to try?

---

### Post by wilox on 2013-04-27
I have sort of "fixed" this now by installing Fedora (the same way via LiLi USB creator). Everything works out of the box. Bye Ubuntu!

---

