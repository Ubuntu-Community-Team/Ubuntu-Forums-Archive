---
title: "Grub error 18 not good :("
date: 2005-06-21
forum: Installation &amp; Upgrades
---

### Post by Skel on 2005-06-21
Alrigth well my ipod broke so i had to go into windows and try and do a updater... 

norton and all this stuff  must have saw linux as a error or cuoppt disk and tried to fix it.. Now i can not do anything... I have no boot load... I cant install a new OS... i have no recovery floppy.... If anyone can help it would be greatly appreciated :?:

---

### Post by The Na Kun on 2005-06-21
[QUOTE=Skel]Alrigth well my ipod broke so i had to go into windows and try and do a updater... 

norton and all this stuff  must have saw linux as a error or cuoppt disk and tried to fix it.. Now i can not do anything... I have no boot load... I cant install a new OS... i have no recovery floppy.... If anyone can help it would be greatly appreciated :?:[/QUOTE]

You can't install a new os?  Well, I had this error after I killed off all of my files, because.. I'm not sure, I just killed it off with my drivers disc for a fresh install.  What would happen when I would turn on the computer is it would just show an error and not do anything.  What I did was I threw in the windows cd, formatted all to NTFS (had to), then after setting up windows I added partition magic and made the linux and all is fine.  What I don't understand is how norton could even see linux.  I mean, they're not even on the same partition (well I hope not :P).  So just throw in the windows cd, restart and do as said.. If you want.  More information would be nice too.

---

### Post by Skel on 2005-06-21
I have 120 GB hardrive that has window and Mp3's and i have another 120 Gb hardrive that is half linux and half space.... When i stick my Cd in It will not let me boot it.. All it will say is "grub Error 18" then stay there... so i cant just reinstall ubuntu or windows i tried that...


Any idea what esle i could try to fix this.... My computer is a veggie at the moment  :???:


Norton Was the thign that messed up grub it detected it and thought it was some sort of error so it just F-ed it up everything was perfect i love Ubuntu.. I just wanna get Unbuntu on and never go abck on windows.. i cant stand it

---

### Post by mingus on 2005-06-21
If when you boot now you get a grub error, that means grub is in your MBR.   Grub error 18 occurs when the boot files on the disk are in a partition which is beyond what the BIOS can see, either because of a BIOS limitation or because of the 1024 cylinder limit.

Even so, you should be able to boot from a Windows install CD or W98/ME/DOS bootable floppy (if your system supports that) by changing the boot sequence in the BIOS.

If you provide more details about your hardware and its age, what version of Windows, the hard drives, the partitions, and what is installed on each partition, and if you are using a drive overlay or PCI controller, we may be able to give you a fix.

---

### Post by Skel on 2005-06-21
I have a Hp pavilivon 762C i have no chnaged anythign expect adding a maxtor 120 Gb slave Drive... I have windows Xp Cd, MY system is maybe 2 years old, 


Specs
512 Mb ram
2 -120 Harddrives 
Pentium 4 proccessor
2.26 Ghz



Ubuntu was install on the Slave hardrive as a parition... Windows was on the master drive...

And i not sure why i can reisntall my Os ether it just comes up with Drug Error 18 i expect it to at least let me reinstall my Os but i guess i was wrong...

---

### Post by Skel on 2005-06-22
:-#  :-#  :-#  ](*,) I cant even use my computer its just a pile of junk.. I cant do anyting cant install a new Os cant boot from a floppy... fuckig windows messed it up thinking grub was a error or soemthing :(

---

### Post by not_yet on 2005-06-22
not sure if this will help  :???: 

you should be able to boot from a floppy

if not you will have to go into the bios at the start of the boot and adjust the boot sequence

so boot from a windows boot disk,  then enter   fdisk/mbr

now you should be able to boot from the install cd

good luck

---

### Post by irusun on 2005-06-22
As Mingus suggested, booting from the CD or floppy is probably your only hope.  The CD/floppy will bypass the MBR, but you may need to change your BIOS settings.  Have you tried that?  Note that some of those "Windows" installation CDs that come with computers are very particular - do you have any other bootable CDs to try?

There are a lot of Linux rescue discs available for download that could probably help fix the MBR.  You're going to have to put some work into it - I don't think there's a magic button that's going to fix this problem.

Also... though it's probably unlikely, there's always the *possibility* that there's something wrong with the hardware and this little episode exposed it...

---

### Post by Skel on 2005-06-22
Thank you all for ur replays i got it working.. I got redhat installed then booted Ubuntu and I toasted all windows now i am 100% ubuntu linux woot thank you all very much \\:D/

---

