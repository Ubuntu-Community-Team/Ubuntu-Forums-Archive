---
title: "Upgrade failed"
date: 2019-10-20
forum: Installation &amp; Upgrades
---

### Post by michaelharden1a on 2019-10-20
I attempted to upgrade, during the upgrade while installing packages the computer locked up, I was able to get into plasma desktop I installed to test out and when doing dpkg —configure -a the computer locks up again, is there a upgrade install option from the live iso? It was an option to save your files and data and reinstall the operating system, I don’t see the option on the 19.04 key, was just wondering if there was a way around having to manually save as much data as possible and starting from sratch.

---

### Post by rsteinmetz70112 on 2019-10-20
What version are you on? What did you do to upgrade?

---

### Post by zimbuf on 2019-10-21
I think the most time-efficient option might be to go ahead and create a sizable partition on your disk and move stuff there. Install Ubuntu around it, and then edit /etc/fstab (on the newly installed Ubuntu) to have it mounted as a regular folder in /opt/<desired name> or $HOME/<desired name>. In general, it's a good practice to have your data like this anyway, as it makes you fairly resilient to botched upgrades or installs.

Any other solution will end up taking significantly longer to tinker around with, IMO.

Also, for the future - the symptom you saw might have been a kernel level bug regarding the out-of-memory routine not being called on high memory load. It tends to end in total system deadlock. You may want to consider using aptitude (if you didn't) as opposed to apt-get or the graphical updater to initiate a dist-upgrade. It might help with situations like this, as it's usually better at catching dependencies.

---

### Post by michaelharden1a on 2019-10-21
19.10

---

### Post by michaelharden1a on 2019-10-21
I&#8217;m assuming that there is no way to drop into a command line shell and run the dpkg command with that said backup data and reinstall, I was thinking the same thing.  I&#8217;ll probably go about that soon

---

### Post by michaelharden1a on 2019-10-21
I think dropping into recovery mode will work, to explain the exact same thing albeit a little different t happened to the churches computer, during upgrade to 19.10 it suddenly went black, like it logged out and was in the state before going to login screen, I was able to boot from earlier kernel, gnome was damaged and could not log in, I had and forgot about it, installed unity, which is not updated by conical, I was able to go into terminal and run dpkg configure it finished the upgrade and was good I think since on my laptop kde and gnome are updatable packages both of them were damaged in some way causing the lockup when trying to run the terminal command, I will attempt recovery mode, command line and run the command directly from command line, if I’m correct this should finish the upgrade.  If not there is the backup and restore method I’ll do if it does not work.

---

### Post by michaelharden1a on 2019-10-21
Officially solved, I finished upgrade by going into root shell under recovery mode, it failed to install 3 items which I was able to finish when I booted up to a newly freshly working kernel and GUI

---

