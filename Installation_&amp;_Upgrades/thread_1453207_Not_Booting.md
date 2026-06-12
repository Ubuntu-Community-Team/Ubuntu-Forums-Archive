---
title: "Not Booting"
date: 2010-04-12
forum: Installation &amp; Upgrades
---

### Post by Macraze on 2010-04-12
The first linux distro I tried to install on my new system was ubuntu(9.10). The installation worked fine but it would not boot. So I just decided to install some other linux distros(fedora and openSUSE) but I was not satisfied. Hoping that the bugs were fixed I downloaded the 10.04 beta and installed it. Everything went smoothly as before but when I got past the bios screen I would not boot. I tried reinstalling another time with different settings(not manually doing the partitions) and the same thing happened. In order to boot into windows I put in my boot132 disc and Ubuntu was listed as a os to boot into(so I think but am not sure that it is not the boot loader). I have no idea what is wrong.

Thanks in advance for any help.

---

### Post by drreed on 2010-04-12
> **Macraze said:**
> ...The installation worked fine but it would not boot. So I just decided to . . .

Hmmm . . .answered one like this earlier. Did you verify the checksums of the .iso file you downloaded (assuming thats how you installed it?) That's critical. Then make certain you verify the burn by running the "verify installation media" option from the install screen. Verifying the disk with your burning utility isn't good enough.

>  Hoping that the bugs were fixed I downloaded the 10.04 **beta** and installed it. 

*emphasis added by me to make a point*

A beta by it's very nature is buggy. That's what a beta release is, the **first** release tossed out there to see what blows up so that you can fix it. :P At some point, you really need the community to give it a drive. Theer's only so many possible situations developers can try by themselves. It reminds me of the 70's era Samsonite commercials with the Gorilla and a suitcase. Also reminds me of everything microsoft has ever released, and they were'nt beta's!

If you've followed step 1 and it still won't install, I'm not sure what to tell you.  Seferal years ago I had a similar problem, but I knew why Ubuntu wouldn't run, it whined about my Radeon XT850 (or w/e it is) Fedora Core 5 ran without a hitch. Do you have any oddball parts, ya know, the newest and greatest little gadget with 16 pipelines instead of the usual 14 like every other model? You don't get an error?

Don't try 10.4 yet, get 9.10. Verify your iso and burn.

---

### Post by Macraze on 2010-04-13
Thanks for the quick reply! So I burned another copy of 9.10 and checked verify and it said nothing out of the ordinary. I will attempt to install it and see how it goes...

---

### Post by drreed on 2010-04-13
> **Macraze said:**
> Thanks for the quick reply! So I burned another copy of 9.10 and checked verify and it said nothing out of the ordinary. I will attempt to install it and see how it goes...

Checked verify? Like the checkbox in your burning utility, or by running the one from the menu? Make certain you verify the checksums of the file you downloaded, if you don't know how just ask

---

### Post by Macraze on 2010-04-13
Oh thats what you meant. I will do that. Do you think it could be because I am on a amd machine and I downloaded i386 version? It still booted into the live cd. Should I download the amd64 version because I am on a amd 64 bit pc

edit:
I checked it and the md5 sums were the same.

edit2:
I forgot to say the installation worked but it still wont boot. I get a message that says "Error: No Active Partition"

---

### Post by oldfred on 2010-04-14
That is either a windows error or a BIOS error. Ubuntu calls it the boot flag. Windows calls it the active partition. Windows requires one primary partition be flagged with the boot flag (active). Linux does not use the flag, some BIOS (intel otherboards maybe others) will not boot unless a primary partition has the boot flag.

You can set the boot flag with gparted from the liveCD. Right click on the partition and manage flags.

---

### Post by slashwannabe94 on 2010-04-14
your problem sounds like a corrupt cd. i would make a fresh o/s cd and then check the cd for error my friend. i don't see why it should not work, dual booting causes allot of problems, try your best to steer away from that dark room and stick to a hard drive per o/s much easier and efficient.

---

