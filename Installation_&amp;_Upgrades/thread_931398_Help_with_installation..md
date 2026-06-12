---
title: "Help with installation."
date: 2008-09-27
forum: Installation &amp; Upgrades
---

### Post by TheRiddler12 on 2008-09-27
I downloaded the .iso file from the official Ubuntu website, i ran the iso in a virtual drive then used the 'in' windows option to install from windows, it installed fine but when i boot linux it goes to 'BusyBox' and its a command line, i dont know how to get to the desktop, any ideas ?

Thanks in advance :)

---

### Post by Pumalite on 2008-09-27
Do you get 'initramfs'?

---

### Post by TheRiddler12 on 2008-09-27
yeah i do mate and i dont know any commands do im like stuck lol

---

### Post by Pumalite on 2008-09-27
Post:
lshw

---

### Post by TheRiddler12 on 2008-09-27
is tha all i need ?

---

### Post by Sef on 2008-09-27
> is tha all i need ?


Yes.  That will be the start.  We will go on from there once you post your lshw.

---

### Post by TheRiddler12 on 2008-09-27
i have just discovered something, wen i installed it, i installed it to my external harddrive, when i boot with it plugged in, i get the 'initramfs' command line but when i boot without it i get a 'grub' command line, and i tried the 'lshw' command and it said it isnt a reconised command.

---

### Post by WWSmith36 on 2008-09-27
Sounds like you are trying to install with wubi.  I would not recommend doing this.  Wubi installer is a good method, but not the best.  Wubi installer don't make a real ext3 filesystem partition, separated isolated from Windows, it create a big file into the windows filesystem and install Ubuntu in it, so if you have problems into Windows partition (viruses, filesystem corruption) you can damage and loose all the installed Ubuntu.

---

### Post by TheRiddler12 on 2008-09-27
Ive managed to uninstall linux without the installer :D now which is the best way to install it to my external harddrive ? so its only there wen the external harddrive is plugeed in :D haha

---

### Post by TheRiddler12 on 2008-09-27
Ive managed to uninstall linux without the installer :D now which is the best way to install it to my external harddrive ? so its only there wen the external harddrive is plugeed in :D haha

---

