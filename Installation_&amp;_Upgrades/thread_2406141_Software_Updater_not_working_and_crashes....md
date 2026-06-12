---
title: "Software Updater not working and crashes..."
date: 2018-11-16
forum: Installation &amp; Upgrades
---

### Post by adventure man on 2018-11-16
Hi guys, when trying to use the Software updater on my Lubuntu (Ubuntu 18.04.1 LTS) machine it finds all the updates but when I hit the install button it starts to install but then disappears, not installing anything.  I've had this problem for a while and decided it was time to see if there is a solution. I use terminal commands to successfully update my computer but would like the option to use the software updater. 
 
I also have an issue with "Software & Updates" where in the "Other Software" tab I can't remove some non-existant program entries, for example Opera, Skype, Brave and Firefox ESR which are no longer on my computer: 
[ATTACH=CONFIG]281644[/ATTACH]


Lastly, with "Software & Updates" when I try to change the times to check for updates it doesn't allow me to do that at all ("When there are security updates" is not even clickable):
[ATTACH=CONFIG]281645[/ATTACH]

Is there a way to reinstall/fix Software & Updates?  Or perhaps a GUI, user friendly update installer I can use in it's place? Thank you!

---

### Post by s9032g@comcast.net on 2018-11-16
I had the same problem and just used synaptic for a while. Now I am on 18.10 and the regular updater seems ok.

---

### Post by adventure man on 2018-11-16
Thanks s9032g, I just updated to 18.10 and none of the problems from my first post are resolved.  Still same crash and inability to change times for update checks, etc...

---

### Post by beankylla on 2019-03-22
hello,

i had a similar issue.

sudo apt purge update-manager && sudo apt install update-manager 

solved my problem.

hope it helps!

---

