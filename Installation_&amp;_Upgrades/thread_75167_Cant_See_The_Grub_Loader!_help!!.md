---
title: "Cant See The Grub Loader! help!!"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by haskan on 2005-10-13
I Cant See The Grub Loader Where You Can Chose Os And I Install It 4 Without Getting In The Grubloader Caus All I Se Is This Message: Hardisk Or Partiton Not Activ. And This Was After I Installed Kubuntu And Rebootet

Thank You For The Anwsers!!!:) 


Ps: I Used Magic Partition And Have Also Xp On My Pc.


Im Sorry Abou The Thread But I Did`Nt  Know Where To Post It,:Confused: Im A Newbie

And I Need Anwser Queickly.

---

### Post by thumper on 2005-10-13
Did you tell the installer to put GRUB in the master boot record?

---

### Post by haskan on 2005-10-13
yes, i did after rebooting it comes up: hardisk or partition not activ

please help me!!:D

---

### Post by cbudden on 2005-10-13
Does it give a error message or is it just bios - Harddisk or partition not active.  Is there any other text?

---

### Post by haskan on 2005-10-13
yes, just that text: hardisk or partition not active press h to boot from hardisk 


just that

i need help please

---

### Post by GeneralZod on 2005-10-13
When you partitioned the drive, did you make the "/"-partition bootable? I *think* not doing this would cause this issue (as it happened to me :)) but I'm not 100% sure that it would affect dual-boots such as yours.

Also, please don't type in ALL-CAPS as it makes my ears ache :)

---

### Post by metoo on 2005-10-13
So out of curiosity, what happens if you hit h as suggested by the system?

A harddisk usually needs at least 1 bootable partition. If you have /boot in a separate partition, make this bootable. Otherwise the one assigned to '/' as suggested before (/boot and grub will then be there).

If it's too late now, try getting a live-cd somewhere or a knoppix cd. Use cfdisk in a shell with something like 'cfdisk /dev/sda' (for the 1st S-ATA harddisk) or cfdisk /dev/hda (for the 1st P-ATA).

Be careful here, cfdisk is a partitioning tool and you can loose all the data if you use it wrong.

So only select the partition you want to make bootable, make it bootable with the option at the bottom of the screen and then select write. If you haven't resized or deleted anything within cfdisk this may work... (crossing fingers. :-) )
If you punched the wrong button, just exit without write. Should not do any harm then.

---

