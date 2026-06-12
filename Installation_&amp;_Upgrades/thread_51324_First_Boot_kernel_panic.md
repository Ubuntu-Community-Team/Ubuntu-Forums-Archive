---
title: "First Boot: kernel panic?"
date: 2005-07-23
forum: Installation &amp; Upgrades
---

### Post by (-_-)zzzZZZ on 2005-07-23
Hi!

Yesterday I my shipped Ubuntu Cds arrived and when I try any of them I get an error:

```
Code 01 00 00 00 eb 17 31 d2 8d 04 5a 83 bc 81 04 01 00 00 00 75 ea 42 83 fa 01 76 ed 31 c0 56b c3 57 31 c0 b9 45 00 00 00 8b 7c 24 08 <f3> ab 5f c3 90 90 90 8b 3c 24 04 8b 51 08 8b 42 0c 85 c0 89 41 
``` 
```
<0>Kernel panic - not syncing: Attempted to kill init!
``` 

I search the forums but didnt find a solution....
then I tried google, and found some simular problems with the installation CDs from other distros...I found some solutions but they all dont work with ubuntu

But the error only occurs with that old PC....
Here's some info about it:
Motherboard:  Asus P2-99
CPU: PIII(Katmai) 557MHz
hdd: IBM-DTTA-351010 (10GB)
RAM: 64MB SDRAM
Graka: nVidia NV4 Riva TNT

I really dont know what to do....so pls help me!
I want to install ubuntu! >_<

Vaporlze

---

### Post by EchoBeach on 2005-07-23
Hi Vapirize
I sympathise!
I just installed Ubuntu on my external 8Gb drive connected by USB 2.0 and it won't start (last few lines shown on the screen):
```
Starting Ubuntu
ata2: disabling port
pivot_root: no such file or directory
/sbin/init: 428: cannot open dev/console: no such file
 Kernal panic - not syncing: Attempted to kill init!
```My PC is a P4 3GHz running XP MCE 2005.
I wanted to keep Linux separate, so I've put it on its own disk.
Being *very* new to Linux, I don't know how to interpret these messages.
Any helpful advice gratefully received.
Echo

---

### Post by (-_-)zzzZZZ on 2005-07-24
Your Problem isn't exactly the same as mine....You have installed ubuntu on an external drive...but I haven't even installed a system....the error occurs when I boot from the install CD and start the installation....this is really weird....
I think I saw people with the same problem as yours in the forum...
Vaporlze

---

### Post by EchoBeach on 2005-07-24
My install disc was burnt from an image on a cover-mounted (magazine) DVD.
I have both a Live CD and an install CD - both from the same place.
Are you able to try with a Live CD - to see if it will run?
Do you have any other Live CDs such as Knoppix - that was my first introduction to Linux?

---

### Post by EchoBeach on 2005-07-27
Hi Vaporize
Are you sure your (received) CDs are OK?
You say 'CDs'.  How many are there?  What's the difference between them (that you can see - or have been told)?
Echo

---

### Post by codejunkie on 2005-07-27
[QUOTE=(-_-)zzzZZZ]Hi!

Yesterday I my shipped Ubuntu Cds arrived and when I try any of them I get an error:

```
Code 01 00 00 00 eb 17 31 d2 8d 04 5a 83 bc 81 04 01 00 00 00 75 ea 42 83 fa 01 76 ed 31 c0 56b c3 57 31 c0 b9 45 00 00 00 8b 7c 24 08 <f3> ab 5f c3 90 90 90 8b 3c 24 04 8b 51 08 8b 42 0c 85 c0 89 41 
``` 
```
<0>Kernel panic - not syncing: Attempted to kill init!
``` 

I search the forums but didnt find a solution....
then I tried google, and found some simular problems with the installation CDs from other distros...I found some solutions but they all dont work with ubuntu

But the error only occurs with that old PC....
Here's some info about it:
Motherboard:  Asus P2-99
CPU: PIII(Katmai) 557MHz
hdd: IBM-DTTA-351010 (10GB)
RAM: 64MB SDRAM
Graka: nVidia NV4 Riva TNT

I really dont know what to do....so pls help me!
I want to install ubuntu! >_<

Vaporlze[/QUOTE]

try the custom boot options like ```
linux acpi=off
``` usually one of the boot options will fix problems like this.

---

### Post by (-_-)zzzZZZ on 2005-07-27
The default 10 CDs...Yea they are all right, they work on a newer PC...
Ok..i'll try this boot option when i get home today...thx

---

### Post by (-_-)zzzZZZ on 2005-08-01
Hi!

I had no success...I tried the flags: 
acpi=off, noapic, nolapic sym53c8xx=safe:y, aic7xxx=no_reset, DEBCONF_DEBUG=5, BOOT_DEBUG=1, pci=noacpi, debian-installer/framebuffer=false, debian-installer/probe/usb=false, hw-detect/start_pcmcia=false, netcfg/disable_dhcp=true

first I tried every flag individually, then all together....but still the same hard lock and the same error message.....

I really have no clue what to do next....I reported this also to bugzilla........
Vaporlze

---

### Post by gemtaz on 2006-12-05
I have the same message error but with different conditions:
- I have a Live CD of Xubuntu 6.10
- I'm trying to install in a Virtual PC (512 MB RAM, 100 GB HD)

Is it possible to install in a virtual pc or should I try something else??

Thanks :confused:

---

### Post by dab on 2007-04-04
> **(-_-)zzzZZZ said:**
> Hi!

Yesterday I my shipped Ubuntu Cds arrived and when I try any of them I get an error:

```
Code 01 00 00 00 eb 17 31 d2 8d 04 5a 83 bc 81 04 01 00 00 00 75 ea 42 83 fa 01 76 ed 31 c0 56b c3 57 31 c0 b9 45 00 00 00 8b 7c 24 08 <f3> ab 5f c3 90 90 90 8b 3c 24 04 8b 51 08 8b 42 0c 85 c0 89 41 
``` 
```
<0>Kernel panic - not syncing: Attempted to kill init!
``` 

I search the forums but didnt find a solution....
then I tried google, and found some simular problems with the installation CDs from other distros...I found some solutions but they all dont work with ubuntu

But the error only occurs with that old PC....
Here's some info about it:
Motherboard:  Asus P2-99
CPU: PIII(Katmai) 557MHz
hdd: IBM-DTTA-351010 (10GB)
RAM: 64MB SDRAM
Graka: nVidia NV4 Riva TNT

I really dont know what to do....so pls help me!
I want to install ubuntu! >_<

Vaporlze


 I just got a Kubuntu distro to work by removing one of the 128mb ram chips on the computer I have here--it seems to be running a little slowly this way--but the kernel does not panic. I'm assuming it is either the sdram or the slot reading the sdram. Each time I try to install another 128mb of ram the kernel panics again. Perhaps you should start with troubleshooting your ram chip (perhaps it's just the way Ubuntu addresses the ram?).

---

### Post by zhimsel on 2007-07-11
i get the same message, but my caps lock light is flashing :/

---

