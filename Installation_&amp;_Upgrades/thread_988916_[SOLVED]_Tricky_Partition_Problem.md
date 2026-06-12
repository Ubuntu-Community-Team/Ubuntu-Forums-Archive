---
title: "[SOLVED] Tricky Partition Problem"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by Favux on 2008-11-21
I have an ancient PC that I'm dual booting between Win98 and WinXP.  I just added the WinXP install about 10 months ago.  Bios is ancient and after "fix" by software included with the new 160 GB hard drive I installed at the same time it now recognizes up to 137 GB.
When I tried to install Hardy Heron in May, hoping to make use of the 23 GB unclaimed by Windows, it wouldn't boot.  I had to use the XP rescue disk to fix the MBR and recovered my two windows partitions.
Reading up on it I discovered that I need the Linux kernel inside the 137 GB.  Now I would like to have another go at it with Intrepid Ibex.  So what I propose to do is shrink the Win98 partition (in a primary) by some the extra 3 GB I gave it and install /swap and /boot in that space between Win98 and WinXP (in an extended partition).  Will that work?  Proposed setup:

Win 98 (primary)
/swap  x1 or 1.5 ram (primary)
/boot  500 MB (primary)

extended
   WinXP        (logical)
   /       6 GB (logical)
   /home  12 GB (logical)

I have Partition Magic to shrink the Win98 partition.  For some reason, probably video, the latest Gparted CD boots to a blank screen.  I would greatly appreciate help on whether the above scheme is feasible.  Tips and hints and outright hand holding of the intrepid yet ignorant newbie that is myself would be greatly appreciated.

---

### Post by cariboo on 2008-11-21
To be able to help you a little better, what are the specs of the "ancient" computer:

cpu speed
video card
sound card
network card
ram

would be a good place to start.

Jim

---

### Post by Favux on 2008-11-21
cariboo907,

550 MHz Pentium III
Gigabyte 440BX motherboard 6ba (most recent available bios)
nVidia GeForce 6200
Creative SB Audigy
Linsksys LNE100TX(v5) Fast Ethernet Adaptor
1.00 GB RAM

Let me know if you need more.

---

### Post by dstew on 2008-11-21
Did you try booting the GParted Live CD with the "Force VESA" option? That might get you a usable screen.

---

### Post by Favux on 2008-11-21
dstew,
no I did not try that.  I'll give it a shot if I need Gparted to implement the partitions I decide on.  Thanks.

---

### Post by Favux on 2008-11-22
Rereading I see I was not as clear as I should have been about some of my questions.
First, am I correct that I can take "/boot" out of the root, "/ ", and just by mounting "/boot" Ubuntu will know enough to load the kernel, vmlinux etc. into it.  And this is enough for Ubuntu to then boot and find the "/swap" and then in the extended partition "/ " and "/home" past the 137 GB barrier?
Second, the "/swap" file should be in the cleared space and should be 1 to 1.5 times ram.  Ubuntu seems to want /swap at the end, but I've read /swap should be at the beginning of the disk or in the middle of the disk.  All of these different recommendations based on access speeds.  But I included it in the newly cleared space on the assumption that the kernel boot in "/boot" would be faster if it could access "/swap" quickly in a primary partition.  Am I correct on this guess?  Or could it also be in the extended partition beyond 137 GB?
Thanks.

---

### Post by caljohnsmith on 2008-11-22
> **Favux said:**
> Rereading I see I was not as clear as I should have been about some of my questions.
First, am I correct that I can take "/boot" out of the root, "/ ", and just by mounting "/boot" Ubuntu will know enough to load the kernel, vmlinux etc. into it.  
Yes, fortunately it is that easy. :)
> **Favux said:**
> 
And this is enough for Ubuntu to then boot and find the "/swap" and then in the extended partition "/ " and "/home" past the 137 GB barrier?
Second, the "/swap" file should be in the cleared space and should be 1 to 1.5 times ram.  Ubuntu seems to want /swap at the end, but I've read /swap should be at the beginning of the disk or in the middle of the disk.  All of these different recommendations based on access speeds.  But I included it in the newly cleared space on the assumption that the kernel boot in "/boot" would be faster if it could access "/swap" quickly in a primary partition.  Am I correct on this guess?  Or could it also be in the extended partition beyond 137 GB?
Thanks.
The main thing is to get the /boot partition inside your 137 GB limit, and then you should have no problems from that BIOS limitation as far as booting Ubuntu goes. I'm not aware of any significant speed advantage to relocating swap to the beginning/middle of the drive, if there is even a speed advantage at all; and unless you heavily use the swap space, I wouldn't think it would be an issue anyway. Also, to my knowledge, whether swap is a primary partition or logical partition really makes no difference to Ubuntu, and you can put swap past your 137 GB limit without any problems I think; again, the main thing is just getting all the boot files in /boot inside that BIOS limit, and you should be fine. :)

---

### Post by Favux on 2008-11-30
Outstanding!  I am now triple booting!  137 GB limit be damned, I now have access to the whole hard drive.  Hmmm, triple booting, maybe execessive?  Naahhhh.

After getting sidetracked by other projects (read procrastinating) and after much fear and trepidation (given the Hardy install fiasco) I went ahead and installed Intrepid.

First I got Gparted live CD to work to make sure that it and Partition Magic agreed.  Unfortunately dstew's suggestion of trying "force VESA" didn't work so I went to the Gparted forums.  There I discovered several other folks were having the blank screen problem.  The moderator suggested reverting back to 0.3.4-8 or 0.3.4-7 (I was using 0.3.9-4).  One forum participant reverted back to 0.3.4-6 and said it then worked.  Blithely ignoring this advice I downloaded the latest 0.3.9-13.iso.  It still led to a blank screen, but now before X started it offered 3 choices; go ahead, try manually configuring X, or go to the command line.  I choose manually configure and after a few attempts got one to work.  Amazingly the nv driver didn't work but VESA 800X600 or 1024x768 with 8 bit color did.  After Gparted confirmed what Partition Magic was showing me I proceeded.

In Win XP using Partition Magic I shrunk Win 98 down 2 GB.  Then I formatted a 500 MB ext 3 partition (primary) for "/boot".  The Ubuntu Partition wiki said 100 Mb to 300 MB max. but I left it a little roomy.  Thanks to caljohnsmith for confirming that separating "/boot" out like this would work.

I also made a 1.5x memory (1.5 GB, the Partition wiki said size of RAM) "/swap" file (also primary).  I figured at this point why take the space from the Ubuntu install when the Win 98 partition could spare it, as I'm steadily de-emphasizing it.  Using a belt and suspenders approach (since my Partion Magic is kind of old) I then booted into Gparted live and made sure it saw the saw the same things and was happy.  It wanted to redo the "/swap" file so I let it.

I then booted with the Ubuntu 8.10 live CD.  Compliments to the Ubuntu team.  The partitioning portion of the install process was much clearer and more flexible than in Hardy.  The only gripe would be that when I was mounting the 500 Mb "/boot" partition there was only a box to enter the mount point in.  However when I got to formatting the unallocated portion of the extended partition  to ext 3 there was a drop down menu with suggested mount points ("/boot" was one of them) and I chose "/".  A similar drop down menu earlier would have been helpful.  Never too much hand holding when messing with partitions.  I decided not to make a separate "/home" logical partition.

The rest of the install went without a hitch.  And here I am-a proud triple booter.

---

### Post by caljohnsmith on 2008-12-01
Congratulations on getting your triple boot working; cheers and have fun with all your OSes. :)

---

