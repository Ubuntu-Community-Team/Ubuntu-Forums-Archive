---
title: "Ubuntu 10.10 install does not finish"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by Bigs11 on 2010-11-26
I've installed previous Ubuntu and other linux distros in the past, so I have a fair idea what I'm doing.
I downloaded the official Ubuntu 10.10 ISO from Canononical, burned to CD and booted from that.
I chose to install, using an existing swap partition, and a freshly formatted (ext4) partition, with mount point "/" as root.
The installation runs fine up to where I enter my User, Computer and Login details.
The forward button to continue, remains greyed out, even tho the copying of files finishes and says down the bottom that I'm ready to go.
At this point, I can't exit, log out, or do a proper restart.
Only a forced reset of the computer gets me out of the installation.
No files get installed on the partition, but the MBR does get written to.
And obviously I get an error trying to boot to it.
I've tried this same procedure 3 times now, with exactly the same result each time.
Any ideas, people?
Thanks in advance :p

---

### Post by Quackers on 2010-11-26
Did you start your username with a capital letter? No capitals allowed at the start of username. It should flag an error but it doesn't. Try  again without a capital.

---

### Post by Bigs11 on 2010-11-26
I used Capitals on all three information areas.
I'm sure I've done that in the past with other distros.
I will try that tomorrow with all lowercase, and let you all know the outcome.
Thanks for the help.

---

### Post by carl4926 on 2010-11-26
Did you run the media check from the cd boot menu? To check the integrity of the cd

---

### Post by Bigs11 on 2010-11-26
Nope, how do I do that?
You mean the checksum?

---

### Post by carl4926 on 2010-11-26
Boot the live cd
get to the boot menu and choose it from there

---

### Post by Bigs11 on 2010-11-27
Was just the uppercase username.
Soon as I used lowercase, it let me finish the install.
All&#347; good.
Thanks for the help.
How do I mark this as solved?

---

### Post by szigetir on 2010-11-27
10.10 install doesn't finish for me neither. The progress hangs. at 97%.

---

