---
title: "[SOLVED] how do i install a 250GB SATA 150MB/s harddrive with ubuntu?"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by jmate24 on 2008-02-18
problem, i have a 250GB Drive that i want to install in my computer and arrange my harddrives so that i am able to use the 250GB drive as my /home folder and have my 80GB ide drive be the / partition with my 120GB ide drive as windows xp pro sp2.
i know that i can set my bios to make the sata raid controller on my motherboard detect the drive as an ide drive. but how do i go through the process, and will the ubiquity installer detect my sata drive as a sata ide drive?
i've tried this before and lost most of my data but found some of the missing part's on other dvd's and i now have my 80GB as a backup drive.

my current setup is:
MSI V-class P4 32-bit 3.2Ghz with sata raid 0,1/sata ide controler Via Chipset
300-watt Power Supply
1GB RAM
Primary
MAXTOR 6L120PO 120GB HDD MASTER mp: /home (BOOT)
MAXTOR 6L040J2    40GB HDD SLAVE mp: /
Secondary
Lite-ON DVDRW/RAM LH-20A1H MASTER
MAXTOR 6Y080P0   80GB HDD SLAVE mp: /media/disk  (Backup Drive)
UBUNTU 7.10 Gutsy USER

---

### Post by Pumalite on 2008-02-18
Boot your Ubuntu Live CD and post from the Terminal the output of:
sudo fdisk -lu
Make your BIOS see SATA as IDE first.

---

### Post by GTvulse on 2008-02-18
There are two problems to consider:

1. THe HD has a SATA II bus and your board can do SATA I only. Unless you can set the HD firmware to emulate SATA I by moving jumpers around or plugging it to a board that supports SATA II and running the HD manufacturer utility software to cap the HD controller to emulate SATA I, you are out of luck (being there, done that).

2. Your board may have a newer BIOS firmware available at the manufacturer's support site that corrects some of the problems you've found. Install it.

---

### Post by jmate24 on 2008-02-19
My Bios Has The Latest Firmwear It was designed for a Prescott Processor and when i went to upgrade and install it; it fully recognized that it was hyper-threading plus on the board it should only be SATA I and so should the hard drive. really all i have to do is make the ubiquity recognize that the via sata raid controler as an ide controler and set my bios to that setting as well and then plug and go. i think that i might possibly be able to save my data as well seeing as to how i will be installing windows on my 120GB drive first. Then copying my data from my 80GB to that 120GB drive. Then when installing ubuntu 7.10 make the / be the 80GB and the home be the 250GB and then copy/move the files from my windows drive to my /home folder. sounds like a snap:lolflag::idea::-\"

---

### Post by jmate24 on 2008-02-20
i've come to find out that this hard drive is oem and that it came with no install cd or jumpers or cables. what do i do now?

---

### Post by jmate24 on 2008-02-22
ah success i tried the sudo fdisk -lu and saw that it was detected and so i formated it ntfs with gnome partition editor. then with ntfs configuration tool i deselected enable write support for internal device and external device then i clicked OK and waited for it to complete then restarted my computer and then opened up the ntfs configuration tool and enabled write support for both internal and external devices and it asked me to give a mount point (just one word 'windows' i.e.) and then i waited and it mounted my new hard drive and i think i can use ntfs config tool in ubiquity so that i can setup a new install with ubuntu. i will report my progress sat feb 23. so please do not close this thread!!!:)

---

### Post by jmate24 on 2008-02-24
It works! Thanks.  I set the Jumper to see the hard drive as 150MB/s Only and I am able to use it I was even able to set it as my /home folder now i have ~216.4GB of space from a 250GB drive thats because i put my swap on that drive which does make a difference. Keep Posting!!:)

---

### Post by Guinness70 on 2008-03-11
ubuntu Gutsy is working.
i added another internal HD yesterday it showed up just fine.
today it doesnt show up...

its a backup drive that was used under windows (i no longer have windows).
worked fine yesterday, not working today :confused:

these are my first 2 weeks in linux/ubuntu so be gentle

---

