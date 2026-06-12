---
title: "Unable to get packages"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by thinhhoang on 2011-10-14
Hello there. I've just installed Oneiric and now I'm having some serious problem with installing new packages including build-essential, adobe-flashplugin, fpc... I've tried googling around, but it didn't help much.
```

thinhhoang@ubuntu:~$ sudo apt-get install build-essential
[sudo] password for thinhhoang: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 build-essential : Depends: g++ (>= 4:4.4.3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```
Sorry about my English.
Please help me!!! btw I'm not an experienced user so forgive me if there is any mistakes.

---

### Post by thinhhoang on 2011-10-20
I think it's been a while and it's time to go for a bump. Without build-essential, I am not able to compile my homework.

---

### Post by raja.genupula on 2011-10-20
```
sudo apt-get install -f
sudo apt-get update
sudo apt-get install build-essential
```

do them one by one and let me know what you got.
All the best.

---

### Post by thinhhoang on 2011-10-25
Thanks for your reply, I've tried those commands but that didn't work. I accidentally find out that my chosen server is not well-synchronized with the main server, so I can't download some packages, even they appear in the list. I switch to Main Server but it is painfully slow since I'm very far away from it.

---

