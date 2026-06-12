---
title: "Failure to install-check CDROM integrity?"
date: 2005-12-02
forum: Installation &amp; Upgrades
---

### Post by pablob on 2005-12-02
I begin a dual-boot install. It begins to open packages and fails around 7?% with some file given. Asks me if I want to retry and I do to no avail. I continue to exit screen and abort installation. Any ideas on what I am doing wrong?

I have tried this with 3 different copies of Ubuntu 5.10 on RW CD's. I have also tried the mailed install CD from Hoary. Both have the same problem but at different % of opening packages. My conclusion from this is that probably the check sum is ok since all versions fail, and at one time I had Hoary on my Dell Inspiron 8000 laptop with dual boot and no problem.

Specs: I have an Intel P4 2.6Ghz, 2 small ATA drives with Win2000 (for games), and Seagate SATA 160GB empty drive where I want to put Ubuntu as primary OS. I have an MSI motherboard with one GB RAM and would like to use Intel 536EP 56K modem. I have used fdisk /mbr each time between installs to make sure there is nothing carrying over. Win2000 does not recognize SATA drive because I used another linux to delete all partitions in the hope that Ubuntu would give me an opportunity to format and setup the whole SATA drive. 

So, what am I missing? I am new, really want Linux, and am not afraid of mildly techy response. Okay? Thanks a bunch.

---

### Post by mlomker on 2005-12-03
My generic troubleshooting advice is to unplug anything that you don't need for the install to work--USB devices, internal cards, hard disks, etc.  If it works with a stripped setup then you'll know that the problem was something that you unplugged.

I assume that you used the same CD-Rom drive to install Windows and it worked fine?  You used Knoppix or some liveCD to boot and things worked okay?

---

### Post by bwog on 2005-12-03
One user reported problems with CDRW. Try a normal CD and verify it.

If that doesnt help post your hardware specs, motherboard DVDwriter, etc.


"I have used fdisk /mbr each time between installs to make sure there is nothing carrying over. Win2000 does not recognize SATA drive because I used another linux to delete all partitions in the hope that Ubuntu would give me an opportunity to format and setup the whole SATA drive."

That isnt necessary ( windows wont understand ext3 partitions anyway, you did use ext3 didnt you?).

---

### Post by grus on 2005-12-03
I had the same problem with a dell machine, and solved it by enabling DMA on the cdrom. Use expert mode and enter -dm1 as parameter to the cdrom module.

Good luck.

---

### Post by vampire_janus on 2005-12-03
[QUOTE=mlomker]My generic troubleshooting advice is to unplug anything that you don't need for the install to work--USB devices, internal cards, hard disks, etc.  If it works with a stripped setup then you'll know that the problem was something that you unplugged.

I assume that you used the same CD-Rom drive to install Windows and it worked fine?  You used Knoppix or some liveCD to boot and things worked okay?[/QUOTE]

i wonder if you read the original post? the installation didn't bug down on hardware configuration...

---

### Post by vampire_janus on 2005-12-03
[QUOTE=pablob]
I have tried this with 3 different copies of Ubuntu 5.10 on RW CD's. I have also tried the mailed install CD from Hoary. Both have the same problem but at different % of opening packages. My conclusion from this is that probably the check sum is ok since all versions fail, and at one time I had Hoary on my Dell Inspiron 8000 laptop with dual boot and no problem.
[/QUOTE]

i think something's wrong with breezy cdroms as a lot of people are complaining about it. i have actually downloaded the isos thrice already. checked the md5 everytime, burned it and never succeeds installing it. i am also at that part of the installation whenever it complains that some packages cannot be installed. i am now doing an alternative installation- ie install from iso as it would give me the option to force some things. i would be able to continue even if some packages don't install at all.

---

### Post by bwog on 2005-12-04
@vampire janus: it is often hard to see what causes a faulty installation, or what exactly causes that the CDs do not seem to be working.

Keep in mind that only the users that have problems come in this section of the forum.

---

### Post by mlomker on 2005-12-04
[QUOTE=vampire_janus]i wonder if you read the original post? the installation didn't bug down on hardware configuration...[/QUOTE]

There are many hardware conflicts (including heat issues) that won't show themselves until the machine is working harder than usual.  

I've been working in server hardware support for 14 years, including a stint working for Compaq.

---

