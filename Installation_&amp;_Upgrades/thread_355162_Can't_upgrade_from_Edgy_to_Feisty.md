---
title: "Can't upgrade from Edgy to Feisty"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by gjtoth on 2007-02-06
Following the instructions provided online, I downloaded the alternative ISO and ran gksu "sh /cdrom/cdromupgrade"

The sequence starts out fine, it shuts off a couple of sources in my list, begins fetching & installing and then pops up with this:

[IMG]http://i86.photobucket.com/albums/k119/gjtoth/Screenshot.png[/IMG]

I click through it and it backs out and that's that.

Anyone got any ideas?

---

### Post by evilc on 2007-02-06
If you want to upgrade from edgy do this in terminal. gksu "update-manager -c -d"

---

### Post by gjtoth on 2007-02-07
> **evilc said:**
> If you want to upgrade from edgy do this in terminal. gksu "update-manager -c -d"

And that gets "could not initiate dbus"

---

### Post by evilc on 2007-02-08
Sorry being late we are having power failures, there is a bug around regarding "could not initiate dbus" do a search and you will see outcome. It may have been resolved now so try your first method again. We have only 30 minutes of power now before it's off again so I will check back when it's back on to see how you went.

---

### Post by gjtoth on 2007-02-08
> **evilc said:**
> Sorry being late we are having power failures, there is a bug around regarding "could not initiate dbus" do a search and you will see outcome. It may have been resolved now so try your first method again. We have only 30 minutes of power now before it's off again so I will check back when it's back on to see how you went.

I reinstalled anything that had to do with dbus.  Then, used the "apt-get" method of upgrading.  It worked!  I'm up to Feisty now.

---

### Post by evilc on 2007-02-08
That's good to hear, I think your problem was linked to the hiccup in one of the updates. Just remember that Feisty is still in dev stage you may get small hiccups occasionally but usually fixed as updates install regulary .

---

### Post by gjtoth on 2007-02-08
> **evilc said:**
> That's good to hear, I think your problem was linked to the hiccup in one of the updates. Just remember that Feisty is still in dev stage you may get small hiccups occasionally but usually fixed as updates install regulary .

Developing or not, I've noticed a MARKED improvement in system speed.  I like the Control Center a lot, too (amongst other very nice improvements and additions)

---

### Post by evilc on 2007-02-08
> **gjtoth said:**
> Developing or not, I've noticed a MARKED improvement in system speed.  I like the Control Center a lot, too (amongst other very nice improvements and additions)

 Glad you like it

---

