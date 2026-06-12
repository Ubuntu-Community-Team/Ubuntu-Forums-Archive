---
title: "cannot log in on graphical mode"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by then_dude on 2010-11-27
hello everybody

i rebooted my pc, and now i cannot log on to my system anymore , at least graphicly. 

i get the graphical window with all the users in it, and i can choose an enter passwords, but after that i get te message

[B]The configuration defaults for GNOME Power Manager have not been  installed

i am running 10.04


can anyone help me ?

i also cannot connet via the terminal to a wifi wpa2 router. 

thanks


[/B]

---

### Post by andrewthomas on 2010-11-27
from the login window press <CTL>+<<ALT>+F2 to get a terminal

login then 

```
sudo apt-get update && sudo apt-get upgrade
```

then <CTL>+<<ALT>+F7 to get back to the gdm login and try again

---

### Post by metalf8801 on 2010-11-27
I had the same problem is was solved by making the partition with Ubuntu installed larger because it had run out of free space. 

Can you do that? You could also try deleting extra files from the command line. 

Good luck 
Dan

---

### Post by then_dude on 2010-11-27
it is indeed the problem that my harddisk is running out of space. 

okee, looking who is the culprit

sudo du -s * | sort -nr | head shows that it is in the media dir, so there are my ntfs partitions mounted


one of the partitions is 9 gig big, how can that be, 

maybe i mounted it wrong or so ? 
can anybody help me please

thanks

---

### Post by then_dude on 2010-11-27
i did it

:popcorn:


i mounted the drive to another mounting point.

then i  unmounted all the drives

then i saw that the previous mount was still 9 gig bigs

i deleted it with force

rm -rf  

my ubuntu is up and running again,  i'm gonna check if something is flooding my harddisk

thanks guys

---

