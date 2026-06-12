---
title: "software-center broken after upgrade to 11.10"
date: 2011-10-27
forum: Installation &amp; Upgrades
---

### Post by brouits on 2011-10-27
after an upgrade from 11.04 to 11.10, i got (for an unknown reason) the xapian index broken, and software-center crashed with an exceptionabout the db. I would like to know what files i can safely remove to make software-center work again. I could already safely remove /var/lib/apt-xapian-index/values and rebuild it, but software-center now run with an endless 'waitclock' icon. Can somebody point me to the files to remove/rebuild ? thanks.

---

### Post by brouits on 2011-10-27
Ok, i managed to make software-center work again with those actions:

in a terminal:
sudo rm /var/lib/apt-xapian-index/values
sudo update-apt-xapian-index
sudo software-center
(take a coffee, it's rebuilding the db)
close software center when it is ready, showing categories
do a ^C in the terminal to really close software-center
click sofware-center icon as normal user
(wait again for xategories to show up)
done.

---

