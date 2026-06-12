---
title: "Edgy can't find my Seagate Barracuda HDD"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by Wesslan on 2006-11-01
I'm trying to make a fresh install of Edgy on my Mini-ITX-server. Everything works fine until the "detect discs"-stage where the installation says that it can't find any drivers for my HDD which is a Seagate Barracuda ATA(IDE) 160Gb.
I've tried locating Linux drivers for it on their site but I can't find any.
The most annoying this is that I already have a Linux-installation on the HDD, namely Mandrake 10.1. If Mandrake 10.1, which is about 300 years old, can find my HDD, I'd expect Edgy to do it also. :)

Any thoughts?

Cheers,
Peter

---

### Post by Wesslan on 2006-11-14
Does anyone have a guess what driver I should use for this HDD?

Cheers

---

### Post by gerkin on 2006-11-14
I'm currently running 2 Seagate Barracuda HD's and have on every version of Ubuntu

They are both 80gB ATA, I recently installed a new one (in Dapper - when my Maxtor HD broke), initially ubuntu didn't detect it so I had to adjust the HDD jumpers and reconnect it then it was away

here is their output from "dmesg":

[17179574.824000] Probing IDE interface ide0...
[17179575.112000] hda: ST380011A, ATA DISK drive
[17179575.392000] hdb: ST3802110A, ATA DISK drive

hope this helps

---

### Post by Wesslan on 2006-11-20
Interesting...
I only have one HDD in my system and it's "jumpered" as primary master and has always worked with Mandrake 10.1. Maybe I should try to play around with the jumper settings then how strange it might sound...

Thanks for the info!

---

