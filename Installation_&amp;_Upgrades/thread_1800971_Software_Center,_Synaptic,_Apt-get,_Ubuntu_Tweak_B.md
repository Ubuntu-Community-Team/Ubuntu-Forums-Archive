---
title: "Software Center, Synaptic, Apt-get, Ubuntu Tweak Broken"
date: 2011-07-09
forum: Installation &amp; Upgrades
---

### Post by Jlb181 on 2011-07-09
Any program I use to try and install or update software suddenly will not start.  Using the command line I get no errors listed.

The results of apt-get update seem fine.  No errors reported.

apt-get install gives me this -


jeffery@Birkhofer-MS-6702:~$ sudo apt-get install atop
Reading package lists... Done
jeffery@Birkhofer-MS-6702:~$ 0%

The 0% is false, I can type a command at the same prompt the 0% is on, example ls, and get results without deleting the 0%.  

jeffery@Birkhofer-MS-6702:~$ sudo apt-get install atop
Reading package lists... Done
jeffery@Birkhofer-MS-6702:~$ ls
070311        Desktop    Dropbox           Pictures  pyNeighborhood  Videos
Ambience.tgz  Documents  examples.desktop  Podcasts  Templates
Audiobooks    Downloads  Music             Public    Ubuntu One
jeffery@Birkhofer-MS-6702:~$ 


What happened . . . I did a check for updates.  Pithos had an update, it downloaded and started the process, apparently it didn't finish because when I entered sudo dpkg --configure -a
the update finished.

Combing through google I found a lot of things to try but nothing is working.  If you need more info to help let me know. 

Thanks

---

