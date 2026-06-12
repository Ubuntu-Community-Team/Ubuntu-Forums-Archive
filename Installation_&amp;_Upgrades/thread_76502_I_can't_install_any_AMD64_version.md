---
title: "I can't install any AMD64 version"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by tymek666 on 2005-10-15
I tried more than 10 times to install ubuntu and kubuntu AMD64. Every time instalation freeze during copying or instaling (after partitioning). Installation freeze in variable stage, sometimes after 5%, sometimes after 97%. Of course i've checked cds. They are fine. Once i was even able to create account but it's freeze during testing respositories... Do you have any ideas how to install ubuntu?
My config: athlon64 (venice), nf4 mobo (gigabyte), gf6600, 1gb ram, sata hdd with xp and pata hdd for linux, dlink 520+ wifi card.

---

### Post by zekolas on 2005-10-15
check out 
[https://wiki.ubuntu.com/Installation](https://wiki.ubuntu.com/Installation)
"Advanced Installation Methods" it shows you how you can install ubuntu using a knoppix live cd, or from windows using a boot disk. This might be some help since it seems the cd installer is lett you down, these installs use the network so it you will need a high speed connection.

---

### Post by mmorales on 2005-10-15
Same problem here!

I try to install the 64bit 3 times with two direfent iso image in two different partition, freeze at 91% and two time on 97% :???:

---

### Post by tymek666 on 2005-10-15
Ok, i know what cause this problem. Just turn off cool'n'quiet function in your mobo bios. Unfortunatly not evey mobo let you do it. F.e my gigabyte k8nf-9 doesn't have this option in bios. But generaly it's rather bug in AMD64 breezy :(
BTW, i'm already running i386 which works fine and install without any problems.

---

### Post by zbirdman on 2005-10-15
I was having the same problems as described above. Disabling "Cool'n'Quiet" in the BIOS eliminated problems with the system freezing while trying to install Ubuntu in general. Never would have thought to even try that one! Good tip.

---

### Post by mmorales on 2005-10-16
I have a MSI K8N Neo Motherboard, even with cool'n'quiet disable on BIOS, installation freeze, ubuntu 5.10 32bit was installed without freeze, but I want the 64bit version any help will be appreciated

---

### Post by tymek666 on 2005-10-16
Does anybody installed 5.10 AMD64 on mobo with nforce4 chipset?

---

### Post by mmorales on 2005-10-16
Mine is a k8N Neo 250GB nforce3

---

### Post by mmorales on 2005-10-17
Coincidence I don't know but the 64bit installation succeed
It was with a new iso image and with cool'n'quite enable :p

---

### Post by mandingo on 2005-10-17
I'm stumped. Running a HP zv6000 (amd 64 3200+).


I usually get to between 80-97% before I freeze. I can't even boot with a debian disc. 

Checked MD5 sums and everything is gravy. Burnt to two discs. Don't have the cool'n'quite option in my BIOS.

Any ideas?:confused: :confused:

---

### Post by Corbelius on 2005-10-17
[QUOTE=tymek666]Does anybody installed 5.10 AMD64 on mobo with nforce4 chipset?[/QUOTE]

I have had the same problem, MSI K8N Neo4 Platinum, I have resolved burning the iso on a cd-r instead a cd-rw.

---

### Post by mandingo on 2005-10-17
[QUOTE=Corbelius]I have had the same problem, MSI K8N Neo4 Platinum, I have resolved burning the iso on a cd-r instead a cd-rw.[/QUOTE]


Been using CD-R media the entire time.

---

### Post by Salane on 2005-11-25
I got mine to install using 
linux pci="noirq'

---

