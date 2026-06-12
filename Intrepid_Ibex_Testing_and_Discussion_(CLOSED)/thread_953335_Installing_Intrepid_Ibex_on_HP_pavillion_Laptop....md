---
title: "Installing Intrepid Ibex on HP pavillion Laptop..."
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by seemanta on 2008-10-20
Hi,

I am waiting eagerly for Intrepid Ibex to be released and also planning to buy to a laptop to celebrate the release.

I have zeroed down on the pavillion DV2910 TX HP model as it is giving me the best value for money: It has the following configuration:

Intel Core 2 Duo 2 GHZ, 2MB L2 cache, 667 FSB
14.1 inch screen
3 GB RAM
320 GB HDD
128 MB dedicated NVIDIA graphics card
1.3 MP integrated web cam + microphone
Fingerprint reader

I want to have a dual boot system with Ibex and Vista over it.

The only catch is: HP does not provide the vista DVDs. On top of it, HP has some retarded concept of a recovery partition.

My question is: Will I be able to format the laptop after purchase, install Ibex, and then use the recovery partition to recover Vista, without overwriting the Linux that I just installed ?

Any helpful pointers would be greatly appreciated!

regards,
Seemanta

---

### Post by Adremelech on 2008-10-20
no, vista will overwrite grub and you wont be able to boot linux if you install vista last. i personally just downloaded a copy of the windows vista dvd off of tpb and use the LEGAL key that came with my compaq F756NR to install vista and then linux.

---

### Post by sergiom99 on 2008-10-20
I made a set of recovery DVDs (it only lets you do it once, so I did it as soon as I got my laptop) and then removed Vista, the recovery partition and installed XP and Kubuntu. Couldnt care less for Vista.

PS: what is tpb?

---

### Post by Sef on 2008-10-20
> PS: what is tpb? 	

The Pirate Bay.

---

### Post by cl0ckwork on 2008-10-20
i have recently installed hardy on my girlfriends laptop.
she has the HP dv6000 series and it came with an 8 gig recovery partition

i just deleted therecovery partition and installed ubuntu in there, everything works on each side.

not sure how much memory you want to allocate for each system but that would by far be the easiest way

and im not sure aobut your position but i am a student at college and i was able to buy a vista install disc for about $15 due to the campus open software agreement of something :D

---

### Post by mclavey on 2008-10-22
Intrepid ibex will not install on a hp dv6000 .... it will not support the video card or the wireless card.

---

### Post by converted on 2008-10-23
I've got an HP DV9910US and it has been happy under both Hardy and Ibex.  Webcam, cardreader, hardware buttons all work.  Under Hardy I had to use MadWifi for Wireless drivers, but I don't even need to do that under Ibex.

However, looking at the hardware specs for the model you mention, they are quite different.

I don't know the status of the Intel integrated wireless bug, or whether the Intel chipset in this model would be affected, but assuming that the bug is fixed at release I'd be surprised to see Intel wireless unsupported.

What I can tell you is how I installed Ubuntu --

At some point I'll probably get rid of the Recovery partition, but given the size of the hard drive I left it in place initially.

I just used a GParted LiveCD (I prefer a GUI for those kinds of things when possible -- the interface is almost a direct clone of Partition Magic) to shrink the Vista partition, then booted into Vista just to check it, and then rebooted off of the Hardy installation disk.  At install time I told Ubuntu to use all the free space on the drive.  This has worked like a charm, and I can still boot into Vista and could (presumably) make use of the Recovery partition functionality if I so chose.  

I'd be surprised if your hardware isn't supported at *release* of Ibex, and I'm even kind of surprised if it's not supported now, with the possible exception of the Intel wireless situation.  My suggestion would be to do what I've described above, since it will *NOT* disrupt your Vista installation at all.

And while I would never suggest piracy, you will have a valid and legitimate Vista key.  If you aren't too picky about *where* you get your media, I'm sure you can get your hands on installation media.  

If you want to be fully on the up and up, I've also been told that manufacturers who do not supply installation media for the OS will do so for a small fee to legitimate owners of their systems. (They may even be required to do so.) I'd guess that if you register your laptop when you get it, then call the same day about installation media, they'll send it for only a few $.  I don't know for sure that they will do this, but I've seen it mentioned more than once.

I would not expect that you could reinstall Vista from the recovery partition after installing Ubuntu without trashing your Ubuntu install, either due to the recovery reclaiming the entire disk, or due to Vista messing with your boot sector (which I suppose could be undone with a bit of fiddling).  As someone mentioned, you can make a set of DVD's at first boot, but again I expect these will be configured to make use of the entire disk, so while they may make it safer to delete the recovery partition, I don't think you'll be in any better shape if you want to reinstall Vista.

Assuming that Ubuntu works on that hardware, I think your safest route is to do what I described above with Gparted and etc.

*I'm not at all an Ubuntu or Linux expert* <-- Disclaimer :)

-- Joe

---

### Post by MJWitter on 2008-10-23
> **mclavey said:**
> Intrepid ibex will not install on a hp dv6000 .... it will not support the video card or the wireless card.

Sorry but i have Intrepid running perfectly on an HP dv6363eu.  Wireless works and graphics as well.. All i had to do was disable the broadcom driver and wl worked..

---

### Post by Cyber-J on 2008-10-23
> **MJWitter said:**
> Sorry but i have Intrepid running perfectly on an HP dv6363eu.  Wireless works and graphics as well.. All i had to do was disable the broadcom driver and wl worked..

It's working fine on my dv6305us as well. I'm using the AMD64 beta edition. I enabled the broadcom drivers and wifi is working fine - no ndiswrapper or fwcutter. :)

---

### Post by waspbr on 2008-10-23
I don't see why the computer would not be supported by intrepid ibex, I am saying that based on the fact that I have a HP laptop myself that runs perfectly with ibex

---

### Post by Ayuthia on 2008-10-23
I have kept the recovery partition in my laptop (dv6338se) and desktop and shrunk the Vista partition through Vista.  I then installed Ubuntu in the extra space.

My laptop then had a "recall" where the wireless card was not found by the motherboard and I was able to rebuild vista over my laptop.  This allowed me to make my laptop look like how it was when I purchased it (yes I was too chicken to show that I used Linux).

The other thing that you can do is make the recovery DVDs in case something goes bad in the recovery partition.  That is what I did.  Just call me paranoid.

---

### Post by myddewji13 on 2008-10-23
> **Ayuthia said:**
> I have kept the recovery partition in my laptop (dv6338se) and desktop and shrunk the Vista partition through Vista.  I then installed Ubuntu in the extra space.

My laptop then had a "recall" where the wireless card was not found by the motherboard and I was able to rebuild vista over my laptop.  This allowed me to make my laptop look like how it was when I purchased it (yes I was too chicken to show that I used Linux).

The other thing that you can do is make the recovery DVDs in case something goes bad in the recovery partition.  That is what I did.  Just call me paranoid.

+1 ... different lappy though... and make sure you use the vista to edit its own partition not gparted... learned my lesson the first time i tried linux... (also another quirk...windows partitions do not mount properly if i restart windows then boot into ubuntu ... i have to shutdown from vista then boot ubuntu)

---

### Post by converted on 2008-10-23
> **myddewji13 said:**
> and make sure you use the vista to edit its own partition not gparted... learned my lesson the first time i tried linux... 

I'm not saying *don't* use Vista to resize, but I do want to point out that I specifically used GParted due to not being sure whether I could trust Vista to do it on my DV9910US, and had no problems at all.

---

### Post by pBeseda on 2008-10-23
I have Ibex running on my dv6000 as well. Almost perfectly, with almost no hassle either, I'm lucky sometimes. Recently though, it gets stuck during boot...(starting a new thread)

---

