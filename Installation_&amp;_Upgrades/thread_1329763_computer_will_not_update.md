---
title: "computer will not update"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by BLOODHOUND11245 on 2009-11-17
hello. i tried to update my computer today and it said


E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


and i dont know what to do........
please help.

---

### Post by mjwilson1313 on 2009-11-17
did you run that command in your teminal

---

### Post by BLOODHOUND11245 on 2009-11-18
well thats the thing i dont know what to enter into the terminal. i havent used the terminal much and im kind of new to ubuntu.

---

### Post by audiomick on 2009-11-18
Hallo.
The terminal is available in the applications menu, under miscellaneous or whatever it is called. I'm afraid my installation is in German, where it is called Zubehör. Any way, the bottom option where all the bits and bobs are.

Edit: It's called accessories, of course. Been here too long, maybe. Seem to be forgetting my native language... :-(

A window will open up with a cursor in it that will look something like this:
mick@ubuntu-desktop:~$
you type in the command from the error message

```
sudo dpkg --configure -a
```

it must be exactly right. The best thing is often to cut and paste. In the terminal you have to paste from the menu. Keyboard shortcuts don't work.

What it means is ( and you should always try and find out what commands mean when you find them in the forums. )

sudo

means "execute as root"

dpkg

is the actual command that will fix up the messed up package

--configure -a

are options about how the command is to be carried out.

Because it start with 'sudo',
you will be asked for a password. This is the one you use to log in.
When it is finished, just close the terminal like any other window.

---

