---
title: "Winblows XP dual boot problems with Account Recognition"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by Nytemare on 2007-09-09
Hello everyone,
I am trying to install Fiesty on my fathers machine to dual boot with Win XP (he wanted it after he saw what beryl could do lol). I opted for the manual partitioner he's what i saw
/dev/sda
      /media/sda1       6000mb (this is a recovery partition fro winblows)
      /media/sda2       78000mb ntfs (winblows partition)

I partitioned it so that it looked like this 

/dev/sda
     /media/sda1       6000mb (still recovery partition)
     /windows            58000mb (winblows)
     /                         17000mb  ext3 (ubuntu)
                                2000mb    (swap)

when i clicked next it did not find the user accounts as it normally does and I worried that this might mean it did not find winblows on the HDD. Could this be due to the recovery partition being sda1?

thanks for any help

PS: I'd really love it if i didn't hose this system lol

---

### Post by Pumalite on 2007-09-09
Well, what happened?; did you reboot to find Grub?

---

### Post by Nytemare on 2007-09-09
I did not finish the installation because this worried me some. I have used linux for about a month now but am still a newbie so i did not try and go through with it.

---

### Post by Pumalite on 2007-09-09
Go back and check: 'Do not Import Accounts' and continue with installation.

---

### Post by Nytemare on 2007-09-09
I know how to get past it really I was wondering if it would GRUB would find winblows if it didn't find the accounts.

---

### Post by Pumalite on 2007-09-09
The accounts have nothing to do with Grub.

---

### Post by Nytemare on 2007-09-09
So this is not a sign that GRUB will not work?

---

### Post by Pumalite on 2007-09-09
There might be a number of things that can go wrong with your installation, but not because of the accounts. Best is to backup everything first.

---

### Post by Nytemare on 2007-09-09
i have. I just wanted to check with one of you gurus before i continued.
thank you

---

### Post by Pumalite on 2007-09-09
You are welcome. Good luck.

---

