---
title: "simply cannot install ubuntu"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by yyiinn on 2008-10-04
:confused::confused::confused:
I have a repeating issue installing ubuntu...

the system simply will not accept ubuntu, i'm a complete linux noob so please excuse what might seem to be a very simple issue...

my system is as follows:

AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
Corsair DDR2 PC2-5300 (333 MHz) 512 MBytes x2
SATA Western Digital 80GB HDD
IDE Western Digital 160GB HDD

and no matter what i try i simply cannot install ubuntu (32bit + 64bit) on my system, I have tried downloading the iso twice and burnt it into two different types of CDR (thinking it might be the disk or download) but everytime i boot into the loader it hangs during the slide bar progress at the beginning. 

Although this happens it will allow me to install ubuntu studio ( 64 bit) although it wont boot into ubuntu studio after the install, Ive even tried opensuse11 with the same result it simply hangs during the initial boot. 

Yet it installs and runs mandriva 2007 with no problems apart from the fact i have no wifi and it states that ndiswrapper is not installed even tho it is. Im not expecting help with either opensuse11 ubuntustudio or mandriva but its driving me mad as too why ubuntu will not install onto my system...

any help or advise would be much appreciated... 
:confused::confused::confused:

---

### Post by Sef on 2008-10-04
If you run the Live CD for a while, how do they run?

---

### Post by yyiinn on 2008-10-04
from a cold boot with the disc in it. if i select to run ubuntu without altering the system the progress bar gets to the last section of the bar then the system hangs and the display goes a bit barmy.

if i try the wubi install its completes the progress bar after installation but then i get get a white "_" in the top left corner and nothing else happens, i left it like that for 5 mins thinking it might just take a min to boot but it just hangs.

---

### Post by hansdown on 2008-10-04
Hi yyiinn.

Try downloading the alternate iso and see if that works. Also, burn the cd at the slowest speed possible.

Hope this helps.

---

### Post by yyiinn on 2008-10-04
ive tried the alternate dload but ive always kept my burn speed to max... i thought the need to burn at slower speeds had been resolved long ago....

what the hell ill give it a go

---

### Post by mikjp on 2008-10-05
Try to give boot options [FONT="Courier New"]noapic nolapic nosplash[/FONT] to kernel to locate the problem. Might well be a problem with graphics card. What card are you using?

---

### Post by xreaper on 2008-10-05
> **yyiinn said:**
> ive tried the alternate dload but ive always kept my burn speed to max... i thought the need to burn at slower speeds had been resolved long ago....

what the hell ill give it a go

lol nice attitude you've got there. Yeah, I'd have to agree, I had to burn at the slowest rate possible for it to work for me. Its generally only because of how big the image file is.

---

### Post by yyiinn on 2008-10-05
nothing too fancy... its an ATI X550

and i tried burning another CD at the slowest speed x16 with two different iso's and same issue.

might sound like a stoopid question but how do i add the commands to the kernel?

---

### Post by Spaceman9 on 2008-10-05
SATA Western Digital 80GB HDD
IDE Western Digital 160GB HDD

The fact that you have a SATA and a PATA drive could be the problem. The Ubuntu installer doesn't handle that combo very well.

You said your're new to linux. Try Mandriva 2008.1 and I bet that won't have a problem with your SATA and PATA drives. Don't use a Mandrive 2009. That's still in testing and unstable.

Any Ubuntu based distro has a problem with a SATA/PATA drive combo. Most linux distros have a problem as well. Even Mandriva will have a problem I bet. So Mandrive 2008.1 might not. It's worth a try. 

The solution with Ubuntu is disconect the SATA drive, install Ubuntu, reconnect the SATA drive and everything should be ok.

Take a look at this thread [https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/32357](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/32357)

Below are the posts from other users with this problem. 

 X3 wrote on 2008-07-06: (permalink) 

Right after I downloaded and started installing the Ubuntu 8.04.1 LTS on a mixed sata/ide drive environment I experienced similar issues when placing the MBR onto the IDE drive that I had partinoned and hadson partition 1 XP Pro and on Partions 2 Ubuntu and on partition 3 linux swap.... the other sata drives just contain data and I thought not much of this untiol I repeatedly experienced error 21 no matter where I placed the ubuntu mbr...

Work around is to unplug the sata drives do the install and then when all is fine plug them back up and all is well....

Solution? well just do what I said...
 Dimitrios Symeonidis wrote on 2008-09-11: (permalink) 

yes, the problem seems to come from the order of the hard disks, something that is decided by the bios.
unplugging disks, like X3 suggested, is a workaround, but it obviously cannot be the solution. we need to find a better way to do this...

---

### Post by yyiinn on 2008-10-05
Cheers for the info I'll give it a try tomorrow. really cant be bothered doing it tnite. I'll post back tomorrow the result.

---

