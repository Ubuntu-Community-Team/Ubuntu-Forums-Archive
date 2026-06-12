---
title: "Instalation fails and stops at $: prompt"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by rednax0 on 2008-06-11
Hi there,

I tried installing Ubuntu desktop 8.04 from a cd made from the ISO file. Boots ok.
When running the install I have to wait a long time watching the ubuntu startup screen and after that it goes back to text mode and just stops at a $: command prompt. Just before the command prompt was some warning text that i could not read because it flashed by so fast.

I have the following hardware (yes it is an old clunker):
Main board: Asus I440 BX-P2B-Ds
CPU: Dual Pentium III 450
Video: S3 Trio 3D
RAM: 780 Mb (or something like that)
Harddisk: Seagate 3120023A 120Gig
NIC: 3com 100Mbit ethernet card
And some telephone modem card.

Harddisk is connected as primary master, LBA mode. On the harddisk are 2 NTFS partitions using all the space on the harddrive WinXP is installed on the first partition. But i want to delete those and install ubuntu. I thought there would be a way to delete the partitions and make a new one in the setup of Ubuntu. But i didn't get tat far :(

Can someone please give some help how to install this.

---

### Post by avtolle on 2008-06-11
Well, I'd suggest downloading the alternative cd iso and burn it to disk and install through that. I've found the alternate cd works better on older hardware than does the Live (Desktop) cd. If I've misunderstood that you were using the Live CD, please correct me.

---

### Post by wpshooter on 2008-06-11
First may I ask you how this computer is going to be connected to the Internet ?  Do you have high speed service provider ?

---

### Post by rednax0 on 2008-06-11
> **avtolle said:**
> Well, I'd suggest downloading the alternative cd iso and burn it to disk and install through that. I've found the alternate cd works better on older hardware than does the Live (Desktop) cd. If I've misunderstood that you were using the Live CD, please correct me.

I'll download ubuntu 8.04 alternative and give that a try.
Thanx

---

### Post by rednax0 on 2008-06-11
> **wpshooter said:**
> First may I ask you how this computer is going to be connected to the Internet ?  Do you have high speed service provider ?

At the moment it is not connected to the internet, but i think that shouldn't matter in this case.
But yes later when it is installed (i hope) it will be connected to broadband internet.

---

### Post by rednax0 on 2008-06-12
> **rednax0 said:**
> I'll download ubuntu 8.04 alternative and give that a try.Thanx

**[SIZE="4"]This solved my problem! \\:D/ Thanx everyone.[/SIZE]**

I had some problems with my network, took me hours to realize that it was because of a crappy patch cable. It did let me ping the router and 212.83.192.1 (internet address), but i could not get a good connection.
But I am now happily internetting on my Ubuntu.

And i had a bit of a fight getting screen resoluton to 1024x768 at first it didn't want to go higher than 800x600. I did set it up during setup and tested ti there on 1024x768. But it only really worked after setting it in 
System->Preferences->Screen resolution.

Greetings Xander.

---

