---
title: "firefox"
date: 2005-05-22
forum: Installation &amp; Upgrades
---

### Post by [pl]ice on 2005-05-22
hi, i posted this problem at other place, still no help :(
   i run the install of 1.0.4 firefox gz it insalled sucessfully, but when i try to run it under my user i get a finger :/ i.e. nothing, when i run sudo ./firefox it pops out, 
i tierd to chown it to my user didn't work.
tired to get it from bacports, same thing.
  Plese help.

thanks

---

### Post by zxee on 2005-05-22
[QUOTE='[pl]ice']hi, i posted this problem at other place, still no help :(
   i run the install of 1.0.4 firefox gz it insalled sucessfully, but when i try to run it under my user i get a finger :/ i.e. nothing, when i run sudo ./firefox it pops out, 
i tierd to chown it to my user didn't work.
tired to get it from bacports, same thing.
  Plese help.

thanks[/QUOTE]
 Did you do "chown ug+x"? 
It might be easier to just install it with apt-get provided you uncomment the required repositories.

---

### Post by [pl]ice on 2005-05-24
didn't work, i gave all the premissions, :
-rwxrwxrwt  1 michal    6338 2005-05-11 14:17 firefox
-rwxrwxrwx  1 michal 9781136 2005-05-11 14:17 firefox-bin

plus the group etc. that includes all files in the /firefox dir. 
Still i can use sudo and that's it.

i tried backports, but a won't install, will try harder if i can' find out what's wrong with the sudo, but it doesn't make me happy :/

---

