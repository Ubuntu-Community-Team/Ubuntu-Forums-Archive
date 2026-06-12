---
title: "System freeze while upgrading to 8.04"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by Djalmahal on 2008-04-19
Hi,

while I was upgrading from 7.10 to 8.04 my system froze, at that point it had finished downloading and was half way through unpacking when the system froze. I had to restart and it boots, it shows I have 8.04 running, but it runs KDE (i usually run Gnome) and I can't connect to the Internet to restart the upgrading process. My data seem intact. 
So, is there a way to boot it from the 8.04 LIVE cd and then finish the install while keeping the hard drive content intact? Is there any other way, unfortunately I don't seem able to activate the internet, even though it detects my wireless network.

Thanks for your input
Andrea

---

### Post by Pumalite on 2008-04-19
Do this at the Terminal:
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade

---

### Post by Djalmahal on 2008-04-19
Hi,

thanks for you prompt answer  Pumalite, I'm running the first command line and it mentions gnome 2.22 and hardy several times while the lines are running by, so I take it that it's actually installing what the upgrade manager already downloaded. 

Now, the other lines will need an internet connection, and i hope that after it's done the "dpkg" it will allow me to access the internet. If that doesn't work, is there a point in booting (just after running the dpkg command line) or is there a risk in this? 

One last thing: How do I switch from KDE back to Gnome?

Thanks a lot
Andreas

---

### Post by Djalmahal on 2008-04-19
Ok, rebooted after the first line, now back in Gnome with UBuntu 8.10 running, do the "apt-get" lines, Internet is back.

Thanks Pumalite, thanks Ubuntu, I love it...
Andreas

---

### Post by Pumalite on 2008-04-19
Continue running the commands until you are finished. You can change your desktop later at boot.

---

### Post by Djalmahal on 2008-04-19
Ok, I ran all the 4 lines, after that the GUI upgrade manager confirms that the system is up to date. Still, the system behaves sluggish, freezes at random times, I don't quite what to do....

Is there a way to confirm integrity of system files, while running the apt-get it came out multiple times with an error code for timidity

ANdreas

---

### Post by Pumalite on 2008-04-19
Run:
sudo apt-get autoremove

---

