---
title: "How do you set up all the packages again?"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by hoppipolla on 2011-10-13
When doing it's upgrade, Ubuntu seemed to break and fail to do the Cleaning Up phase.

It all seems to be working completely fine, but just to be on the safe side I was wondering if I could run a command to set up all it's packages again (you know the one I mean, so that it just sets them up without reinstalling them or anything like that).

I just can't for the life of me remember the command! I'm sure I'm not imagining this lol


Thanks a lot guys, 11.10 overall seems really cool!


Hoppi!

---

### Post by varunendra on 2011-10-14
Not sure, but perhaps it would be:
```
sudo apt-get clean
sudo apt-get autoremove
sudo dpkg --configure -a
sudo apt-get install --fix-broken
```

Perhaps it is only the third command you need. I would like see if somebody can confirm this or suggest correct ones.

---

### Post by hoppipolla on 2011-10-15
Spot on varunendra!

I ran all those commands just because the others are always good to run as well every so often I think, but I think the key commands here are

```
sudo dpkg --configure -a
```

To configure all packages not previously configured.

```
sudo dpkg-reconfigure -a
```

To reconfigure ALL packages.



I did try the second command but it seemed a bit overkill, looked like it was going to be there AGES and kept asking me questions for the default set-up of packages (even core packages) so I decided to chicken out and just configure packages that aren't set up yet with the first command!!

So... yeah that's it! Solved! Thank you muchly!

---

### Post by varunendra on 2011-10-15
Glad it worked, and thanks for the appreciable feedback :)

---

