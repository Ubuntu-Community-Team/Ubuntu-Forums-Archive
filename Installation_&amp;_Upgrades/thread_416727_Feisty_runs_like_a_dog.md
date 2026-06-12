---
title: "Feisty runs like a dog"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by dannyboy1121 on 2007-04-21
I ran the upgrade for Feisty (from Edgy) on my desktop (the wife will kill me if I mess up the laptop).

The upgrade appeared to run without issue - no error messages and nothing in the messages log to indicate there are any big issues. However - everything runs like a dog. 

All applications seem unresponsive - really laggy to the point where it's un-usable.

Any ideas where I should start to try and resolve the performance problems?

---

### Post by dannyboy1121 on 2007-04-21
I hereby give official permission for someone to fix my fault ...


no really - just a point in the right direction would be cool (sorry for the bump but this forum is like wildfire at the moment).

---

### Post by Rui Pais on 2007-04-21
Hi,
is your cpu at 100%? (you can use top on a terminal to check)

There is a thread around where some people with a lag gnome said that it came back to normal edtting
a line on /etc/hosts from: 
 ```

127.0.0.1       localhost 
127.0.1.1       <your_hostname>
```
to
```
127.0.0.1       localhost <your_hostname>
127.0.1.1       <your_hostname>

```

i never understand how can this had anything to do with speed... but several people swear that it make they gnome fast, so it wont hurts trying.

good luck.

---

### Post by dannyboy1121 on 2007-04-21
I did notice that my cpu seemed to be maxed out - I'll give your suggestion a try and let you know how I get on. Many thanks for responding. :)

---

### Post by dannyboy1121 on 2007-04-21
Just in case someone else searches the site for this - the fix was simple (if a little obscure) -

From the desktop - click SYSTEM -> ADMINISTRATION ->  RESTRICTED DRIVERS MANAGER

It seems that my ATI driver is no longer supported and Feisty and switched it off :confused:  .. so I've switched it back on and my performance is back on track.

---

### Post by Azyx on 2007-04-21
Cheers Azyx

---

