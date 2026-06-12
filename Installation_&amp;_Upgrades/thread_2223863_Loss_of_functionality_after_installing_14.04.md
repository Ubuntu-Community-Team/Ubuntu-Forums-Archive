---
title: "Loss of functionality after installing 14.04"
date: 2014-05-13
forum: Installation &amp; Upgrades
---

### Post by Tony_Fendall on 2014-05-13
Hi, I have a clean install of 14.04 on a Vista laptop of HP manufacture.  Since the install the laptop will not operate on its battery, even though icon says fully charged. As soon as I remove mains the laptop instantly shuts off.
I have wired connection to the internet OK, but my wireless connection wont work any more.
So basically my laptop is unusable as a portable machine.
any help appreciated.
TonyF

---

### Post by sudodus on 2014-05-14
Welcome to the Ubuntu Forums :-)

Please describe you computer with more details! It will make it possible to give better advice.

Hardware:

- What model of HP is it?
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Software:

- Is it a dual boot system with Vista and Ubuntu, or an Ubuntu only system?

-o-

I'm going to suggest some other version (12.04 LTS, 13.10 or 14.04 LTS) and flavour (Lubuntu, Xubuntu, standard Ubuntu, Kubuntu) or light-weight re-spin of 12.04 LTS (Bento, Bodhi, LXLE).

Particularly if the computer is middle-aged or old, 12.04 LTS might be a better choice than 14.04 LTS.

A boot option might also be a solutiton for your computer. See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by mastablasta on 2014-05-15
lshw command will list hardware and you can copy that and post it here. 

i too lost funcitonality with 14.04 on HP laptop, but nowhere near as bad as yours. mine had a newer model certified for Ubutnu while this older one actualyl had it all working well. so post the hardware spects and let's go through it. one step at a time.

also cas suggested check the boot options. acpi off or similar might help.

---

### Post by Tony_Fendall on 2014-05-22
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

Please describe you computer with more details! It will make it possible to give better advice.

Hardware:

- What model of HP is it?
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Software:

- Is it a dual boot system with Vista and Ubuntu, or an Ubuntu only system?

-o-

I'm going to suggest some other version (12.04 LTS, 13.10 or 14.04 LTS) and flavour (Lubuntu, Xubuntu, standard Ubuntu, Kubuntu) or light-weight re-spin of 12.04 LTS (Bento, Bodhi, LXLE).

Particularly if the computer is middle-aged or old, 12.04 LTS might be a better choice than 14.04 LTS.

A boot option might also be a solutiton for your computer. See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
The system was intended to be single boot Ubuntu, I have now ditched Vista, machine is HP G5000 laptop, I can't give any more info as I can,t access details of wireless card or anything else.
Sorry for the delay, election work.
Tony

---

### Post by sudodus on 2014-05-22
- Did the computer run from the battery with Vista?

- Have you tried another version (12.04.4 LTS) and flavour (medium light Xubuntu, lighter than Ubuntu)? Or a community respin based on Ubuntu 12.04 LTS (Bento, Bodhi or LXLE)?

- The power manager (for battery etc) and wifi driver might work with version 12.04 LTS.

- You can try a USB wifi stick. In that case you should select one that is known to work 'out of the box' with linux.

- It is also worthwhile to try ***Knoppix***, which is known to be good at recognizing hardware, also old hardware.

---

### Post by mastablasta on 2014-05-22
lshw command will throw out the various hardware specs and chips.

---

