---
title: "dual booting, GRUB error 17"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by brandn on 2008-01-24
I'm trying to dual boot windows xp and ubuntu.  I installed ubuntu without a problem but now when I turn on my computer I get GRUB error 17 during 1.5.  The only way for me to get past this screen is with a GRUB boot disk, and I can only boot to my windows partition.  Any help will be appreciated, I've been trying to fix this for like 3 days and I'm about to give up on ubuntu.

---

### Post by zvacet on 2008-01-24
Look [this](http://users.bigpond.net.au/hermanzone/p15.htm#When_trying_to_boot_Linux) and don´t give up.Stay with Ubuntu!

---

### Post by brandn on 2008-01-24
okay i tried supergrub...all i get is more errors.
when i try to boot in linux i just get file not found, i've tried both the automatic methods and the methods where i specify the partition its on, and no luck.

---

### Post by confused57 on 2008-01-24
> **brandn said:**
> okay i tried supergrub...all i get is more errors.
when i try to boot in linux i just get file not found, i've tried both the automatic methods and the methods where i specify the partition its on, and no luck.
Boot up with your Ubuntu live cd, open a terminal(Applications---Accessories---Terminal), post the ouput of:
```
sudo fdisk -l
```
-l is a small "L"

Do you get the grub boot menu and error 17, when you try booting Ubuntu or do you get error 17 and no grub boot menu?

---

### Post by brandn on 2008-01-24
i get no menu, just the error.

heres what i get after running sudo fdisk -l :

Device        Boot    Start           End          Blocks              Id       System
/dev/sda1 *                 1          12748      102398278+     7       HPFS/NTFS
/dev/sda2              12749        25784      104711670        f       W95 Ext'd  (LBA)
/dev/sda3               25785       36483       85939717+     83      Linux
/dev/sda5              12749        25497      102406311        7       HPFS/NTFS
/dev/sda6              25498        25784         2305296        82      Linux swap / Solaris

sorry its not formatted, i had to type it out because the computer with the issue has no internet and for some reason when i post it deletes the spaces

---

### Post by confused57 on 2008-01-24
Try some of the suggestions in this thread, from the link that zvacet gave you:
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

Also, you should be able to restore your Windows IPL to the mbr, using Super Grub Disk...I think the option is "Fix Boot of Windows".
Other methods to restore your Windows boot:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

How old is the computer?  Your problem may actually be grub error 18, in spite of error 17 being reported:
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)
This may or may not be the case, but a possiblity.

---

### Post by brandn on 2008-01-24
im pretty sure the problem isnt the error 18 thing, this computer is only five years old.

i've looked through that thread, and the problem isnt caused by an error in the menu.lst file, because when i try to boot in GRUB command line, bypassing menu.lst and specifying the partition ubuntu is installed on, it still can't mount the partition.

also, when i do geometry(hd0) in GRUB it lists all of my partitions, including the ext3 partition, as unknown type.  could the fact that its not recognizing the partition as ext3 be the reason that its not able to mount?

---

### Post by confused57 on 2008-01-24
> **brandn said:**
> im pretty sure the problem isnt the error 18 thing, this computer is only five years old.

i've looked through that thread, and the problem isnt caused by an error in the menu.lst file, because when i try to boot in GRUB command line, bypassing menu.lst and specifying the partition ubuntu is installed on, it still can't mount the partition.

also, when i do geometry(hd0) in GRUB it lists all of my partitions, including the ext3 partition, as unknown type.  could the fact that its not recognizing the partition as ext3 be the reason that its not able to mount?
Depending on how much effort you want to put into resolving your problem, you could try updating your bios, if there is an updated bios for your pc.

Another possiblity to rule out grub error 18 would be to resize your sda1 by 10 Gb or so...install Ubuntu to the freed space(this should put Ubuntu within 137 Gb limit, if error 18 is the problem).  If Ubuntu boots, then you could reinstall using this partition for root and sda3 as /home.  If you try this, make sure to defrag your Windows partition(maybe a couple of times), before resizing.

If none of the suggestions in the thread by American Yellow work, exploring grub error 18 is the only thing I know to try...or try reinstalling Ubuntu again on your current partitions.

---

### Post by chrisclark16 on 2008-01-24
hey brandn  i do not know to much about liunx but i know about the GRUB error 17 that hp to a lote of time what you need to do is to  install ubuntu first and install  windows xp in v boxs and that why you well be ab to run windows insid of ubuntu.................................................................................. 






                                                     p.s how much ram and hd do you have 
                          you can email me at [email]freepchelp16@yahoo.com[/email] and you can im me on yahoo 
                                                               and have a good day :)

---

### Post by brandn on 2008-01-24
> **confused57 said:**
> 
Another possiblity to rule out grub error 18 would be to resize your sda1 by 10 Gb or so...install Ubuntu to the freed space(this should put Ubuntu within 137 Gb limit, if error 18 is the problem).  If Ubuntu boots, then you could reinstall using this partition for root and sda3 as /home.  If you try this, make sure to defrag your Windows partition(maybe a couple of times), before resizing.


ubuntu is installed on an 80 gig partition, so doesn't that rule out error 18? sorry if i'm misunderstanding something

---

### Post by confused57 on 2008-01-24
> **brandn said:**
> ubuntu is installed on an 80 gig partition, so doesn't that rule out error 18? sorry if i'm misunderstanding something
The size of the partition doesn't matter, it's the location of the partition on your hard drive.  If I'm reading your fdisk correctly your 80 Gb partition is located after your sda1,sda5, & sda6, which would place it approx. 200 Gb on your hd(past the 137 Gb limit, if indeed this is the problem or not).

---

### Post by brandn on 2008-01-24
right, thanks for clearing that up. i was confused, heh. once i make the 10gb partition, how do i get the ubuntu installer to use one partition for root and one for home?

---

### Post by confused57 on 2008-01-25
> **brandn said:**
> right, thanks for clearing that up. i was confused, heh. once i make the 10gb partition, how do i get the ubuntu installer to use one partition for root and one for home?
Here's an excellent guide for setting up partitions with the Desktop cd:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

You would need to select "Manual Partitioning"...then you should be able to select the 10 Gb, format as ext3, select primary partition, there should be a drop-down menu that you can select the mountpoint(/) not (/root).
Then click on your 85 Gb partition, format as ext3, logical(or extended) partition, mountpoint /home.

Swap is mountpoint swap, logical partition.

I always use the alternate install cd, just my preference, so I can't really give you specific advice on installing with the Desktop live cd; but the above should be a representative guideline.  Maybe someone else can give you more specific instructions, using the Desktop cd.

If grub error 18 isn't your problem, you might still not be able to boot Ubuntu...so if it's worth your time & effort, you can try what I've suggested or wait to see if anyone else has a better suggestion.

---

### Post by brandn on 2008-01-25
im gonna try it out, hopefully it works.
even if it doesnt thanks a bunch for your help, i appreciate it.

---

### Post by deltaprime on 2008-01-25
if you have a windows xp cd you can put it into your drive and boot it, then you go and find load cmd or command prompt or something like that. anyhow you should get a black screen saying A:\ or C:\ . Once you have that you just type **fixmbr**. that will fix you master boot record
then reboot jour computer and see if it worked.
Another option is to get super grub onto a usb stick or a cd, boot it and fix your master boot record.
hope it helps - tell me if it doesn't
[U]
DELTA[/U]

---

### Post by confused57 on 2008-01-25
> **brandn said:**
> im gonna try it out, hopefully it works.
even if it doesnt thanks a bunch for your help, i appreciate it.
Good luck & hope it works.  I should have mentioned you could resize your Windows partition with Gnome Partition Editor on the Desktop cd(System---Administration---Gnome Partition Editor):
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Windows will prompt you to run a chkdsk at boot, since you resized the partition.

---

### Post by brandn on 2008-01-25
it worked! i also decided to install kubuntu instead.  i'm not sure if that contributed to it working, but everything is working now so i don't really care.

---

### Post by confused57 on 2008-01-25
> **brandn said:**
> it worked! i also decided to install kubuntu instead.  i'm not sure if that contributed to it working, but everything is working now so i don't really care.
Well done...I was afraid to check if you got it working or not, glad you did.  I don't think installing Kubuntu, instead of Ubuntu would make any difference...Kubuntu is essentially the same as Ubuntu, except it uses KDE, instead of Gnome desktop.

---

### Post by deltaprime on 2008-01-25
thats good
 
 
DELTA

---

