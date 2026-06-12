---
title: "Where is the 2.6.32-17.26 kernel?"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Lollerke on 2010-03-23
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/540231](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/540231)
Launchpad says it was released four days ago (March 19),but I don't see it in the update manager, altough I can see it in Synaptic.

---

### Post by ratcheer on 2010-03-23
I was wondering about that, myself.

Tim

---

### Post by timosha on 2010-03-23
Just do an update and you'll have it.

---

### Post by Uncle Spellbinder on 2010-03-23
> **timosha said:**
> Just do an update and you'll have it.

Nope. I did that, they're held back and I still have 2.6.32.16

```
unclespellbinder@lucid:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic-pae linux-headers-generic-pae linux-image-generic-pae
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
unclespellbinder@lucid:~$ 

```

---

### Post by timosha on 2010-03-23
Yep ! I got it 10 minutes ago.

EDIT: but not the pae kernel, the generic one.

---

### Post by _h_ on 2010-03-23
I had to do a sudo apt-get update first and then they appeared in Update Manager.

---

### Post by Uncle Spellbinder on 2010-03-23
Just got it. :D

---

### Post by philinux on 2010-03-23
Boots fine. In fact it's shaved another 5 seconds of the boot time.

20.44 seconds now. Pretty impressive. In karmic I get over 1 minute.

---

### Post by _h_ on 2010-03-23
> **philinux said:**
> Boots fine. In fact it's shaved another 5 seconds of the boot time.

20.44 seconds now. Pretty impressive. In karmic I get over 1 minute.

This new kernel is definitely a HOLY **** kind of reaction.

I went from 34.48 seconds boot time on previous kernel:

[http://img708.imageshack.us/img708/3107/daniellaptoplucid201003.png](http://img708.imageshack.us/img708/3107/daniellaptoplucid201003.png)

To a jaw dropping 18.70 second boot time on the new kernel:

[http://img717.imageshack.us/img717/3107/daniellaptoplucid201003.png](http://img717.imageshack.us/img717/3107/daniellaptoplucid201003.png)

---

### Post by crjackson on 2010-03-23
I'm really having a hard time waiting for this release.  I wish my testing computer hadn't died.

---

### Post by philinux on 2010-03-23
> **crjackson said:**
> I'm really having a hard time waiting for this release.  I wish my testing computer hadn't died.

10gig testing partition ;) You can have it all.

---

### Post by _h_ on 2010-03-23
> **philinux said:**
> 10gig testing partition ;) You can have it all.

This.

Go for it and feel the power. :P

---

### Post by ratcheer on 2010-03-23
This new kernel and everything that came with it seems to have fixed all the issues I have been having. No more disk drive clicking / resetting. System boots quickly and cleanly with plymouth and nvidia proprietary. Excellent!

Tim

---

### Post by libihero on 2010-03-23
it still doesnt show up for me on the update
there is a greyed out kernel update, but it requires a partial update

---

### Post by philinux on 2010-03-23
> **libihero said:**
> it still doesnt show up for me on the update
there is a greyed out kernel update, but it requires a partial update

```
sudo apt-get dist-upgrade
```

As always be careful with that. Check what it wants to do. If in doubt hit the N key.

---

