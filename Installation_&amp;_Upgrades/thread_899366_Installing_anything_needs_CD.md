---
title: "Installing anything needs CD"
date: 2008-08-24
forum: Installation &amp; Upgrades
---

### Post by Stoodle on 2008-08-24
Every time I try to install something, it asks me to place the LiveCD in with 8.04 on it. I didn't need to do that until upgrading to this version from feisty. It's taunting me because my CD doesn't work now I've upgraded. The button's always been a little messed up so to turn it on, I'd go to terminal and type eject. I get this:
```

eject: tried to use `/dev/hdc' as device name but it is no block device
eject: unable to find or open device for: `cdrom'

```I have to open it with the little hole on the outside. I opened that but it didn't recognize the CD when I was trying to install something. Why do I need it all of the sudden?

Now I'm getting
```

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```I don't even know why...

---

### Post by wannadumpwindows on 2008-08-24
Open up the synaptic package manager, and go to settings >> repositories and then uncheck the cd-rom. That'll take care of the cd issue.

And for the other one, you probably have another update process running, you can only run one at a time. Close the other one, and then try again.

---

### Post by Joeb454 on 2008-08-24
Check System &#8594; Administration &#8594; Software Sources

And make sure your CD isn't listed/enabled as a software source :)

---

### Post by Stoodle on 2008-08-24
Doh! Thanks guys! I thought that by adding it, it'd give me the choice to read from CD but not the obligation.

---

### Post by Joeb454 on 2008-08-24
It'll always check. I thought it would work that way once...I soon learnt ;)

---

### Post by wannadumpwindows on 2008-08-24
> **Stoodle said:**
> Doh! Thanks guys! I thought that by adding it, it'd give me the choice to read from CD but not the obligation.

No problem. The CD is more for adding new programs when you don't have an internet connection. Just in case you ever need to.

It does come in handy now and then when you have a stubborn machine that doesn't wanna connect . . . .

---

