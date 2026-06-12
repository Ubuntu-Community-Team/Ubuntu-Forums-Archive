---
title: "hdd cannot be found in ubuntu. (i really need help!)"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by jay1097 on 2007-10-10
hey guys,
First off im trying to install Ubuntu on my new PC. i have a new asus mobo (dont remember the name), a ATi x1550, a AMD AM2 stocket dual-core, 2 gigs of ocz gold ram, 250 gig hdd (Westrn digita SATA), a supermulti LG dvd drive, and a TV tuner.

So my problem is that when i put my Ubutnu 6.10 liveCD in everything works fine but if i go to install Gparted it cannot find a hdd to partition. The funny thing about this is that my bios sees the hdd, i can install windows without much problem, and i made a Gparted livecd and it is able to see and partition the hdd. However, when i go to install ubuntu gprated doesn't see anything, at all it basically says no devices found.

So far ive tired a couple things, first i cleaned my hdd completly of my windows install, then i used my gparted disk to make sure that it was all cleaned out and not paritioned or formatted at all. Then i try to install ubuntu and again nothing, so i then switched my SATA cable and made sure eveything was connected in my PC, still no luck.

Right now im out of ideas and there doesn't seem to be any post on the forums that can help me.
So if anyone can offer some advice im all ears. i have a gpartedlive CD, ubutnu liveCD for 6.10 and 7, i also have the textbased install for 7 and i have 6.06 release as well none of which seem to be able to see my harddrive. im using the 6.10 CD because ive used it before to install ubuntu on my laptop and i know that it works. i also have a supergrub CD but i dont know what if anything to do with it.
Thanks in advance for any help. and keep in mind that windows can be installed on this harddrive so i don't think its a hdd defect.

---

### Post by Pumalite on 2007-10-10
Ubuntu does not install in unallocated space. Use Gparted to make partition of your whole hdd and format ext3. Ten install.

---

### Post by jay1097 on 2007-10-10
i have already tierd that and i still have the same problem. infact my hdd is now partitioned as ext3 and when i try to install ubuntu, gparted still cannot find the hdd. usally when u try to install ubuntu gparted shows you the breakdown of your hdd space, but whenever i get to that stage of the installation it loads for a bit and then there is nothing being showed about the harddrive i literaly get stuck at step 5 of the install process, i just have no options when i get there. its very frustrating because ubuntu is usally extremly easy to install and ive done it some many times before and never once had a probelm like this with gparted.

---

### Post by Pumalite on 2007-10-10
Post your specs. The Alternate CD might be your answer. Also I suspect your iso. Did you do md5sum on it?

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by jay1097 on 2007-10-10
i know my iso is fine i burnt it with 1x write and i have used the same CD to install ubuntu on another PC. i dont know what md5sum and i will try doing it when i get home tonite and see if that works. i know for sure it is not the iso i even used by 6.06 CD which i got from the ubuntu community (ship-it i think) and i have the same problem with that one aswell. my comps specs are posted in my first post, like i said i can install windows without a problem but i would much rather have a linux box than an other crappy windows pc.

---

### Post by boingo-bo on 2007-10-10
and-or combination of chipset on motherboard.
I had a problem in the past installing a version of fedora core (I forget which one) on a system I have which has no IDE, only SATA (including CD) and has only SATA drives - the chipset version was INTEL P965 (I think).

Anyway - it was a similar symptom. able to boot fine from live cd, but install could not find HD. - The solution was to do the install with a distribution which had a newer version of the kernel - one which had support for my Hardware. (I think Kernel version 2.6.18 - but I forget for sure)

I am now installing Ubuntu on an identical system. - I purposely picked version 7.04 (Fiesty Fawn) because it has a newer Kernel (2.6.20)

if I were you I would download an iso of 7.04 and try it out.

---

### Post by jay1097 on 2007-10-10
alright im going to try that out once i get home, i never thought that i would have a compatabilty problem with a harddrive, but you could be onto something about the SATA thing, btw my mobo does have ide slots (i use one from my cd drive) but i didn't buy a ide hdd because i think the SATA system is better.

---

### Post by Pumalite on 2007-10-10
That escaped me, but he is right; I've heard that complaint before. I'm not sure, but I think a bug was filed to that effect.

---

### Post by boingo-bo on 2007-10-11
she :)

---

### Post by Pumalite on 2007-10-11
Good catch!

---

### Post by jacksonz123z on 2007-10-12
Sounds like you need to load SATA drivers so that your HD can be recognized.   I have the same problem with a Gigabyte Mobo.   I am going to wait till Gutsy and try again.  Otherwise, linux drivers are available.  However going back to PATA could be easier!

---

### Post by jacksonz123z on 2007-10-20
The good news is that the Gigabyte GA-VM900M motherboard SATA drivers are now recognised by Gutsy automatically.  This motherboard now works perfectly.

---

### Post by jay1097 on 2007-10-23
Thank you for the help everyone. i just installed gusty and it worked no problem i guess you were right about the SATA drivers. Anyway thanks again i really apperciate the help.

---

