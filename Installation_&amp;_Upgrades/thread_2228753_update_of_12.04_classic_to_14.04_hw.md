---
title: "update of 12.04 classic to 14.04 hw?"
date: 2014-06-09
forum: Installation &amp; Upgrades
---

### Post by ottosykora on 2014-06-09
I have number of computers running the 12.04lts, but all have in addition to the normal unity also the classic front installed and are all operated and used with the classic dektop.

OK, now the 14 was released, so I have to update sometimes.

How does this work? Will I be simply prompted by the regular update and will this go by itself?

So far I have ticked in the update sources that I should be prompted when next lts version is available.
I was not prompted so far.

Will the classic desktop also be updated or is it the completely lost?

---

### Post by Bucky Ball on 2014-06-09
Everything should be upgraded. At the point release, I think sometime in July, you will be offered 14.04 LTS when you run Update Manager. It will be at the top of that screen. 

You can also update via the terminal by following the instructions here:

[http://www.omgubuntu.co.uk/2014/04/upgrade-ubuntu-14-04-12-04](http://www.omgubuntu.co.uk/2014/04/upgrade-ubuntu-14-04-12-04)

You might want to run these commands to make sure your current install is up to date first, though:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Then:

```
sudo update-manager -d
```

If these are production machines I'd wait for the point release, personally. Actually, I'd wait for another year as 12.04 LTS suits my purposes and is rock solid for me. As I need it to be. I fiddle around with 14.04 installed on another partition and will eventually just 'migrate' and start using it permanently. ;)

---

### Post by ottosykora on 2014-06-09
Ah, OK then will first wait til July, by then the first bugs might be cleared and then might try on one of the machines. and see what happens.
Simply hope that the classic setup I have with so much work installed on all machines will somehow survive.

---

### Post by Bucky Ball on 2014-06-09
> **ottosykora said:**
> 
Simply hope that the classic setup I have with so much work installed on all machines will somehow survive.

Do a complete backup of the partition using Clonezilla to make sure you can reinstall if it doesn't:

[http://clonezilla.org/](http://clonezilla.org/)

---

