---
title: "Uninstall Ubuntu Dual Booted with 2 hard drives"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by Trumpman06 on 2008-08-11
I recently put Ubuntu 8.04 on my laptop.  I am dual booting with Windows Vista Ultimate.  My laptop has 2 hard drives so i have windows installed on one and ubuntu installed on the other.  i would like to uninstall ubuntu from my laptop so that i can use my second hard drive.  Any help is appreciated.

---

### Post by caljohnsmith on 2008-08-11
Do you know if Grub is installed to the Master Boot Record (MBR) on your Ubuntu HDD, or is it installed to the MBR of your Vista HDD? What exactly do you get when you startup and how do you boot Vista and Ubuntu? 

The only reason I ask is if Grub is in the MBR of the Ubuntu HDD, just simply reformat the Ubuntu HDD and your Vista HDD should be fine. But if Grub is in the MBR of the Vista HDD, you will have to replace it with the Vista MBR.

---

### Post by Trumpman06 on 2008-08-11
i am not sure which drive it is on but when i start up my computer grub loads and lets me select which os to run.

---

### Post by caljohnsmith on 2008-08-11
Before you format the Ubuntu HDD, see [this thread about how to restore the Vista MBR]("http://ubuntuforums.org/showthread.php?t=740221"). I would recommend having that Vista restore CD on hand, or your original Vista CD, so that when you format the Ubuntu HDD, you can fix your Vista HDD if it has the Grub MBR.

---

### Post by Trumpman06 on 2008-08-11
one more issue...when i am running vista i can only see my vista hard drive.  i cannot see the hard drive that has ubuntu installed on it.

---

### Post by caljohnsmith on 2008-08-11
> **Trumpman06 said:**
> one more issue...when i am running vista i can only see my vista hard drive.  i cannot see the hard drive that has ubuntu installed on it.
That's because Vista (to my knowledge) doesn't have any support for the ext3 file system that Ubuntu uses. There are free programs available though that can make your Ubuntu accessible in Windows, but I assume that is a moot point since you're getting rid of Ubuntu.

---

### Post by Trumpman06 on 2008-08-11
how then can reformat that drive if it isnt accessible through windows?

---

### Post by caljohnsmith on 2008-08-11
Vista has its own disk/partition manager, and I think in there you should be able to see your Ubuntu HDD and format it. That's different then actually mounting your Ubuntu partition in Vista and being able to read/write to it, which requires special software.

Another option is to boot up a Live CD and run:
```
gksudo gparted
```
And that will allow you to format your HDD and partition it any way you like.

---

### Post by Trumpman06 on 2008-08-11
I now have the Vista mbr installed so when i start up i go directly to vista.  i tried to use the 'gksudo gparted' command that was suggested but i get a message saying 'not a recognized batch file or executable'.

---

### Post by caljohnsmith on 2008-08-11
> **Trumpman06 said:**
> I now have the Vista mbr installed so when i start up i go directly to vista.  i tried to use the 'gksudo gparted' command that was suggested but i get a message saying 'not a recognized batch file or executable'.
I think you missed what I said: I said you could boot up a Live CD (like the Ubuntu Live CD), open a terminal (command window), and type that command in. You can't run that command in Windows. :)

---

