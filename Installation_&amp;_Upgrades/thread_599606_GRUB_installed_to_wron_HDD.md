---
title: "GRUB installed to wron HDD"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by scalextric on 2007-11-01
Hello All, thought I was being clever using a seperate physical hard disk to try out Linux distros so that it would not risk any of my data on the windows XP partitions.
Imagine my suprise after a few attempts att getting Ubuntu installed on the drive that GRUB had installed onto the MBR and now prevents me booting to WIndows.:confused:
Several forums suggest fixes using the winXP recovery console and I will try this.

Its pretty bad form from Ubuntu that there is no way to control this unruly GRUB install.  The first 3 installations I tried put grub in the right place, the 4th didnt, for apparently no good reason at all.:mad:
How do I control which physical drive GRUB gets installed upon?

Not ranting, just suprised!

---

### Post by omns on 2007-11-01
To run a dual boot system you must have grub installed. Restoring the Windows will remove your ability to boot Ubuntu. The windows bootloader doesn't like any other OS other than itself. Unlike grub which will boot as many as you like :)

Your windows partition should have been picked up by grub during the install but seeing that it didn't you can fairly easily add it in manually.
First run the command

sudo gedit menu.lst

In this list you should find a default entry for Windows that will work for your system. Just remove the # marks at the beginning of the lines, save and then reboot. You should be able to boot into Windows or Ubuntu

---

### Post by rsambuca on 2007-11-01
The last step of the installation tells you grub will be installed to the mbr, and gives you an option to set it differently.  Don't get mad at the installer for doing exactly what it told you it was going to do!

---

### Post by scalextric on 2007-11-02
Thanks to you both, but Im not trying to create a dual boot system in the traditional sense of having GRUB allowing me to choose Windows or Ubuntu.
I have 2 physical hard drives which I can enable/disable from BIOS prior to OS boot, I therefore dont need GRUB and the MBR to co-exist, they should be on seperate physical drives.
My question is; how do I control which physical drive GRUB is installed on?  As the Ubuntu installation was on /dev/sda and the Windows installation is on /dev/sdb, why did Ubuntu put GRUB on /dev/sda the first 3 times, then /dev/sdb the 4th time, when on all four occasions the OS installation was onto /dev/sda?

---

### Post by shad0w_walker on 2007-11-02
The last page of the installer. It has already been said. There is a box you click which selects where grub is installed.

---

### Post by scalextric on 2007-11-02
rsambuca, thanks again for your post, I suppose why it went wrong isnt really the issue, not being an expert installer of Ubuntu, could you tell me exactly when/where that message comes up so I can look out for it next time?
Thanks

---

### Post by scalextric on 2007-11-02
thanks shad0w_walker

---

### Post by shad0w_walker on 2007-11-02
The grub option appears on the final page of the installer. When you confirm all the settings and double check your username, etc. Its a button near the bottom of the window.

---

### Post by rsambuca on 2007-11-02
> **scalextric said:**
> Thanks to you both, but Im not trying to create a dual boot system in the traditional sense of having GRUB allowing me to choose Windows or Ubuntu.
I have 2 physical hard drives which I can enable/disable from BIOS prior to OS boot, I therefore dont need GRUB and the MBR to co-exist, they should be on seperate physical drives.
My question is; how do I control which physical drive GRUB is installed on?  As the Ubuntu installation was on /dev/sda and the Windows installation is on /dev/sdb, why did Ubuntu put GRUB on /dev/sda the first 3 times, then /dev/sdb the 4th time, when on all four occasions the OS installation was onto /dev/sda?

One of the little quirks with using multiple drives is that the grub has to basically 'guess' at the order of your drives as listed in the bios.  Usually it gets it right, but sometimes it does get it wrong.  The most problems is when you have mixed IDE and SATA drives.  

You have a choice of where to install the grub at the very last stage of the installation.  If memory serves, it says something like:  "grub will be installed to (hd0)", which you have to agree to.

---

### Post by scalextric on 2007-11-03
I just ran through the installation pages again and there is an 'advanced' button in the lower right hand of the final window that confirms the partition setup.
rsambuca as you correctly say it shows that GRUB will install to " (hd0) ", though its not abundantly clear to me which physical drive (hd0) actually is.
Can I infer from your last post, whichever drive is shown as the primary boot drive in the system BIOS, will become hd0? Or is there still an element of chance?
If there is still an element of chance I presume disabling the Windows HDD in BIOS would prevent an error at installation time?

I did manage to repair my MBR so no permanent damage done :)

Thanks much.

---

