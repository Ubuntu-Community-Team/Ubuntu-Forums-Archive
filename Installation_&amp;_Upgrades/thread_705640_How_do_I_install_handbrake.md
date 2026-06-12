---
title: "How do I install handbrake?"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by bishoy on 2008-02-23
I Am trying to install handbrake on ubuntu 7.10. there isnt a .deb file for it, the only way to install it is using a .tar.gz file and i do not know how to do this. can anyone help please? 
[http://handbrake.fr/?article=download](http://handbrake.fr/?article=download)

---

### Post by Pumalite on 2008-02-23
cd /Desktop
tar xvzf filename.tar.gz
cd filename
make
make install
Take a look at README.

---

### Post by von Stalhein on 2008-04-20
Revive dead thread!!

I'm trying to do the same thing.
I d/l to a directory called "handbrake". It contains nothing but HandBrakeCLI (from the tar.gz file).

After I cd to the above directory and use the next command I get```
 make: Nothing to be done for `HandBrakeCLI'
```

What have I missed here??

---

### Post by jrothwell97 on 2008-04-20
HandBrakeCLI is the program. It's already been compiled for you: all you need to do is cp or mv it to a more convenient place, and then use the terminal to run it.

---

### Post by von Stalhein on 2008-04-20
Thanks for that.

Given that I'm happy where it is, what's the terminal command to start it?

15 minutes Googling and some fiddling in Terminal got me no further :-(

---

### Post by Spartan.II.117 on 2008-04-20
cd (directory)
./handbrakecli

---

### Post by von Stalhein on 2008-04-21
OK, thanks for that, it's sorted now.

---

