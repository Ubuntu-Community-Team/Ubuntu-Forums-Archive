---
title: "only partial upgrades and still broken"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by FraggedLocust on 2009-04-10
I try to run sudo apt-get update, and I get warnings like:

W: Failed to fetch [repository]. Could not resolve [http address].

It seems to do this for a bunch of repositories. This error is repeated in the GUI when I run partial updates as well.

---

### Post by alphacrucis2 on 2009-04-10
> **FraggedLocust said:**
> I try to run sudo apt-get update, and I get warnings like:

W: Failed to fetch [repository]. Could not resolve [http address].

It seems to do this for a bunch of repositories. This error is repeated in the GUI when I run partial updates as well.

Maybe try changing your repo's. Which ones are you using?

---

### Post by FraggedLocust on 2009-04-10
It looks like I have an Akirad repository that I don't remember adding in third-party.
I disabled it. let's see if that fixes things.

EDIT: nope. the partial update still crashes.

---

### Post by FraggedLocust on 2009-04-10
I ran:
```
sudo apt-get autoclean
sudo apt-get update
sudo apt-get upgrade

```

and it seems to be working.

---

### Post by FraggedLocust on 2009-04-10
it looks like the partial upgrade is crashing when trying to install the packages. But I do not get a crash report dialogue.

---

### Post by bobnutfield on 2009-04-10
At least one other post has reported the same issue when updating from the GUI, and I am having it as well.  Updating and upgrading from the terminal works just fine.  I am sure the devs are aware and it will be corrected in a future update.

---

### Post by johnnybirdman on 2009-04-10
> **bobnutfield said:**
> At least one other post has reported the same issue when updating from the GUI, and I am having it as well.  Updating and upgrading from the terminal works just fine.  I am sure the devs are aware and it will be corrected in a future update.

I have only used the terminal for updates and got the error.  Oddly enough, I tried the gui and it worked..?? the beta testing continues.

---

