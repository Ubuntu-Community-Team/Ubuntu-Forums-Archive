---
title: "how to download amsn"
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by DarkenedFear on 2008-04-01
Hi i am new to ubuntu and i dont know the code you got to put in terminal to get programs like aMSN 

can i get that code to enter so i can get it cause i downloaded it from the internet and it gives me a error and i was told that i should download it from there.?

Thanks

---

### Post by terrafire on 2008-04-01
Try

> sudo apt-get install amsn

---

### Post by jrib on 2008-04-01
If you really want to use the command line to install things, read: [https://help.ubuntu.com/community/AptGetHowto](https://help.ubuntu.com/community/AptGetHowto) .  If you just want to install things use Add/Remove or System -> Administration -> Synaptic in your menus

---

### Post by DarkenedFear on 2008-04-01
ok were i downloaded it from the internet how do i uninstall it  it gives me a error when i run the add and remove programs?

---

### Post by DarkenedFear on 2008-04-01
ok were i downloaded it from the internet how do i uninstall it  it gives me a error when i run the add and remove programs?



and also how do i install kmess

---

### Post by jrib on 2008-04-01
Take the time to write proper sentences so we can help you.  I'm not really sure what you just said.

* Explain what you did before
* Explain what you are doing now
* Show us the error you are getting and how you get it
* Try to solve one problem at a time

---

### Post by DarkenedFear on 2008-04-01
ok i opened up add remove programs and tryed to install kMess and its coming up with a error of 


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


can someone help    that error comes up everytime i try to install or uninstall anything

---

### Post by jrib on 2008-04-01
Close all packaging programs, open a terminal, run:
```
sudo dpkg --configure -a
```

---

