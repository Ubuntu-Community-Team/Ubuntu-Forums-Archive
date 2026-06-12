---
title: "How to switch from development to stable?"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by CrimsonRider on 2009-12-02
Hi,

A while back I shifted my install to 

"Ubuntu karmic (devevlopment branch)"

Since Karmic is now out and stable, I wish to switch my install over to Karmic Stable, but for the life of me can't figure out how to do it. I can find upgrade guides for 9.04 to 9.10 but not from 9.10 dev to 9.10 stable.

It's a command line only server install.

Can anyone help point me in the right direction?

---

### Post by phillw on 2009-12-02
> **CrimsonRider said:**
> Hi,

A while back I shifted my install to 

"Ubuntu karmic (devevlopment branch)"

Since Karmic is now out and stable, I wish to switch my install over to Karmic Stable, but for the life of me can't figure out how to do it. I can find upgrade guides for 9.04 to 9.10 but not from 9.10 dev to 9.10 stable.

It's a command line only server install.

Can anyone help point me in the right direction?

If you've been keeping your auto-updates turned on - relax - you're on the release version :-D

If  in doubt  System-->Administration-->Update mananger. 

Regards,

Phill.

---

### Post by CrimsonRider on 2009-12-02
I've been keeping updating, for sure, but I don't have X on this box so I can't check.

lsb_release -a gives: Ubuntu karmic (development branch)

I am running aptitude safe-upgrade now.

thanx for the response

---

### Post by phillw on 2009-12-02
```
uname -a
```should report back that you have kernel -15 if your kernel is upto date. If that's upto date - you're on the latest release !!

> Linux piglet 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux  on my 32 bit system


Phill.

---

### Post by CrimsonRider on 2009-12-02
The update ran fine, it now reports that I am on kernel version 2.6.31-13-server, wich is current.

Also, the lsb_release -a now correctly gives me Ubuntu 9.10 - Karmic

thanx

---

