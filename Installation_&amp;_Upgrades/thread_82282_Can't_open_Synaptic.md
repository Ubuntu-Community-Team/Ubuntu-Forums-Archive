---
title: "Can't open Synaptic"
date: 2005-10-26
forum: Installation &amp; Upgrades
---

### Post by valentin.dumitran on 2005-10-26
I just installed 5.10 and I'm having a problem with installing packages.
When I try to start Synaptic It asks me for a password; I tried to enter the root password, but it says "wrong password" so i thought it was asking for my user's password; when I enter that, nothing happens (absolutely nothing...no error, no nothing)
Apt-get seems to work, althow I didn't actualy try to install anything with it.

Can anyone help me with that?

---

### Post by Xian on 2005-10-26
Open a terminal and test a command to see if your passwd is working.
Something like:

$ sudo gedit

---

### Post by valentin.dumitran on 2005-10-26
My password is ok. It was the first thing I tried. I didn't have a lot of time for tests cause It was about 3AM when I finnished installing it and now I'm at work, but I like Ubuntu and I think I'll spend a few hours trying to see what's wrong...

---

### Post by valentin.dumitran on 2005-10-26
I have another ideea. Can anyone tell me how to start Synaptic from a console? I can work as root from the console (I open the console from Gnome) and maybe I can start it like that.
I really don't want to use apt-get as long as I save Synaptic...

---

### Post by aysiu on 2005-10-26
There should be no root password unless you installed in expert mode. 

And if you're able to use apt-get, you should be able to use that same password for Synaptic.

That said, if you want to try Synaptic from the terminal, use the command ```
gksudo synaptic
```

---

### Post by valentin.dumitran on 2005-10-26
I opened a console and I typed:
$ su
It asked for the password, all ok
# apt-get 
works fine
# synaptic (it seemed logical)...and nothing

I installed in expert mode because I also use Win XP and I wanted to be sure the instaler doesn't do something stupid like erasing my partitions...
As I said, right now I'm at work, but when I get home I'll try again...

---

### Post by valentin.dumitran on 2005-10-26
I finally got it working.
For some strange reason sudo gives me that weird "wrong password" error, but if i use su, it works fine.
So to start Synaptic I open a terminal:
$ su
pass...
# synaptic
This works. It still seems weird...but it works.

---

### Post by galleonway on 2005-10-26
I did the same install,  same problem, but I get this: 

"bryan@d207-216-23-217:~$ su
Password:
root@d207-216-23-217:/home/bryan# synaptic
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified"

---

