---
title: "lost power while upgrading"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by jdsloan on 2010-05-08
H E L P was upgrading my GREAT UBUNTU 9,1 to 10.04 ran for about 4 hours, 1 hour left and lost power, CRASH    aaaaaahhhhhhhh what are my options.

---

### Post by mörgæs on 2010-05-08
I wouldn't waste my time trying to rescue a system which has suffered a hard shut down during an upgrade. The fast and safe approach is getting your files out and doing a clean install of 10.04.

---

### Post by Catharsis on 2010-05-08
```
sudo apt-get clear
sudo apt-get update
sudo apt-get dist-upgrade
```
It may want you to do some other things like:
```
sudo apt-get -f install
sudo dpkg --configure -a
```
These would also be helpful to run.

If you can't get to a terminal, hold down Shift while booting to enter GRUB, select the recovery kernel, and then select "root shell with networking". In this case, you don't need "sudo" in your commands.

---

### Post by jdsloan on 2010-05-09
tried to install 10.04 from cd, error message of "unknown user", UPGRADING is the worst idea EVER, do not do it, I had a fantastic UBUNTU in 9.1, now I have NOTHING, I give up, will be my last UBUNTU thread, going back to the demon spawn Windows, fun while it lasted but am beaten

---

### Post by mörgæs on 2010-05-09
I hope that you are still reading this.

If 9.10 works, you don't need to worry about other versions for the next year. There is full support for 9.10 through april 2011, though 10.04 is released.

---

