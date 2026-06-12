---
title: "sata HDD woes with feisty"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by lxme on 2007-04-28
Hello Ubuntu Friends !

Ok, so I decided recently to dump my edgy and to replace it with a brand new Feisty.
I did a clean install but had to disable Sata in bios because both live and alternate CD wouldn't properly boot with it enable. (I did the installation on my primary PATA disk)

now, beside a few minor glitches, my feisty is working very nicely. 
but I'd like to enable SATA so I can use my secondary disk

Alas, even with SATA enable in bios, feisty seems to have problems with my disk, which is strange cause Edgy had NO problems with it!! (same hardware, same bios settings)

here is the result of a dmesg | grep ata1


dm@Merle:~$ dmesg | grep ata1
[    6.996000] ata1: SATA max UDMA/133 cmd 0x0001e800 ctl 0x0001e482 bmdma 0x0001e000 irq 20
[    7.520000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   37.528000] ata1.00: qc timeout (cmd 0x27)
[   37.528000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 0
[   37.528000] ata1.00: ATA-6: ST3200822A, 3.01, max UDMA/100
[   37.528000] ata1.00: 390721968 sectors, multi 16: LBA48 
[   37.528000] ata1.00: applying bridge limits
[   37.528000] ata1.00: failed to set xfermode (err_mask=0x40)
[   37.528000] ata1: failed to recover some devices, retrying in 5 secs
[   43.164000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   43.332000] ata1.00: revalidation failed (errno=-2)
[   43.332000] ata1: failed to recover some devices, retrying in 5 secs
[   48.968000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   49.136000] ata1.00: revalidation failed (errno=-2)
[   49.136000] ata1.00: disabled


there's something funny here.. is feisty having compatibilities problems with my hardware ? did I forgot something in Feisty's configuration ? 
for now it seems like a regression over Edgy, so I hope I just forgot something somewhere.
any help on that matter ?

my rig:

AMD X2 3800
2 GB DDR
Asus A8n-vm CSM
Primary HD seagate 200GB PATA
Secondary HD seagate 200GB PATA (with PATA to SATA adapter)

---

### Post by bulldog on 2007-04-28
I see you use some form of adapter to connect the Sata hdd,is it a PCI card?
I had a similar device in another computer,and it needed drivers to see the PCI Sata connector,before it could be used.
Even windows didn't see the Sata hdd till I installed the driver.

---

### Post by lxme on 2007-04-28
Hi Bulldog, 

The adapter is a basic converter, it doesn't need any kind of drivers, firmware or software to work.
[http://www.maplin.co.uk/Module.aspx?ModuleNo=36036&TabID=1&C=SO&U=strat15&doy=search]("http://www.maplin.co.uk/Module.aspx?ModuleNo=36036&TabID=1&C=SO&U=strat15&doy=search")

In my Edgy days, I just plugged it and my IDE drive was seen as sda without further tweaking :)

---

### Post by newguy1950 on 2007-05-02
I am having a very similiar problem on feisty, I get the same error messages (**qc timeout cmd 0x27, err mask 0x40**) when booting. However, since I have only SATA drives, I cannot boot and copy and paste.

My system *sometimes* boots, sometimes doesn't. A cold reset (killing the power) is usually the only thing that allows me to boot.

Here are a few things of note:

a.) The problem, so far, seems to be rather random - I **cannot reproduce** it reliably.
b.) **Killing the power** seems to work in most cases - however, I have seen it occur right after starting the system in the morning, after it had been off for hours.
c.) EDIT: irrelevant (CD/no CD in drive)
d.) This happens with kernel **2.6.20-15-generic**. Before that, I used **edgy** and **2.6.17-11-generic** with no problems. However, since the upgrade to feisty, 2.6.17-11-generic also has had this problem sometimes.

If anyone can comment on having a similiar problem, please do so.

Here are some other threads with similiar issues I have found:

_[http://ubuntuforums.org/showthread.php?t=385601](http://ubuntuforums.org/showthread.php?t=385601)_
(links to launchpad bug _[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/91940](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/91940)_ - supposed to be fixed in -13, could be a completely different issue or a regression in -15).
_[http://ubuntuforums.org/showthread.php?t=414141](http://ubuntuforums.org/showthread.php?t=414141)_ - especially the third posting

---

### Post by PietM on 2007-11-24
I had the same problem with my SATA drive using 7.10 Gutsy Gibbon. Adding "irqpoll" to the first boot option in grub (/boot/grub/menu.lst) solved the problem, although I don't really understand why.

---

### Post by fudo81 on 2008-05-07
I've experienced a very similar random behaviour at boot using gutsy, and now with Hardy things just got worse: boot fails almost every time. Any help?

---

### Post by fudo81 on 2008-05-10
I solved the problem by adding an "all_generic_ide" string to the kernel line of GRUB. Hope it works for you too!

---

### Post by master_b on 2008-05-14
I'm having the same trouble with Kubuntu HARDY fnal hd install.

When I installed my HD setup was:-

Primary Master - IDE partions 1( hardy),2( /home) and 4 (empty) ext3, partition 3 being swap.

Primary Slave - IDE - partitions 1,2 and 3 being ext 3 - data only

Secondary Master - IDE - DVD-RW

Secondary Slave - IDE - data - 1 ext3 partition

All seen as /sdax and work OK.

I then attached my 2 SATA hds. System boot fails trying o find /home partition.


PROBLEM

SATA hds become /sda1 and /sda2, and all IDE hds, prevously /sdx become 
/hdx and therefore /home, whch was on /sda2 is now on /hda2 and can be found.

In addition, the System places the SATA hds above the IDE hds in priority ( ie in /system Settings/Disk and Filesystems, the SATA hds are listed before the IDE hds.

Had no problems under earlier versions of Kubuntu.

DONT wan to change boot reference to /home ( ie from /sda2 to /hda2) as if I remove the SATA hds for any reason, the system will then again fail to boot as it will cease looking for /hda2 and be once again looking for 
/sda2

By the way, the PC bios is set to boot from the 1st IDE hd.

Any way to fix this?

---

