---
title: "Won't Boot after Install; Flawed CD?"
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by wkdude18 on 2008-04-01
I installed Ubuntu using the live CD, and then I rebooted my laptop after removing the disc. But when the computer tried to reboot, it said loading... and then _ and then the screen remained black. I do not understand why it will not boot however I suspect the Cd might be flawed because when I ran an integrity check it said there were 60 missing files. I do not know what to do? Is there a way to get the files into the OS without uninstalling it? I do not want to go through the rigor of doing so.

---

### Post by Pumalite on 2008-04-01
Try:
Ctrl+Alt+F1 to get command line
sudo dpkg-reconfigure xserver-xorg
Get back with results.

---

### Post by wkdude18 on 2008-04-01
Thank you very much. I pressed ctrl-alt-f1,, and the commands reappeared and Ubuntu loaded; however, it seems odd that it won't load without my pressing those keys but its better than a black screen.

---

### Post by Pumalite on 2008-04-01
Can you explain to me better what happened? Ctrl+Alt+F1 was only to get a command line. Did you reconfigure your xserver?

---

### Post by wkdude18 on 2008-04-02
No. I just pressed ctrl-alt-f1, the command line loaded, and the OS loaded before I could enter the command.

---

### Post by wkdude18 on 2008-04-02
Stuff like checking for drivers [ok] loading files needed for boot [ok] and there was no time for me to type it in. It just loaded after pressing ctrl-alt-f1.

---

### Post by Pumalite on 2008-04-02
Have you been booting without problems following that?

---

### Post by wkdude18 on 2008-04-03
After I press ctrl-alt-f1, I have no problems booting.

---

### Post by Pumalite on 2008-04-03
Just to be sure. Check your UUID's
Compare
blkid (at the Terminal)
With:
cat /etc/fstab

---

### Post by wkdude18 on 2008-04-12
yeah there pretty much the same. Muchas gracias. Much thanks for your help.:):):popcorn::guitar::KS

---

### Post by Pumalite on 2008-04-12
You are welcome. (De Nada). Good luck.

---

