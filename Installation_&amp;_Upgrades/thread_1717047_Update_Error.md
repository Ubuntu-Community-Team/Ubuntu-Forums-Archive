---
title: "Update Error"
date: 2011-03-29
forum: Installation &amp; Upgrades
---

### Post by Smaug95swe on 2011-03-29
Okey today when i started my computer i got an error from the updater saying the Following

Ubuntu 10.10
_________________________________________________________
[SIZE=4]NOT ALL UPDATES CAN BE INTALLED
[SIZE=2]Run a part upgrade to install as many as possible.[/SIZE]

This can be caused by:
[SIZE=3]*[/SIZE]A earlier update that hasent been complete
*Problem with parts of the installed software
*In offical program packages that havent been "?Something?" By ubuntu
*Common changes in a early version of ubuntu
___________________________________
[SIZE=2]So what should i do? Just take Part update?
and do you know what may be the cause of this.
Only thing i installed lately was a "game" from the ubuntu Program central and i havent runned it and i restarted my computer 1 time before this when having it installed.
[/SIZE][/SIZE]

---

### Post by Sean Moran on 2011-03-29
> **Smaug95swe said:**
> Okey today when i started my computer i got an error from the updater saying the Following

Ubuntu 10.10
_________________________________________________________
[SIZE=4]NOT ALL UPDATES CAN BE INTALLED
[SIZE=2]Run a part upgrade to install as many as possible.[/SIZE]

This can be caused by:
[SIZE=3]*[/SIZE]A earlier update that hasent been complete
*Problem with parts of the installed software
*In offical program packages that havent been "?Something?" By ubuntu
*Common changes in a early version of ubuntu
___________________________________
[SIZE=2]So what should i do? Just take Part update?
and do you know what may be the cause of this.
Only thing i installed lately was a "game" from the ubuntu Program central and i havent runned it and i restarted my computer 1 time before this when having it installed.
[/SIZE][/SIZE]


Just a suggestion.  I hope it works, and sorts out the packages:  Open terminal and enter: 

sudo apt-get -f check

The 'F' (-f) is for fix, and the check is just to check your apt packages and dependencies.  It might not fix things, but it only takes a minute.  Not sure what else to suggest.  Good luck.

---

### Post by Smaug95swe on 2011-03-29
This is what it said... (swedish

 Kunde inte erhålla låset /var/lib/dpkg/lock - open (11: Resursen tillfälligt otillgänglig)
 Kunde inte låsa administrationskatalogen (/var/lib/dpkg/). Använder en annan process den?


Eng fail translation

Could not keep the lock /var/lib/dpkg/lock - open (11: the resource is for the moment unuseable
Couldnt lock the administrator catalog (Folder?) (/var/lib/dpkg/). Is another process using it?

Thats all it said nothing else... I tried as root too

---

### Post by mörgæs on 2011-03-29
Try to close all windows and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

does it work?

---

### Post by Enigmapond on 2011-03-29
Just run the partial upgrade and then upgrade again. This happens sometimes when the update is interrupted...I would, however reboot prior and that should release the lock.

---

### Post by Smaug95swe on 2011-03-29
ill try it soon kinda busy soz

---

### Post by Smaug95swe on 2011-03-29
> **mörgæs said:**
> Try to close all windows and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```does it work?

Nope that dindt work just said the samething but instead of adminfolder it said download folder

And my download is so slow its just going 2000B/S i dunno why cuz we have 10mbs and we usualy can download up to 2mb/s and it dont help to change dl location sometimes fast sometimes slow

---

### Post by plucky on 2011-03-31
> Nope that dindt work just said the samething but instead of adminfolder it said download folder

Can you copy and paste the complete error message to the Forum? The English version.

Try from a terminal ```
sudo apt-get dist-upgrade
``` 

It will give a description of what it will try to do,just make sure it doesn't try to un-install your complete Desktop before you give it the go-ahead.

Good Luck

---

### Post by Smaug95swe on 2011-04-01
> **Smaug95swe said:**
> This is what it said... (swedish

 Kunde inte erhålla låset /var/lib/dpkg/lock - open (11: Resursen tillfälligt otillgänglig)
 Kunde inte låsa administrationskatalogen (/var/lib/dpkg/). Använder en annan process den?


[SIZE=3][B]Eng fail translation

Could not keep the lock /var/lib/dpkg/lock - open (11: the resource is for the moment unuseable[/B][B]
Couldnt lock the administrator catalog (Folder?) (/var/lib/dpkg/). Is another process using it?[/B][/SIZE] 

Thats all it said nothing else... I tried as root too

[SIZE=4][COLOR=black]
Look abit above and you find the engtranslation... i highlight it here for you[/COLOR][/SIZE]:lolflag:

---

### Post by plucky on 2011-04-01
Try removing the lock file with ```
cd /var/lib/dpkg/
sudo rm lock
```

If that works,run ```
sudo apt-get dist-upgrade
```

Good Luck

---

### Post by megnetz on 2011-06-23
Hello! I have the same problem. Tried removing the lock but appears to stay and still the same error message.

---

### Post by megnetz on 2011-06-23
sudo apt-get clean gives the same error message.

---

### Post by mörgæs on 2011-06-23
Please describe in all detail what you have tried and post the error messages. It is not clear what 'the same' means.

---

