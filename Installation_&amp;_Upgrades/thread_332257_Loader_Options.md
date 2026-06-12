---
title: "Loader Options"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by jcq on 2007-01-05
I had a post about this in [another thread]("http://ubuntuforums.org/showthread.php?t=299587"), but since I hadn't yet seen an answer, I figured I should post it here where it seems applicable.

Because of the problem described here:
[http://www.brianparsons.net/?p=63](http://www.brianparsons.net/?p=63)
I am unable to use the default setup of Grub as my boot loader.   Default setup would prevent me from accessing the DVD drive in both Linux and Windows (I am dual-booting).   Apparently there are two possible fixes.  One is to add the "acpi=off" option to Grub, and the other is to use LILO.   

The questions I have then are as follows:
[LIST=1]
[*]Is there any reason to not use LILO?   Is Grub better in some way?  Why did it become the preferred solution?
[*]When/How do I install LILO?  I don't remember, is it an option during the initial install off the disc?   If not, what's the proper procedure for switching boot loaders?
[*]I *believe* that no matter what, if I don't install Grub on the MBR, Windows will be unaffected by this drive problem.   If I use the Windows boot loader as the primary one, what command do I add to it for Ubuntu?  (Drive has 3 partitions -- Windows is on primary, Linux on 2nd, and swap partition on 3rd)
[/LIST]

Thanks in advance...

---

### Post by jcq on 2007-01-07
Nobody can answer those questions for me?

I'm trying to get answers to those before starting with my install.

Thanks...

---

### Post by jcq on 2007-01-08
Shameless bump.

I want to do the install today, but I really would like a little info about how one would go about  (at minimum) installing Grub on the Ubuntu partition, not the MBR, or installing LILO instead of Grub.

Surely there's somebody out there that can help with that info?

---

### Post by logos34 on 2007-01-08
> Is there any reason to not use LILO? Is Grub better in some way? 

Well, it does have the 'Automagic' kernel update feature.

[LILO vs. GRUB]("http://lwn.net/Articles/89772/")

---

### Post by jcq on 2007-01-08
OK, so I tried adding the acpi=off option in Grub.   It allowed me to access the DVD drive in Linux, but it also caused me to lose network functionality.    Sorry if this is a stupid question, but why would that be?   What other side effects of "acpi=off" might there be?

I guess ideally I'd be happy to just use the Windows boot loader as main...   how would I set that up?   I mean, is Grub already installed on the / partition as well as the MBR?   So could I just reference that partition in the nt loader and have it work?

Can somebody point me to the proper procedure to switch to LILO?   Or better, tell me how to have Grub only handle linux and also how to avoid losing network functionality with acpi set to off?

---

