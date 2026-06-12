---
title: "GRUB ERROR  Please Help :("
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by braveerudite on 2005-10-14
](*,)  I'm trying to install the AMD64 5.10 Ubuntu but after two installation attemps I can't get UBUNTU to load.  I am getting the following massege during the first boot after copying the installation files to the HDD (ATA 60 Gg @7200 RPM) 

"GRUB Loading Stage1.5Read Error"

Can someone please help an Ubuntu fan out?   

Please give out noob explanation. ](*,)

---

### Post by livingtarget on 2005-10-14
Are you trying to dual boot by any chance? 

I used to get some error like that by trying to boot from ntldr (the windows boot manager) and having ubuntu on a second drive. Got around it with some bootdisks and eventually installed wingrub which works half decent.

If you are not dual booting then maybe reinstall grub?

---

### Post by braveerudite on 2005-10-14
I have 2 HDD, One SATA drive for Windows conected to the SATA thingy and the other is connected to the Primary Master IDE. 
Note: When  I tryed to install Ubuntu to the regular IDE HDD I completely disconnnect the SATA drive to avoid conflicts but still wont innstall properly. ](*,) 

Whats going on? I would hate having to go back to Fedora because of this.  [-o<

---

### Post by braveerudite on 2005-10-14
someone plz help

---

### Post by yerffej on 2005-10-15
I had this exact problem but with a Asus motherboard. Changing the boot sequence of my two hard drives in the BIOS resolved the problem.

---

### Post by alainhenry on 2005-10-16
I have a similar problem.  Just to make sure I understand, if you change the boot order in the bios, then hda becomes hdb and conversely.  You then have to update you menu.lst to take account of this, I assume ? (basically, all hd0 become hd1 and hd1 become hd0)

Alain

---

