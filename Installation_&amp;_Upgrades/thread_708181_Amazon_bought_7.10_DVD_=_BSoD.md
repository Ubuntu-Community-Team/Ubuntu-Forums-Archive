---
title: "Amazon bought 7.10 DVD = BSoD"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by afs97209 on 2008-02-26
Bought a Ubuntu DVD from Amazon. Loaded it in my HP Pavilion DVD drive. Boot. First menu comes up. Choose 1. Ububtu graphic with orange load bar finishes, next get cursor in upper left corner, then goes BSoD.

Reboot. Same thing happens. BSoD.

Reboot. First menu comes up. Choose 2. safe graphic modeUbubtu graphic with orange load bar finishes, next get 4 lines of text, then that goes BSoD.

Reboot. Try safe mode again. BSoD again.

Try text install mode. no black screen of death at least. Get to partitioning. Get a menu where I choose between several guided choices or manual. I certainly can't manually set-up a dual boot partition. Choose the only guided choise that doesn't involve reformating the whole disk. Get told... 

"...Before I can select a new partition size, any previous changes have to be written to disk. You cannot undo this operation...."

Excuse me? I'm not allowing this or any other software to write nothin' that can't be undone before I know exactly what sort of partitions the software intend to install.

So... forget the text install from the DVD, too.

So now my only option at this point is a virtualbox installation. I'll make a long story short. No BSoD this time. I am only able to get a basic install. However, the installation is recognizing nothing in the virtualbox. No network. No internet. No audio. It won't even recognized the DVD player I just installed it all on. So I can't load one single package from the DVD to the basic install.

I couldn't  have a more "standard" setup here. HP Pavilion. Intel Celeron chip, NVidea GeForce FX5200, Samsung DVD player, Realtec AC 97 audio. It's not a flawed/scratched DVD that's causing the BSoD, because it installed from the DVD into the virtualbox just fine.

---

### Post by Carl H on 2008-02-26
> **afs97209 said:**
> Before I can select a new partition size, any previous changes have to be written to disk. You cannot undo this operation

That sounds like it's going to shrink your Windows partition to make room for your Ubuntu installation, and it's telling you that it has to do that before it can do anything else. 

You could always shrink your Windows partition using a Windows based tool if you feel more comfortable with that?

---

### Post by NilsHG on 2008-02-26
Be sure to backup your important data before continuing with the partition of your hard drive. if anything goes wrong you will have your data at least.
there are plenty of howtos on this forum and the web on how to partition your disk for dual boot. try the forum search and google (or the search engine of your choice)

---

### Post by afs97209 on 2008-02-27
I haven't been able to reply until now. 

The attempt to build a dual boot XP/ubuntu system seemed to go fine as I was going through it. Shrank the existing primary partition, then made the new ones for ubuntu. Then installed ubuntu system. That seemed to go fine. Finished up. Rebooted after everything installed, got to the ubunbu orange bar graphic, and then got the Black Screen of Death all over again.

Tried to reboot through grub. Ubuntu Black Screen of Death.

Try rebooting back into windows. I'm forced into a disk scanning utility, then windows says the hard disk is compromised. Try rebooting through every different combination of safe modes, etc. All I get from windows is the hard drive compromised blue screen of death. Oh... and sonmewhere along the way grub just completely freaking disappeared. Went back to the normal windows start up for a few seconds, then the blue screen of death with the text warning on it.

Wooow... you guys managed to advise me into two different screens of death on two different operating systems at the same time. That takes talent. 

So I went straight through early morning-day-evening to now reformating my hard drive, installing the recovery system, drivers, etc. security updates, etc. Fun stuff.

Thanks for the help guys.

---

