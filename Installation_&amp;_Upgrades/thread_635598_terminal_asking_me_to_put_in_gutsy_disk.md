---
title: "terminal asking me to put in gutsy disk"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by hotroddude on 2007-12-08
I just installed gutsy after being killed by the numerous problems ive had in feisty. terminal is giving me a strange error when i try to do certain commands, like right know im reinstalling awn and terminal keeps telling me to do this

```
 Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter 
```

i dont have a gutsy gibbon disk so i cant. im having a troublesome day today lol
all help is greatly appreciated.

thanks in advance,
steven

ps. how do i turn off that spell check type thing that keeps underlining my words?

---

### Post by taurus on 2007-12-08
If you don't want it to keep asking you for the installer CD, edit /etc/apt/sources.list

```
sudo nano -Bw /etc/apt/sources.list
```
and place a # in front of the first line with the cdrom in it to comment it out.  When you are done editing, save it with <Ctrl>o and exit with <Ctrl>x.  Then, run

```
sudo apt-get update
```

---

### Post by yabbadabbadont on 2007-12-08
Start up Synaptic (System->Administration->Synaptic Package Manager) and go to Settings->Repositories.  Uncheck the entry for the cdrom.  Ok the change, then hit the reload button.  It should stop prompting you from then on.

---

### Post by yabbadabbadont on 2007-12-08
> **hotroddude said:**
> ps. how do i turn off that spell check type thing that keeps underlining my words?

In Firefox.  Edit->Preferences->Advanced tab->Check my spelling as I type.  (Uncheck it ;))

---

### Post by hotroddude on 2007-12-08
darn im getting a new error

```
steven@steven-desktop:~$ sudo apt-get update
E: Type 'sudo' is not known on line 67 in source list /etc/apt/sources.list
```

did nothing more than what was told.
thanks for the quick replies

EDIT: nevermind seems to be working, i removed that line taurus asked me to add but kept the "#" thanks for the help.

---

### Post by WearZeeP on 2007-12-08
> **hotroddude said:**
> darn im getting a new error

```
steven@steven-desktop:~$ sudo apt-get update
E: Type 'sudo' is not known on line 67 in source list /etc/apt/sources.list
```

did nothing more than what was told.
thanks for the quick replies

EDIT: nevermind seems to be working, i removed that line taurus asked me to add but kept the "#" thanks for the help.


Hmm.. looks like you messed up something, the thing that you were supposed to do, was to put that first line in the terminal, and then edit the file from there, but you could just do 
```

sudo gedit /etc/apt/sources.list
```

and find the line where is says something about a cd, and comment it out (put a # in front of the text on that line, so apt-get and synaptic wont care about it)

---

### Post by aysiu on 2007-12-09
Your /etc/apt/sources.list is completely messed up.

[Get a fresh sources.list](http://www.psychocats.net/ubuntu/sources#key) and then try again: ```
sudo apt-get update
```

---

