---
title: "xubuntu install problems"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by Wofl on 2006-12-01
hello

I'm installing xubuntu from the alternate cd on an old ibm iseries thinkpad 1200 laptop

it worked great, until it installs and the configures anthy

it now is stuck for hours at 65% telling em that it is "Configuring anthy"

is there anything i can do (maybe somehow leave out this package when installing)

Thanks a lot

---

### Post by aysiu on 2006-12-01
Sounds like a corrupt CD.

Did you do a checksum on it before you burnt the CD?

If you have no idea what I'm talking about, read this:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Wofl on 2006-12-01
i didnt do checksum, but its working now
i gave my pc another chance overnight, in the hope that it just need a little more than 3 hourt for that one thing, and true enough, this morning it actually got done

i never thought that it could be that slow

---

### Post by Herman on 2006-12-01
A good trick I learned recently for installing faster in a machine with less than say 256mb or so of RAM is to make a swap area first with a [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php")  or any other way you can.
Any other live  Linux CD, be it the  'Alternate' install CD or  'Desktop' or another kind of Live CD, will find that swap area and use it. It can make a remarkable difference to the speed of an install. Sometime soon I will run some test installs and record the time difference just so I will be able to quote some example figures.

It's too late now for Wofl, but it might help someone else. Anyway, congratulations Wofl, on a successful installation! :D

EDIT 1: I am not sure at what stage it 'configures anthy', if that is before disk partitioning then having a pre-made swap area might have helped, but if 'configuring anthy' comes later, (probably it does) then it wouldn't have made any difference.

Regards, Herman

EDIT 2: I did run some trial installations and recorded the times.
I used an old Acer  'AcerPower' for these tests, it has an Intel(R) Celeron(TM) CPU 1300MHz, an 80.0 GB hard disk, and 256mB of RAM. All these tests were done in the same computer setting up a dual boot with Windows XP Home Edition on the FAT32 filesystem. The XP partition was resized to take up the whole disk again after each install was deleted.

1) Time taken for an 'Alternate' Xubuntu install, 27 minutes.   This comprised of about five minutes for detecting hardware and partitioning the disk, followed by 21 minutes of installing the base system and selecting and installing software, and about 1 minute to install Grub and reboot.

2) An Edgy Eft 'Alternate' CD install took 41 minutes.  Detecting hardware and partitioning the disk took about the same amount of time as for Xubuntu, then 35 minutes was needed to install the base system and selecting and installing software. It took about 1 minute to install Grub and reboot.

3) A Ubuntu Dapper Drake Christian Edition, (Desktop Live/Install CD) with no pre-made swap area booted okay, but on beginning the install it took an hour an still did not succeed in opening the Window for step 1 of the install (select language). I gave up, I was too impatient to wait any longer.

I used a GParted LiveCD to create a 1.0 GB swap area and tried again.

4) Ubuntu Dapper Drake Christian Edition, (Desktop Live/Install CD) with 1.0 GB pre-made swap area took 8 minutes to detect hardware and partitioning the disk, 28 minutes 'Installing System', and 4 minutes to install Grub,  shut down and reboot. Total = 40 minutes.

Conclusions, 
(a) Xubuntu is a little quicker to install than Ubuntu, probably because it's smaller.
(b)  It probably makes no difference for the 'Alternate' CD install whether there is any pre-made swap area or not, because the 'disk partitioning stage comes pretty early in the installation anyway.
(c) We can still run a 'Desktop' install CD in a computer with only modest amount of RAM very well if we make a swap area somehow first. Otherwise, the 'Desktop' CD might not even be able to get started.
(d) With this amount of RAM, the 'Alternate' CD and the 'Desktop' CD are about equal for speed. With less RAM than this, the 'Alternate' CD would probably  start showing an  advantage.

---

### Post by Wofl on 2006-12-05
thats why i used the alternate

the discription said it can install on 64mb of ram, so i went for that...

and to anthy

i googled it and it poped up masses off japanese sites. it apparently enables me to type japanese characters and such stuff (cool, but not worth the time...)

---

