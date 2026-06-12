---
title: "Emachines problem?"
date: 2005-12-03
forum: Installation &amp; Upgrades
---

### Post by theimp on 2005-12-03
I got an emachines T3990 and was trying to use a live CD for Ubuntu I burned.  My computer, however, has decided that it will not boot from the CD drive but rather my hard drive.  I attempted to get into the BIOS settings to fix the problem, but once I got there I couldn't find anything that suggested it would allow me to boot from my disk drive first.  Help please?
](*,)

---

### Post by bwog on 2005-12-03
I couldnt find it on the net, but the option has to be there (one would need it to boot from a windows CD for instance). Check again I would say.

---

### Post by mfarquhar on 2005-12-03
what bios do you have (i have 2 Emachines and 2 different bios)

there should be a BOOT menu in there if you have the normal one. i'll check back with you after i check my machines

---

### Post by aysiu on 2005-12-03
I've had two different eMachines computers.
Both were able to boot from CD.
Keys to try during bootup (when the big *e* appears on the screen):

Delete
F1
F2
Escape

---

### Post by mfarquhar on 2005-12-03
i checked my machines

CTRL+ALT+DELETE gets into mine (don't do this once ubuntu starts up because it will force the machine into an immediate restart)

if you have PHOENIXBios
go to the BOOT menu and put the CD-ROM as the first boot thing

if you have AMIBIOS double-click the advanced button, and change the boot order

---

### Post by theimp on 2005-12-04
I got into the BIOS settings (making sure my pesky man had his attention elsewhere, vile backseat driver) and browsed around to find the proper section for the order of boot settings.  Had to press Delete a bunch of times to get into BIOS (despite the screen's suggetion to hit F2).  That is quite wonky, I must say, having on-screen directions that don't work.  Ick.
I finally found the order in which the computer boots and it said that it did boot the CD-RW drive first.  Well, crud.  The next things in my thought-process (wrong or not) points to the CD I burned.

I used my burner for this CD after I'd made certain all of the information had been downloaded into my temporary file.  I don't know if Gateway's Win XP w/sp2 does bad things to the disk and that may be the problem?  I made sure I got the Live CD version for the Intel processors since I have an Intel Celeron D Processor 335, so I don't think it is because of the processor.  Should I be using a specific burning program for this?  I've burned Windows programs to this specific type of CD-Rs before without any problems, and the label says there is 700MB of space on these disks which leaves a little extra room after burning the 670MB Live CD program.

Perhaps there is a trick to getting it to boot the disk first (like getting into the BIOS settings)?  Any suggestions?  I'm thinking, perhaps, that trying again to order a Live CD over the mail to see if that will work may be my best option.
  The first time I tried to order the CD didn't work, though I found plenty of interesting information and learned new things so it wasn't a waste of time. :]

---

### Post by bwog on 2005-12-04
You need to burn the iso as a (bootable) image. You do not need a special burning program, Nero does the trick like many others. It may help to burn the cd slowly.

The CDrom has to be first in the boot order, but you already managed that, if I understand you well.

To be sure you can verify the CD.

Just come back here if you cant figure it out.

---

### Post by theimp on 2005-12-04
Sounds good to me. :)

How does one verify the CD?  My CD says the program is listed as an "ISO file" and you were mentioning an ISO image?  I did not alter it in name or anything else when I burned it and my programs did not give me a choice as to how I wanted it done (it took 7 minutes).  I tried shutting down and restarting my computer, and again no Ubuntu (just XP).

---

### Post by aysiu on 2005-12-04
[Verify disk image](http://www.linuxiso.org/viewdoc.php/verifyiso.html)
[Burn ISO with Nero](http://www.wizardskeep.org/mainhall/tutor/neroiso.html)
[Burn ISO with Easy CD Creator](http://www.wizardskeep.org/mainhall/tutor/cdcriso/cdcrtiso.html)

---

### Post by theimp on 2005-12-08
I've been talking to my grandfather as I am working on this because my dad was saying he is a fan of Ubuntu.  My grandfather was saying that when he downloaded Ubuntu he was very pleased for its completeness, but it re-formatted his hard drives without consulting him first.  Luckily he had the proper disks to be able to boot Windows back onto his computer.  Being as my particular version of the emachines computer only comes with a retrieval program I would not be able to download Ubuntu with good concience (as I am not the only one who uses this computer).  My retrival program resides in one of my hard drives and if it were re-formatted I would be screwed (as I do not have $100 to buy XP) so perhaps it is better that I have not been able to get the Live CD to work.
I'm sorry I put you guys to all this trouble.  I was hoping to try out this operating system for myself.  Perhaps when I get the money together for a new motherboard and processor for the ATX we have I shall have a proper computer to play with.  Thank you for your time.

---

### Post by canadianwriterman on 2005-12-08
[QUOTE=theimp]I've been talking to my grandfather as I am working on this because my dad was saying he is a fan of Ubuntu.  My grandfather was saying that when he downloaded Ubuntu he was very pleased for its completeness, but it re-formatted his hard drives without consulting him first.  Luckily he had the proper disks to be able to boot Windows back onto his computer.  Being as my particular version of the emachines computer only comes with a retrieval program I would not be able to download Ubuntu with good concience (as I am not the only one who uses this computer).  My retrival program resides in one of my hard drives and if it were re-formatted I would be screwed (as I do not have $100 to buy XP) so perhaps it is better that I have not been able to get the Live CD to work.
I'm sorry I put you guys to all this trouble.  I was hoping to try out this operating system for myself.  Perhaps when I get the money together for a new motherboard and processor for the ATX we have I shall have a proper computer to play with.  Thank you for your time.[/QUOTE]

First of all, if you truly have the Ubuntu Live CD, it will not reformat your hard drive because it does not install itself on your computer (although I belive you have an option to install it after the Live CD is up and running). Perhaps it was really the install CD that your grandfather had. As far as reformatting your entire hard drive during an install, you have to be careful to read the install options thoroughly. There are options that will take over your hard drive and erase everything else. But you should choose the option to partition your hard drive to share the hard drive with Windows.

In any event, if you are nervous, just ensure that you download the file clearly labelled as Live CD.

---

### Post by aysiu on 2005-12-08
[QUOTE=theimp]My grandfather was saying that when he downloaded Ubuntu he was very pleased for its completeness, but it re-formatted his hard drives without consulting him first.[/QUOTE] This is simply not true. Maybe your grandfather's eyesight isn't so good, or maybe he hit <Return> through the choices too quickly before getting a chance to read them. During the installation, you always get this dialogue (see attached image).

You then have a choice to erase your entire hard drive or repartition. You have a choice. Ubuntu asks you.

---

### Post by tay on 2005-12-09
the emachines i have around that i play with sucks.   the pci network card never configured with the bios, and the screen size don't fit the screen.  emachines..:confused:

---

