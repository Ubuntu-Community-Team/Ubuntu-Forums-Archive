---
title: "operating system problem"
date: 2022-06-14
forum: Installation &amp; Upgrades
---

### Post by zongmans on 2022-06-14
Codes don't work, can't install anything
sudo apt-get install apache2(and many other codes)

---

### Post by tea for one on 2022-06-14
Can you navigate to [https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info) and peruse the information.
Then, if you are happy with the software and its intention, run the script and pop the report in this thread.

---

### Post by The Cog on 2022-06-14
Let's start with sudo apt-get install apache2. Can you post exactly what you typed, and what the response was? Then we can have a look and think about it. 
Copy and paste is much better than posting screenshots for this.

---

### Post by zongmans on 2022-06-14
I'll try later

---

### Post by ubfan1 on 2022-06-14
Did you first run sudo apt-get update ?  Then try your installs.

---

### Post by QIII on 2022-06-14
Just a note about terminology.

"Codes" generally relates to gaming.  It's not a term we use here much.

What you are talking about are "commands".  You issue commands in the terminal.  You don't type codes.

---

### Post by zongmans on 2022-06-15
```
zongmans:~$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 apache2 : Depends: apache2-bin (= 2.4.41-4ubuntu3.11) but it is not going to be installed
           Depends: apache2-utils (= 2.4.41-4ubuntu3.11)
E: Unable to correct problems, you have held broken packages.
```

---

### Post by TheFu on 2022-06-15
As others suggested, 

```
sudo apt-get update
sudo apt-get full-upgrade
sudo apt-get -f install
```

Then you can try installing whatever new packages you like, assuming each of those commands complete without errors. If they have any errors - STOP. DO NOT CONTINUE.  Post the exact command and the error output back here for more advice.

Plus, it is really nice when forum code-tags are used for all terminal input/output.

---

