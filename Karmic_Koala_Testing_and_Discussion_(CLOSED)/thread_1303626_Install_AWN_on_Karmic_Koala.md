---
title: "Install AWN on Karmic Koala"
date: 2009-10-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by razorboy5 on 2009-10-28
Hi

Did anyone successfully install AWN on 9.10?
I'm trying to install by using software centre

it install fine but when i run it will not show up

is there some packages needed to run that i'm missing possibly?

thx

---

### Post by Giblet5 on 2009-10-28
It works fine.

Eliminate your configuration as the cause by creating a new user. logging off, then logging in as that user.

Turn on compiz and test AWN.

Does AWN work for the new user? If so, then your config is somehow conflicting with AWN.

---

### Post by darco on 2009-10-28
AWN is fine w/KK...are you receiving any error messages? Are your running a composite manager (ccsm)? You have visual effects enabled?

darco

---

### Post by prem1er on 2009-10-28
> **Giblet5 said:**
> It works fine.

Eliminate your configuration as the cause by creating a new user. logging off, then logging in as that user.

Turn on compiz and test AWN.

Does AWN work for the new user? If so, then your config is somehow conflicting with AWN.

+1 I had it working a couple of weeks ago with the beta's. So far, none of the updates have broken it. Haven't tried on a fresh install.

---

### Post by razorboy5 on 2009-10-28
Well visuals on extra

compiz is on, at least i'm assuming it is becuz desktop cube works along with a few other compiz stuff

did a reinstall of awn but now
when i go System>Pref>AWN nothing pops up

---

### Post by razorboy5 on 2009-10-28
> **Giblet5 said:**
> It works fine.

Eliminate your configuration as the cause by creating a new user. logging off, then logging in as that user.

Turn on compiz and test AWN.

Does AWN work for the new user? If so, then your config is somehow conflicting with AWN.

followed these steps
does not work in the other user as well

---

### Post by Giblet5 on 2009-10-28
> **razorboy5 said:**
> followed these steps
does not work in the other user as well

Try starting it from a terminal window: ```
avant-window-navigator
```

Post any errors it prints to the terminal window.

---

### Post by razorboy5 on 2009-10-28
ran the code however it said it was not installed
as it clearly shows on Software Centre it was installed...

i'll install using

sudo apt-get install avant-window-manager

in terminal and report back :P

---

### Post by prem1er on 2009-10-28
You should 

```
sudo apt-get --purge remove avant-window-manager
```

before you try to reinstall again.

---

### Post by razorboy5 on 2009-10-28
thx for all the help
by removing it and installing it using terminal i got awn working

however i still cannot get AWN Manager open, i click on the button and just nothing happens... will mark it solvedmthou thx

---

