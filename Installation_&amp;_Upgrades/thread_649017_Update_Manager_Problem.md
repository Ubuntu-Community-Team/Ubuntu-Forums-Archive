---
title: "Update Manager Problem"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by blueberry17 on 2007-12-24
Hi! I have updates in the Update manager available, but when I click install updates, I get an error saying:

> Could not apply changes! Fix broken packages first.

How do I fix these broken packages so that I can get the updates?

---

### Post by PmDematagoda on 2007-12-24
Do:-

```
sudo apt-get install -f
```

That can fix your problem.

---

### Post by blueberry17 on 2007-12-24
that didn't work

---

### Post by PmDematagoda on 2007-12-24
Could you please post the complete error you got?

---

### Post by blueberry17 on 2007-12-24
Just this window saying:
[B]
Could not apply changes!
Fix broken packages first.[/B]

With a close button for the window

---

### Post by PmDematagoda on 2007-12-24
Open Synaptic, then select Status in the left-hand side column, after that select Broken, after that, could you post the package names that are shown to be broken?

---

### Post by blueberry17 on 2007-12-24
There is no "broken" category under status, but there is under custom filters. In custom filter's broken, there are no broken packages listed.

---

### Post by PmDematagoda on 2007-12-24
Try:-
```
sudo apt-get update
```
and
```

sudo dpkg --configure -a
```
then see if the problem is solved.

---

### Post by bapoumba on 2007-12-24
Please post your sources.list:
```
cat /etc/apt/sources.list
```
and the error to:
```
sudo apt-get update
```

---

### Post by blueberry17 on 2007-12-24
in the terminal when I typed sudo apt-get update, this was the error:

>  GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783


And it said that I could try apt-get update to correct the problem, but that didn't work.

---

### Post by PmDematagoda on 2007-12-24
What guide did you follow to get the Medibuntu repositories?

---

### Post by blueberry17 on 2007-12-24
Oh, never mind! I just unchecked some unnecessary repositories in Synaptic and it solved the problem. Thanks for your help anyway!

---

### Post by PmDematagoda on 2007-12-24
Then it seems that your Medibuntu repository maybe the one that caused the problem, follow this [guide]("http://www.medibuntu.org/repository.php") on how to add the Medibuntu repositories properly.

---

