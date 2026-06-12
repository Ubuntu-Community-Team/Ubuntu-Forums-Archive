---
title: "could not update ICE authority file"
date: 2013-09-11
forum: Installation &amp; Upgrades
---

### Post by geekhush on 2013-09-11
hi,
so i recently upgraded from ubuntu 12.10 to 13.4 using a live usb and now i get the error "could not update ICE authority file ubuntu 13.4" and cant log in as the admin. i installed kde and it doesnt work very well too. i also dont see the old user from my ubuntu 12.4 install and hence no files too, although i can access them from the home folder(old user) and none of the applications can be accessed. can anyone help? thanks in advance.

---

### Post by Toz on 2013-09-11
Try deleting the .ICEauthority hidden file from the home directory of the admin account. To do this, from the login screen, go to the first tty (Crl+Alt+F1) and login with your admin account into the console (text) session. Once logged in, issue the following command:
```
sudo rm .ICEauthority
```
...(enter your password when prompted). The go back to the GUI login screen (Ctrl+Alt+F7) and try logging in again with your admin account.

---

### Post by geekhush on 2013-09-13
hi, thanks for the quick reply :)
anyways so i deleted the .ICE  authority and i am no more getting the error but i cant see anything as i  log in. i am guessing the gnome is the culprit, but i am not really  sure.... any other suggestions?

---

