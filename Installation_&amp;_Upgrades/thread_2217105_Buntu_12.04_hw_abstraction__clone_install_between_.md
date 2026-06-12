---
title: "Buntu 12.04 hw abstraction / clone install between PCs"
date: 2014-04-15
forum: Installation &amp; Upgrades
---

### Post by eric13 on 2014-04-15
Hi,
I've always impressed by the LiveCD of linux distribution since Knoppix  many years ago. Once installed on a HDD, are the distrib that "generic" and can it be transfered from one PC to the next one? 
During the installation, there is a "hardware installation" step. Does it install computer specific drivers? How works the driver abstraction in Linux? I am more familiar with the messy Windows...

More specifically, I plan to install Ubuntu 12.04 LTS in a few 11-years-old computers. Target is within my family but maybe also recycling center if we want to get rid of some of them. 
I think it would be LXLE, a derivate of Lubuntu 12.04 but with LTS. I have to stick to 12.04 since these PC have old NV1x/NV2x GPU which is buggy with the "nouveau" driver, thus I will need outdated Nvidia proprietary drivers.

Instead of installing the same stuff everywhere many times, I would like to prepare the basic install on a VM in a more recent computer with all updates and necessary packages; and then just clone the partitions to the physical HDD of these old computers.

a) it is feasible? Are they "no go" issues?
b) how/what is to care about?
c) what will be the computer specific work after the clone?

Here what first come to my mind:
1) I plan to stick with the default generic kernel of the distrib; 
2) Are the UUID of the partitions any specific to the HDD? It might be easier to stick with the old hdax scheme.
3) I wish I could find a tool/script for basic customization of step c), like changing the username and password.
4) After cloning a partition, I would probably have to update grub separately if I want to keep a windows XP aside...
5) installing the NVidia proprietary driver would be obviously in the step c).

What do you think?

---

### Post by mörgæs on 2014-04-15
Remastersys is abandoned, but maybe you can find a similar application. I guess that's what you are looking for.

---

### Post by eric13 on 2014-04-16
it is not really that I want to build a live cd: optical drive are too slow anyway.
I just want to clone my buntu install between computers.

---

### Post by ian-weisser on 2014-04-17
Personally, I think that's more work than 11-year-old machines are worth. Some kind of unrecoverable hardware failure can't be too far off.

Is it really worth cloning your customized install for somebody else? That's the hard part. It may be much easier to throw a rather lightweight default install on, and let the user make their own choices.

---

