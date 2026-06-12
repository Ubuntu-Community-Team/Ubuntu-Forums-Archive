---
title: "Install ONLY Ubuntu OS on SSD (22gb) [Samsung NP530]"
date: 2014-02-18
forum: Installation &amp; Upgrades
---

### Post by jorgemariel94 on 2014-02-18
IN ENGLISH:
i have an ultrabook samsung series 5 ultra NP530 and i want to install Ubuntu (and Windows) this way:

SSD (22gb): Ubuntu 12.04 (only O.S., not programs)

HDD (500gb): Windows 7
                   All programs of Ubuntu
                   Data Shared on both OS (Music, Photos, Docs, etc) 

How could i do this? help meeee (Sorry for my bad english)

EN ESPAÑOL:
tengo una ultrabook Samsung series 5 ultra NP530 y quiero instalar SOLO el SO en el SSD.
Lo que quiero decir es que necesito que se instalen los programas de Ubuntu en el HDD para que no se me llene el SSD (ya que es muy chico y se me hara un lio)
Obvio que tmb quiero dual boot y comprartir todos los datos entre los Sistemas Operativos

simple: solo SO en SSD y TODO lo demas en el HDD

---

### Post by ajgreeny on 2014-02-18
I don't think there is any simple way to do that in Ubuntu as its file system arrangement is very different from Windows, though I certainly can't help with any Windows queries as I don't use it any more.

You could try making separate partitions on the HDD with ext4 format for /usr and maybe for some of the other main folders in your filesystem at the time of OS installation, as /usr is where all the packages mainly are installed, (my /usr folder is 4.8GB out of the total 6.5GB for my whole OS partition ie, almost 75% of the total) but I would not personally recommend it.

Why do you want to keep the programs separate from the OS?  I do not think there will be any real advantage in doing so; in fact I suspect exactly the opposite, though I would wait for other forum users to answer before doing anything more; I could be wrong.

---

### Post by jorgemariel94 on 2014-02-18
the SSD is TOO small.. if i want to install lots of apps muy SSD will be completly full and i would have space problem...

---

### Post by oldfred on 2014-02-19
I have a 60GB SSD, and have it configured with two / (root) partitions each about 28GB. My working install uses about 11GB and that includes /home. My /home is about 2GB, but most of that is .wine for Picasa. But I do aggressively move all data folders like Music, Videos etc and some hidden folders in /home like Firefox & Thunderbird profiles that start to get larger into my data partitions. I have two data partitions, one NTFS from when I still booted XP, but all new data now goes into my Linux formatted data partition.

So you should be able to use 22GB for / without issue.
If apps are not in SSD they will not load quickly.

---

