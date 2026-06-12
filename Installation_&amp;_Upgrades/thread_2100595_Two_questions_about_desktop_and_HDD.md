---
title: "Two questions about desktop and HDD"
date: 2013-01-02
forum: Installation &amp; Upgrades
---

### Post by PaulClarke on 2013-01-02
Hello,

Just returning after a couple of year using Mint.  I have both installed and considering my options.

HDD

Since installing Ubuntu I have noticed that even when idle the HDD is constantly going burr bur like it is reading or writing but it does it every few seconds  - all the time!!  and is annoying.  Any ideas?

Desktop

Like a lot I am not sure about Unity.  The only part that really annoys me is having the drop down menus at the top of the screen.  Can that be changed so they stick to their window?

Lastly can the top bar be moved to the bottom but this is not a biggie.

Regards

Paul

---

### Post by dino99 on 2013-01-02
is hdparm installed ?

[http://askubuntu.com/questions/123744/disks-constantly-spinning-no-matter-what-i-do-jbd2-im-on-the-brink-of-insani](http://askubuntu.com/questions/123744/disks-constantly-spinning-no-matter-what-i-do-jbd2-im-on-the-brink-of-insani)
[http://askubuntu.com/questions/39760/how-can-i-control-hdd-spin-down-time](http://askubuntu.com/questions/39760/how-can-i-control-hdd-spin-down-time)

About unity and else, i think its a bad idea to change the default settings (as its still a work in progress); but if you want to fight against conflicts & unexpected troubles, then its the way to go.

As some users prefer the gnome2 style, then have a look at alternatives like UGR, Lubuntu, cinnamon, ...

---

### Post by PaulClarke on 2013-01-03
Hello and thank you for the reply.

That seemed help but not completely.  Now it is only at the annoying level.

How come this doesn't happen in Mint?

Regards

Paul

---

### Post by vanadium on 2013-01-03
> **PaulClarke said:**
> Hello,

Desktop

Like a lot I am not sure about Unity.  The only part that really annoys me is having the drop down menus at the top of the screen.  Can that be changed so they stick to their window?

```

sudo apt-get autoremove indicator-appmenu appmenu-gtk appmenu-gtk3 appmenu-qt

```
Although I like the global menu, I currently disabled it because Alt+menu hotkeys for libreoffice do not work with the global menu. Anyway, I like Unity also without global menu, and it is perfectly stable.

To reverse: "sudo apt-get install" the same packages.

> 
Lastly can the top bar be moved to the bottom but this is not a biggie.

No. You need to take Unity somewhat as it was designed. For a more configurable desktop environment, one must move to gnome classic or xubuntu.

---

