---
title: "BIOS CD boot?"
date: 2012-01-25
forum: Installation &amp; Upgrades
---

### Post by c0brabg on 2012-01-25
Hello I have a certain problem here. So a friend wanted me to reinstall her computer so I said what the heck and we decided that she should go with Ubuntu. Her computer is not very old and her bios is Energy 6.00. The problem is that I can't get the CD to start heck I using a DVD with windows 7 and it still didn't work. I also tried launching the CD from the already dying need of reinstallation Windows Xp.  
 I set the BIOS to boot from CD-ROM. It's strange though on my laptops I normally press F2 and I get a boot option but I can't find it there, only boot priority and it always seems to go for the HDD no matter what I do.
 Thank you in advance for the help. I also can't find the motherboard model but I'll try that too if it's really needed thought I don't know if I can even install everest.

---

### Post by Quackers on 2012-01-25
Are you sure you selected cd-rom and not something like USB cd-rom?

---

### Post by c0brabg on 2012-01-25
> **Quackers said:**
> Are you sure you selected cd-rom and not something like USB cd-rom?
  Yep pretty sure. Is it possible that the CD was written on such a slow speed that the computer cant read it.

---

### Post by oldfred on 2012-01-25
How old is this system?

This only shows booting from IDE devices. Most CD's were on the IDE chain and could be booted as secondary master. But real old systems only booted from floppies. 

[http://www.google.com/#sclient=psy-ab&hl=en&site=&source=hp&q=BIOS+Energy+6.00&pbx=1&oq=BIOS+Energy+6.00&aq=f&aqi=&aql=&gs_sm=e&gs_upl=732l2619l0l3512l6l6l0l0l0l0l183l806l0.6l6l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=2e384fa13cd4139e&biw=1280&bih=575](http://www.google.com/#sclient=psy-ab&hl=en&site=&source=hp&q=BIOS+Energy+6.00&pbx=1&oq=BIOS+Energy+6.00&aq=f&aqi=&aql=&gs_sm=e&gs_upl=732l2619l0l3512l6l6l0l0l0l0l183l806l0.6l6l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=2e384fa13cd4139e&biw=1280&bih=575)

---

### Post by c0brabg on 2012-01-25
> **oldfred said:**
> How old is this system?

This only shows booting from IDE devices. Most CD's were on the IDE chain and could be booted as secondary master. But real old systems only booted from floppies. 

[http://www.google.com/#sclient=psy-ab&hl=en&site=&source=hp&q=BIOS+Energy+6.00&pbx=1&oq=BIOS+Energy+6.00&aq=f&aqi=&aql=&gs_sm=e&gs_upl=732l2619l0l3512l6l6l0l0l0l0l183l806l0.6l6l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=2e384fa13cd4139e&biw=1280&bih=575](http://www.google.com/#sclient=psy-ab&hl=en&site=&source=hp&q=BIOS+Energy+6.00&pbx=1&oq=BIOS+Energy+6.00&aq=f&aqi=&aql=&gs_sm=e&gs_upl=732l2619l0l3512l6l6l0l0l0l0l183l806l0.6l6l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=2e384fa13cd4139e&biw=1280&bih=575)
  It actually said 2005, the processor was something along the lines of amd 3100 so I guess it's not too old. The motherboard was a Gigabyte (now I remember when going to bios repair or something). Can reflashing the bios help? Though I wouldn't want to risk that.
 And the problem is that the manual I also found is a little different from the real things. I guess I am gonna have to take pictures or something.
 Edit: Very likely to be AMD Sempron 3100+

---

### Post by lisati on 2012-01-25
> **oldfred said:**
> But real old systems only booted from floppies. 

+1. Although my 12-year-old machine supposedly can boot from CD, when I put Ubuntu on it, I needed to have a boot floppy that loads up drivers and hands over control to the CD (not the original drive)

---

### Post by Quackers on 2012-01-25
Have you checked that the cd drive actually still works?
Have you tried that particular disc on another machine?

---

### Post by c0brabg on 2012-01-25
> **Quackers said:**
> Have you checked that the cd drive actually still works?
Have you tried that particular disc on another machine?
  1.Supposedly works. My friend said that 3,4 days before her PC she said that sjhe could load up images on a DVD 
  2. Yes I tried it on my laptop works fine
 And about the floppy. Well I'm sure the PC is old but not that old I mean it's maybe like 4,5 years or so. But it has a floppy cartridge (or whatever you call them).

---

### Post by fsLori on 2012-01-25
If your CD boots on other machines, something may me wrong with that CD-drive. If it doesn't boot on other machines, your CD may be damaged. A fine alternative could be to boot from a bootable USB stick with Ubuntu on it.

---

### Post by c0brabg on 2012-01-25
> **fsLori said:**
> If your CD boots on other machines, something may me wrong with that CD-drive. If it doesn't boot on other machines, your CD may be damaged. A fine alternative could be to boot from a bootable USB stick with Ubuntu on it.
Doesn't thtat work only with the newest computers ?Though i will try it.

---

### Post by darkod on 2012-01-25
You are right, a PC that is 4,5 years old should definitely boot from CD.

1. Check the connections of the cd-rom. If it's sata, check the sata cable and the power cable. Try with another power cable, if you can also with another sata cable. Try another sata port on the board.

2. If it's IDE, make sure it has no conflict with a HDD for example if they are both set to Master. It might need a jumper to set it as Slave if on the same cable (channel). Again, check the power cable and try another power connector.

3. Try the usb stick option, 5 years ago it's still possible it would boot from usb.

On Gigabyte the boot menu is usually F12 during boot, if it has a boot menu.

---

### Post by RangerRay on 2012-01-26
> **Quackers said:**
> Have you checked that the cd drive actually still works?
Have you tried that particular disc on another machine?

As Quackers stated, check to see if CD/DVD Rom works, I'm saying this from having the same problem 

a week ago. Check and make sure that the power cable, as a matter of fact, check and make sure that  

all cables going from CD/DVD Rom, floppy disk and hard drive are connected firmly to the units and on 

the mother board. You may also want to check the jumpers on the Rom and floppy drive are on properly 

(if required). I made the mistake of forgetting to install the third wire to my DVD Rom, which I can not tell 

you the name of it. That was my first problem. The next problem that occurred was the CD I downloaded 

Ubuntu 11.10, was not a CD, but a DVD, so I had to swap out My Cd Rom with My DVD  Rom so the disk 

would work. Once, I took care of these problems, placing the disc in, The system automatically 

recognized the disk and started the installation. Normally, i use F-2 or F-12, even hitting the delete button 

to get boot able device screen. I hope this helps!:D

---

