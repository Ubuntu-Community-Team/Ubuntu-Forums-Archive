---
title: "Ubuntu upgrade not showing"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by ambdeep on 2010-01-30
I just ran system update(i did not upgrade to 9.10)......after that i wanted to upgrade my system to 9.10 but the upgrade option is not showing.....when i check my update options it shows "normal releases"....ive run a check on the available updates also but it still doesnt show the option.....please help.....thanks in advance!!!!

---

### Post by ambdeep on 2010-01-30
*bump*
please help

---

### Post by ambdeep on 2010-01-30
Is there no solution?

---

### Post by raymondh on 2010-01-30
This is a result of a quick google search

[http://ubuntu-tutorials.com/2009/10/28/how-to-upgrade-to-ubuntu-9-10-karmic-koala/](http://ubuntu-tutorials.com/2009/10/28/how-to-upgrade-to-ubuntu-9-10-karmic-koala/)

remember to be updated in jaunty before upgrading.  Also, have a working/tested back-up of your files.

---

### Post by ambdeep on 2010-01-30
thats the problem......it was showing till abt 2 hrs ago....now it doesnt show.....

---

### Post by raymondh on 2010-01-30
you could try using the terminal.  Again, be updated first in jaunty before upgrading to karmic.  And, have a back-up.

Method 1

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Method 2

```
sudo apt-get install update-manager-core
sudo do-release-upgrade
```

Method 3

```
sudo apt-get install update-manager
sudo update-manager -d
```

I have used both methods 1 and 2.

To find out what version you are in now

```
lsb_release -a
```

Regards,

Raymond

---

### Post by ambdeep on 2010-01-30
Thanks!!!!!

---

