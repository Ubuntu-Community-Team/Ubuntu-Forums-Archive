---
title: "how to solve this error"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by mattsajay on 2007-09-06
I was installing programs (like octave, open ssh, vmware etc)

and keep getting this error:  Could not connect to localhost:4001

can anyone help in pointing out the error. 

I had earlier tried to get the automatix 2 but did not install the packages yet when this error started flashing. 

i have the universe and multiverse repositories enabled. 

my internet connection is working okay, i am posting from the machine having the problems. 

this is the error i get from the command line:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main gcc-3.4-base 3.4.6-5ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

---

### Post by dabl on 2007-09-06
If you attempted to install Automatix, it may have borked up your /etc/apt/sources.list.  You can edit that file in Super User mode by entering in a console ```
gksu gedit /etc/apt/sources.list
```

There is a standardized format for the repository entries in that file -- you should be able to observe what the *universe* and *multiverse* and *security* repositories look like, which is the correct format, and then scroll down to the Automatix entries and delete the one(s) that are screwed up.   :)

---

### Post by mattsajay on 2007-09-07
thanks dabl, that was a helpful hint. 

am up and running. great!

and to be honest, i have not seen such an active support forum! thats guys!

---

### Post by dabl on 2007-09-07
Cool -- glad you're back!  8-)

---

