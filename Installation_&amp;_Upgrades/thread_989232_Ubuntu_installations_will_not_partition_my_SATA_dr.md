---
title: "Ubuntu installations will not partition my SATA drives."
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by Brian Woodhouse on 2008-11-21
I have upgraded my hardware and find that, Ubuntu 8.04, Ubuntu 7.04, and Linux Mint all stop at step 4 "prepare partitions" stage of the install. There is no problem installing Suse 11, and Fendora 9 both will partition my SATA drives. In desperation I put a 40G PATA Maxtor drive back on the system and Ubuntu would partition and install ok on it.

Hardware is: MSI P43neo motherboard, Intel Core 2 duo E7300, Ge force NVIDIA 8500GT graphics card, hd1 Maxtor 160G SATA, hdb Hitachi 250G Sata, and the ATA parallel drive that was reintroduced is a Maxtor 40G. The system has 2G of Corsair memory.

Can anyone help I want to use Ubuntu on a SATA system.

---

### Post by Pumalite on 2008-11-21
Does BIOS see your hard drives and "how" does it see them. Maybe you need certain changes in the BIOS setup.

---

### Post by Brian Woodhouse on 2008-11-21
Thanks for the quick reply where you asked about the BIOS. The bios does record all the drives correctly. It is just the Ubuntu systems that will not see the SATA drives.

---

### Post by caljohnsmith on 2008-11-21
Are you saying that the Ubuntu installer doesn't see any of the partitions on the HDD, or that when you try and set up partitions, it stops? Does it hang or does it give an error? 

How about opening a terminal (Applications > Accessories > Terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for whichever is the SATA drive you want to install to, also please post:
```
sudo parted /dev/sdX print
```
And replace sdX with the drive. That will help clarify your setup.

---

### Post by Brian Woodhouse on 2008-12-05
I still cannot install Ubuntu. I have tried Ubuntu 8.04, Ubuntu 7.04, Ubuntu 6.06, Linux Mint 4.0, Lindows 4.5, every Debian based system fails at the partition discs stage. I can easily install Mandriva 2009, which works well on my system. My BIOS recognises all my hard drives, Partition Magic under Windows 2000 will partition all the hard drives, so the hardware must be ok. Ubuntu based systems do not seem to see the drives.
Hardware: MSI P43 neo Mobo, Intel Core 2 duo E7300 processor, 2GB Corsair memory, 250G Hitachi HP72502 SATA, 160G Maxtor STM316081 SATA, and a Maxtor 6E040LO 38g ata. Media is a Samsung RW SATA DVD.
  What is wrong I cannot change all the hardware.

---

### Post by zvacet on 2008-12-05
I can be totaly wrong,but did you try in bios see is AHCI or IDE mode?See whitch one will work for you.

---

### Post by Brian Woodhouse on 2008-12-10
I did try IDE and all other setting associated with the drives the problem still persists. In desperation I have installed Mandriva 2009 instead of Ubuntu.

---

### Post by pmq on 2008-12-10
I am having the exact same problem.

My Spec: Seagate 250GB, samsung 1TB, both NTFS & SATA. intel quad core 6600, 8800 GTXXX nvidia.

when i get to the partition page none of my hdd's are visible. I have vista installed in the TB HDD along with all my progs and docs, the other hdd is music and movies etc.
I did a shrink on the big drive to allocate 50gb to linux. This space has not been formatted.

Both the hdd's are visible to the bios settings.

there was one good thing, when i had an external 750gb hdd attached via USB, this was visible and is in NTFS format.

any ideas i can work at?

I was thinking maybe disconnecting one of the sata drives, i suspect they may be conflicting with each other when it comes to ubuntu. I will try this when i get home from work today.

Like the original poster, i am able to install mandriva 2008, but i want ubuntu.

pmq

---

### Post by Daillew on 2008-12-10
Hi Brian & pmq, This may be of some help to you. I've just setup my new PC in the last couple of weeks and I also experienced the problem of Ubuntu not seeing my drives. I found it very frustrating after fitting three 250 GB SATA hard drives on the system. This is what worked for me, give it a try.

[LIST]
[*]My drives are set to **AHCI** in the systems BIOS.
[*]Boot with your Ubuntu LiveCD, choose your language.
[*]Press **F6** to change the boot options and append this to the end of the command line: **pci=nomsi**
[/LIST]
 
Ubuntu now recognised my drives and I could just partition them as normal. After the installation of Ubuntu and restarting my machine everything works perfectly OK. My system has been up for a couple of weeks now, I've had no problems and my drives are performing great. David.

---

### Post by dootzky on 2008-12-10
solution that worked for me, a quick fix, really:

- go to BIOS, and enable AHCI mode. (it was disabled by default)

and everything works normaly. 
now I see all hard drives and partitions, and I'm installing already :)

thanks to all and specially Daillew, good tips!!

cheers!! ):P

---

### Post by pmq on 2008-12-20
Hi,

Just dropped by to say thanks for the info. I now have my distro up and running. 

Just a side note, once ubuntu was installed, vista wouldnt boot up at all, i would get the windows loading bar then a blue screen. This happened a few times and i couldnt get to the desktop... The solution to this was to set the sata drives back from AHCI to IDE again and this worked :) just to let you know

Cheers 

pmq

---

### Post by Brian Woodhouse on 2008-12-20
Problem solved. I have just obtained an Ubuntu 8.10 DVD, it installes without any problems, so it seems that earlier releases just could not see my system discs. 
Many tanks to all the members who tried to help me. Ubuntu 8.10 is very professional and it has a great disk partition manager.

---

### Post by Daillew on 2008-12-21
Hi pmq, happy your up and running with Ubuntu. Your problem booting Vista was probably caused because Vista needs a SATA driver. My motherboard is an ASRock ALiveNF5-eSATA2+R3.0, the manufacturer CD that came with it has SATA drivers on it for Vista. To install Vista onto the drive with AHCI enabled i had to load the SATA drivers during installation. When the Vista installer asks you to choose where you want to install it, select Load Driver, eject the Vista disk and pop in the motherboard one, browse to the appropriate folder and select the driver, load the driver, pop the Vista disk back into the drive and carry on with the installation. This is what worked for me, it may not for you. It could be worth having a look at your motherboard cd or motherboard manufacturers website for drivers. David

---

### Post by Brian Woodhouse on 2008-12-22
The problem for me is solved. I found that Ubuntu 8.10 sees the SATA drives and installs without any trouble.

I will stay with the 8.10 version it seems very polished and good.

---

