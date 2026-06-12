---
title: "P4P800 Deluxe install issues (solved)"
date: 2006-03-29
forum: Installation &amp; Upgrades
---

### Post by exkalibur on 2006-03-29
Untill today, I used my old boxes (PIII, II and MMX) to run various distros. I had tried Live CD's on my P4 and everyone of them had failed.  Today I had decided that Ubuntu deserved to be on a better machine and went on with the install.....

First : unplugged my Raid SATA drives (Redmond OS) and swapped the IDE caddy for a new drive dedicated to Ubuntu.
Then put in the Live CD to test.....It would hang after the hardware detection for a while before coming up with a " couldn't mount CD rom drive ". Ok, Back to square one.....Go in bios and change the IDE setting from "enhanced" to Compatible with only the P-ATA enabled....Voila ! Perfect install at blazing speeds. Finally Ubuntu is running on a more worthy machine.

Drapper......Here I come.

Edit : Unplugging the raid and disabling it was already getting old.....Workaround for now : irqpoll at the grub line. Using ICH5R raid SATA controler seems to be an issue with lot of users.

---

### Post by tbg58 on 2006-03-29
Nice post -- whether you intended to or not, you showed some folks a really good methodology for testing things out:
1.  Unhook the old hard drives with any other OS you want to hold onto for now.
2.  Hook up a hard drive that will be dedicated to Ubuntu.
3.  Run the LiveCD first to see if the current version of Ubuntu is going to pick up all your hardware devices.
4.  Adjust the BIOS if necessary.
5.  After a successful dry run with the LiveCD, rock and roll.

Hope you don't mind my schematization -- your post was a pretty good tutorial by example.  Kudos!

tbg

---

### Post by nyinge on 2006-06-25
Thanks for the info, exkalibur.  :)  I've now decided to give up on installing Kubuntu on my box using Intel ICH5R sata raid controller.  I've also googled around, and the results were not too good.  I'm just gonna hook up an old IDE drive for it.

---

