---
title: "Install Ubuntu Using Smart Boot Manager"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by Imoen_tw on 2007-12-09
I have smart boot manager, which I am able to boot from. What I'm not figuring out is how to use it to complete the install. I have ubuntu 7.10 alternative on CD. I select the cd drive in sbm and it goes to the cd. I select to install ubuntu and it loads the kernal and the thing after that, then when the computer restarts if I use the sbm I get to the same install screen, if I don't I get to the grub loader with error 21. I had ubuntu installed but it was done on a different computer in an attempt to get around the bios' lack or botting from cd support, so it told me the cpu was too old for the kernal. I don't have any clue how to just delete the old install and start over. Can someone please help me and explain to me so I understand???

---

### Post by logos34 on 2007-12-09
> **Imoen_tw said:**
> I select to install ubuntu and it loads the kernal and the thing after that, then when the computer restarts if I use the sbm I get to the same install screen, if I don't I get to the grub loader with error 21.

So it won't even let you begin the installation, just restarts?

post your system specs or take a look at this:
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
[http://www.ubuntu.com/getubuntu/releasenotes/710](http://www.ubuntu.com/getubuntu/releasenotes/710)

error 21:
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

---

### Post by Imoen_tw on 2007-12-09
The Computer Specs
Model is a Compaq 7478 with the following specs:
• 533 MHz AMD K-6(r)
• 97 MHz system bus
• 384 MB 100 MHz SyncDRAM - 8 MB dedicated for video memory
• 30.0 GB 1 UltraDMA hard drive
• DVD-ROM Drive1
• CD-RW Drive2
• 512KB L2 Pipeline Burst Cache
• Trident Graphics Integrated in the ViaChipset.
• ESS Allegro PCI Audio

I had a problem earlier that I let ubuntu use the whole drive, which deleted the part the bios uses to identify the drive on Compaq computers. I fixed that and re-installed ubuntu selecting to use only the free space, but I did the install with this hard drive in a different computer because this one does not give an option to boot from the CD, so now it installed the kernal that the other computer's processor would use. I have been working on this for 3 days now, all I want is a solution to get this computer working and I have never had a more frustrating experience in my life. I don't know why it gives error 21, the hard drive shows up in the bios and is recognized, but it's also saying that off of the install that was done on the other computer so I would guess that the install needs to be removed, which is why I asked how to remove it.

---

### Post by logos34 on 2007-12-09
the earlier installation/kernel is not the problem, you're running from the install cd not the system on the disk (it isn't even mounted)...can't you get to the 'partition' stage of the install (it's right after language choice and hardware detect)? If so you can delete the earlier ubuntu install and set up the new root on that partition...It will overwrite the grub on the mbr with a new one too.  

If it won't let you get to that stage and just reboots then maybe it's having some problem with your hardware, although technically you have enough MHz and ram to run the live cd if you wanted.

---

### Post by Imoen_tw on 2007-12-09
I can't get to anything on the disk because the computer doesn't have the option to boot from CD in the BIOS and Smart Boot Manager will let me get to the cd to select install but then after it loads the kernals and restarts the cd isn't running anymore to continue.

---

### Post by logos34 on 2007-12-10
ok, I understand now (I think). 

My only suggestion at this point is to download [Xubuntu desktop/install CD]("http://www.xubuntu.org/get").  It'll run much better on an older pc like yours.  If you can boot into the live session and everything works, then hopefully it will allow you to install without a problem.

---

