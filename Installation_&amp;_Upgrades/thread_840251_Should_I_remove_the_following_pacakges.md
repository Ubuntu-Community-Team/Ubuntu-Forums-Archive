---
title: "Should I remove the following pacakges?"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by garylamanilao on 2008-06-25
Good Day,

I tried installing Avast as anti-virus programs for my Ubuntu 8.04 (64 bit). I've read a couple of times than an anti-virus is not necessary but I just got a bit paranoid (I'm new to linux -> MS OS user for the since DOS... I hope that explains my hesitation at running without any anti-virus... even at DOS I got the (c) Brain virus as well as the old Pentagon. Hahahaha!)


I ran the following scripts at the terminal:

wget [http://files.avast.com/files/linux/avast4workstation_1.0.6-2_i386.deb](http://files.avast.com/files/linux/avast4workstation_1.0.6-2_i386.deb)
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install build-essential dpkg-dev fakeroot


After reading the article of Joe Barr at Linux.com ([http://www.linux.com/feature/60208](http://www.linux.com/feature/60208)) I felt releived and thought that an anti-virus is no longer necessary. Well written article, I think he did a good rundown on how linux based OS works... that's why Ubuntu asks so many times for administrative password. "Ok, so I don't need and anti-virus program then"

Then I came across jdong's (Ubuntu Forum - here) article regarding Malicious Commands ([http://ubuntuforums.org/announcement.php?f=73](http://ubuntuforums.org/announcement.php?f=73)). That really got me worked up. 

Lesson learnt -> more caution on sudo commands, make sure programs sources are of credible sources, easy on administrative passwords.



Question, are the above listed commands a threat to my OS's integrity. The "fakeroot" is really scary. If so, how can I undo them? Sorry for being such a noob... I love the OS, but I'm still thinking under MS rules/conventions. Unlearn, unlearn.

Many thanks,



- Gary

---

### Post by PmDematagoda on 2008-06-25
The packages you installed are not likely to be harmful since they are from the Ubuntu repositories, so you can trust them. About fakeroot, it doesn't do anything but provide a fake root environment so that you could run certain root processes as the normal user, but if the process requires real root permissions then it won't work since fakeroot doesn't provide root permissions.

Edit:- If you wanted to remove the packages, do:-
```
sudo aptitude remove build-essential dpkg-dev fakeroot
```
it is pretty much the opposite of the command you used to install them:).

Oh, and one more thing, don't be over-paranoid, being careful is one thing, but being over-paranoid may cause you to make a mistake yourself.

---

### Post by garylamanilao on 2008-06-25
Thanks PmDematagoda, that's good news to me. Atleast I could rest easy knowing that no one / nothing (virus) is hacking my PC whenever I use it. 

Thanks for the uninstallation tip, I think it's hight time I learn more about the terminal commands. Got to do more research here at the forums and elsewhere. :)

---

