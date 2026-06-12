---
title: "Dual boot XP and 6.10 to a single SATA drive"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by chrisblue on 2007-02-18
Hi,

Been trying to install Edgy as a dual boot with XP SP1 on a single 160GB SATA drive.

Wiped out the XP install twice now and getting gun shy.

So figured it was time to ask some questions rather than just reading others posts and how tos.

As a result of a hard drive crash I have installed a new 160gb sata drive to hold both XP and Edgy. 

For the last two Edgy installs I have not fully partitioned this drive but just left half of it as free space and only partitioned around 75mb for the windows dir (bit excessive I know since my data is mostly on the mirrored drives.

I have been installing from the desktop icon on the 6.10 AMD live CD and have noticed that the it wants to install the grub loader to hd0 when I don't have any PATA drives installed.

The ubuntu partitions seem to be being installed correctly however the grub is corrupting the MBR on the windows partition as after the install I can't start either OS.

Is there a "how to" that I should read in order to install both OSs on one sata drive, I can find a few for separate pata or sata drives but nothing that deals in detail and specifically with one sata.

FIXMBR and FIXBOOT have not helped resurrect the windows install and I have had to reinstall it twice now.

I have attached the current drive arrangement (as per the thumbnail) so if anyone has any pertinent advice I would appreciate it.

Cheers.

---

### Post by Herman on 2007-02-18
```
I have been installing from the desktop icon on the 6.10 AMD live CD
 and have noticed that the it wants to install the grub loader to hd0 
when I don't have any PATA drives installed.
``` That's nothing to worry about, Grub makes no distinction between IDE and SCSI (including SATA) drives in its numbering scheme. :)
[LEFT] > The ubuntu partitions seem to be being installed correctly however the grub is corrupting the MBR on the windows partition as after the install I can't start either OS.Hello, the MBR is not part of the Windows filesystem and it isn't even inside the Windows partition.
[/LEFT]
 The MBR doesn't belong to Windows. I have computers here that have no Windows installed at all and never have and never will. They all still have a MBR in their hard disks. :) The MBR belongs to the person who owns the computer.
 What exactly do you mean when you say you 'can't start either OS'? Are you getting any error messages? I'll bet your MBR is fine. > FIXMBR and FIXBOOT have not helped resurrect the windows install and I have had to reinstall it twice now. Normally those overwrite the bootloader section of the MBR and Windows bootsector respectively, I don't know why they won't work for you. :confused:

What disk partitioner are you using?
 
I think you are panicking way too much and over reacting. Re-installing is not necessary at all. Probably everything is working okay and you just need to learn how to solve your boot problems. I can probably help you but I will need to know exactly what error messages you get  or what happens (what you see) when you try to boot up.

---

### Post by chrisblue on 2007-02-18
Thanks for the reply Herman,

I will give it another go tomorrow and let you know what messages I get step by step.

I partitioned the disk using the XP utility.

Cheers

Chris

---

### Post by waverider on 2007-02-18
Talking of which, I've been trying to do the same thing, except using Acronis Disk Director Suite for my partitioning. Of my 110GB SATA HDD I have about 70 for Windoze and 35 for Ubuntu, and the rest is other stuff. My problem is that the Ubuntu partitioner (during installation) won't recognise my HDD. My contact believes it is due to the HDD being SATA, though I have my doubts. Is there something I'm doing wrong?

Waverider

---

### Post by bulldog on 2007-02-18
> **waverider said:**
> Talking of which, I've been trying to do the same thing, except using Acronis Disk Director Suite for my partitioning. Of my 110GB SATA HDD I have about 70 for Windoze and 35 for Ubuntu, and the rest is other stuff. My problem is that the Ubuntu partitioner (during installation) won't recognise my HDD. My contact believes it is due to the HDD being SATA, though I have my doubts. Is there something I'm doing wrong?

Waverider

Sata isn't a problem for ubuntu,I myself have a IDE and a Sata disk and everything works fine.
The problem could be if you have the sata drive not connected directly to the motherboard,but connect it through a PCI card or something like that.
In that case it's possible ubuntu can't recognize your hdd because in most cases you need a driver for that PCI card.

You can try the use of the GParted live cd however,this is a live cd everyone should have in his posession.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
Boot this live cd and see if it recognize your sata disk.
Partition and format it the way you like and try again.

If you have more than one disk you have to make sure the disk you're booting from is the same as where GRUB is installed to.
Multiple hdd's makes it a little more difficult to sort out because what your BIOS is set to,is not always the way ubuntu names the hdd's.
You can find out with a simple command how your disks are ordered in ubuntu```
cat /boot/grub/device.map
```

---

### Post by willc0de4food on 2007-02-18
> **chrisblue said:**
> Thanks for the reply Herman,

I will give it another go tomorrow and let you know what messages I get step by step.

I partitioned the disk using the XP utility.

Cheers

Chris
with my install, for some reason the bootloader is crazy..
with anything i select it says something like partition not found..
i select the "windows xp" option and it proceeds to tell me something like
boot disk error
please insert a system disk and try again
something to that effect..i press enter twice to get rid of those messages and it brings me back to the ubuntu bootloader. i am now able to boot to either ubuntu or windows.
i'm not sure why on earth i have to go through this process but maybe yours will be the same way..?

---

### Post by waverider on 2007-02-19
> **bulldog said:**
> The problem could be if you have the sata drive not connected directly to the motherboard,but connect it through a PCI card or something like that.
In that case it's possible ubuntu can't recognize your hdd because in most cases you need a driver for that PCI card.

Where can I get a driver? In fact, where do I find out what kind of PCI (if at all) card I have? It's a brand new laptop and I'm reluctant to open it up. I'm still running Windoze XP.

> **bulldog said:**
> You can try the use of the GParted live cd however,this is a live cd everyone should have in his posession.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
Boot this live cd and see if it recognize your sata disk.
Partition and format it the way you like and try again.

That's the partitioner I tried using before. I tried, after unsuccessfully installing, to use GParted from the Ubuntu Live CD.

And it's a single HDD.

---

