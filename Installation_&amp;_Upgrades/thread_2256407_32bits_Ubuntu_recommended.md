---
title: "32bits Ubuntu recommended ?"
date: 2014-12-12
forum: Installation &amp; Upgrades
---

### Post by kaweka on 2014-12-12
The Ubuntu installer download page uses just one criteria for the 32bits or 64bits variant recommendation.
It reads there 32bits one is recommended if less than 2GB ram are available.

Does it really mean that for Pentium 4 32bits processor and 2GB RAM populated setup the 64bits Ubuntu is recommended in the fact?

---

### Post by bobthebaritone on 2014-12-12
Dear kaweka,

A Pentium 4 with 2 GB of RAM will effectively run 32 bit ubuntu. You need to be very careful on defining exactly what Pentium 4 - so consult the motherboard manual and physically inspect the processor. Some p4's do support 64 bit processing.

The simple rule to follow is if you need to address more than 4 GB of memory you will need a processor supporting 64 bit addressing.

Cheers,

Bob

---

### Post by Impavidus on 2014-12-12
A 64 bit Ubuntu cannot run on a 32 bit processor. The advantages of 64 bit – slightly faster and the ability to give more tha 4GiB of memory to your applications – get obvious when you have more then 4GiB of memory. The disadvantages – needing more memory to complete the same task – become a problem when you have less than about 2GiB of memory. Inbetween it doesn't matter much.

---

### Post by grahammechanical on 2014-12-12
In the past the 32 bit ISO image was recommended because a 32 bit OS will run on a 64 bit CPU. The architecture of the 64 bit CPU was designed to be backwards compatible with 32 bit operating systems. So, in a situation where the intended new user did not know whether the CPU was 32 bit or 64 bit installing 32 bit Ubuntu would be successful regardless of the CPU architecture.

The present Ubuntu.com download page recommends 64 bit Ubuntu. For many years all new machines have had 64 bit CPUs and machines with a 32 bit CPU are unlikely to be capable of running modern Linux desktop environments. 

I am using every day 64 bit Ubuntu 14.10 on a machine with 1 GB of RAM. But it does have a video adapater that has 1GB of its own memory. I think that fact is a big reason why I am getting a good user experience on this machine without needing to increase the amount of RAM. It has an Intel Core 2 DUO 2.40 GHz CPU. So, although the hardware is long past its sell by date, it is still giving a good account of itself.

In the case of your machine, I would suggest that the determining factor would be the graphic card capabilities. You most definitely need a 32 bit operating system but you may need to be installing Xubuntu or Lubuntu on account of the graphic adapter.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Regards.

---

### Post by kccv42 on 2014-12-12
I have had issues when running 32-bit on a 64bit machine. It worked for me but with problems. I am now using a 64bit ubuntu for a 64 bit machine. It runs much better and doesn't crash as much.

---

### Post by kaweka on 2014-12-13
Hi, Thanks for all your hints. My actual concern is the correctness  of recommendations made by Ubuntu.
As for 14.10 the Intel x86 is still on the list of compatible HW.
For recommendations Ubuntu should take the whole spectrum of supported HW into consideration.
Just focusing on the mainstream is not a good certificate for vendor.
As yourself tell just the RAM amount is not the only criteria for decision which version to take. At this point the Ubuntu recommendation is not accurate and misleading.
There is an old **famous slogan known from Linux world**: "Linux had lower hw requirements than Windows, so better chance to be able to run
LInux on your old hw setup than Windows". My hope was  and is that slogan is still valid.
The inaccuracy in addressed Ubuntu recommendation does comply to that slogan.
Does it mean the slogan is obsolete? If yes, since when?

For me the point is clear. It is Pentium 4, 32Bits, no mechanism on motherboard nor in bios to address above 4GB.
Motherboard enables to populate RAM up to 4GB. The region somewhere above 2GB covered by RAM helps nothing because peripheries are mapped here as well.
So 32Bits variant is the only suitable.
These were just the inaccurate recommendations made by Ubuntu which pushed me into irritations.

---

### Post by coffeecat on 2014-12-13
> **kaweka said:**
> 
For me the point is clear. It is Pentium 4, 32Bits, no mechanism on motherboard nor in bios to address more than 4GB.
So 32Bits variant will be the most suitable.

You have a 32-bit processor which cannot run a 64-bit OS. Therefore you have to use the 32-bit version of Ubuntu. It's as simple as that. How much RAM you have does not influence that lack of choice.

---

