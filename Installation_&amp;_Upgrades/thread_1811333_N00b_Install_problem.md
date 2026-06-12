---
title: "N00b Install problem"
date: 2011-07-24
forum: Installation &amp; Upgrades
---

### Post by gnomic on 2011-07-24
I have an old compaq model D51S that I'm trying to upgrade to give away to an old guy that needs a computer. I can get the model to install an old 7.04 CD, but it wont' boot from the 11.04 CD or even a LiLo'ed flash drive.

Unfortunately, the 7.04 doesn't connect to any upgrade servers anymore, so I can't seem to upgrade from the hard drive.

HELP! I just want to get this thing working and setup so the old guy can write letters. 

Thanks. I'm sure the answer is somewhere... but my searches did not identify the right answer for me.

---

### Post by Quackers on 2011-07-24
10.04 may be a better option.
How much ram is installed and what graphics card is used in the pc?

---

### Post by YesWeCan on 2011-07-24
Hi there. Can you give more details about how it doesn't work?
How much RAM have you got, 512MB?
Did you run "check disc" on the CD menu to make sure it was recorded properly?

I'm not sure I'd choose 11.04 - its sort of "new". Does your intended user need Unity?

---

### Post by YesWeCan on 2011-07-24
> **Quackers said:**
> 10.04 may be a better option.
How much ram is installed and what graphics card is used in the pc?
Ah..the duck beat me to it. :P Darned fast creature.
I agree, probably RAM or graphics. I feel a nomodeset coming on.

---

### Post by Old_Grey_Wolf on 2011-07-24
I Googled on Compaq D51S and got results indicating it is a single core Pentium 2.4 GHz processor. It probably came with 512 MB of RAM. I would try Xubuntu or Lubuntu on it from the 10.04 release. Ubuntu 11.04 isn't going to work very well, if at all. The 10.04 releases are supported until April 2013.

Edit: That computer will probably only boot and install from CD. It also appears to have integrated graphics; therefore, it is probably Intel. So, that should not be a problem.

---

### Post by gnomic on 2011-08-02
> **Old_Gray_Wolf said:**
> I Googled on Compaq D51S and got results indicating it is a single core Pentium 2.4 GHz processor. It probably came with 512 MB of RAM. I would try Xubuntu or Lubuntu on it from the 10.04 release.

I tried the 10.04 release and had the same problem. Was there some change in the boot loader between the 7.X and 10.X releases? Its like its not even recognizing that its a bootable CD.

Still stuck at same point.

---

### Post by gnomic on 2011-08-02
> **YesWeCan said:**
> Hi there. Can you give more details about how it doesn't work?
How much RAM have you got, 512MB?
Did you run "check disc" on the CD menu to make sure it was recorded properly?


It doesn't boot from the CD, but it does recognize it once the system is running under 7.X. I've tried multiple CDs and yes, they pass check disk. There is no error message. The drive starts, stops, and the next device in the boot chain (floppy) does the same, then it boots from the hard drive which has the old 7.X version.

The system has 512MB. 

I'm suspecting that the old BIOS doesn't recognize the bootloader, but I don't know how to fix it.

---

### Post by awam66 on 2011-08-02
> **gnomic said:**
> It doesn't boot from the CD, but it does recognize it once the system is running under 7.X. I've tried multiple CDs and yes, they pass check disk. There is no error message. The drive starts, stops, and the next device in the boot chain (floppy) does the same, then it boots from the hard drive which has the old 7.X version.

The system has 512MB. 

I'm suspecting that the old BIOS doesn't recognize the bootloader, but I don't know how to fix it.

You need to set your BIOS to boot from CD first. When you first switch on you probably get a splash screen with the computer name on it. To access the BIOS you need to press a fuction key (mine is F2 or F12. It usually tells you. Then go to the part that shows the boot sequence and change it to CD first then HDD. HTH

---

### Post by gnomic on 2011-08-03
> **awam66 said:**
> You need to set your BIOS to boot from CD first. When you first switch on you probably get a splash screen with the computer name on it. To access the BIOS you need to press a fuction key (mine is F2 or F12. It usually tells you. Then go to the part that shows the boot sequence and change it to CD first then HDD. HTH

The boot order is properly set and I can watch it hit the CD first. I've even tried building a a USB image (with Lilo) and boot from it first -- with the same results.

---

