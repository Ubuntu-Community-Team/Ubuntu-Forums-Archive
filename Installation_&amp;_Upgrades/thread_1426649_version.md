---
title: "version"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by ale52 on 2010-03-10
I've installed [or at least I thought I did] version 9.10.  That's what I recently downloaded from Ubuntu.com. However when I go to check the installed version [System/About Ubuntu] it tells me this..."Thank you for your interest in Ubuntu 7.10
                - the Gutsy Gibbon - released in October 2007."

Can anyone explain this?

Thanks

Alan <><

---

### Post by howefield on 2010-03-10
Open a terminal, Applications > Accessories > Terminal and type

```
lsb_release -a
```

What is the output ?

---

### Post by Ferb on 2010-03-10
In the terminal

lsb_release -a

then you will see what distro you just installed

---

### Post by ale52 on 2010-03-10
> **howefield said:**
> Open a terminal, Applications > Accessories > Terminal and type

```
lsb_release -a
```

What is the output ?

Distributor ID:  Ubuntu
Description:     Ubuntu 7.10
Release:         7.10
Codename:        Gutsy

---

### Post by howefield on 2010-03-10
Then you have 7.10 ;-)

Which is now end of life and unsupported. Best get something more current..

---

### Post by ale52 on 2010-03-10
> **howefield said:**
> Then you have 7.10 ;-)

Which is now end of life and unsupported. Best get something more current..

"I've installed [or at least I thought I did] version 9.10. That's what I recently downloaded from Ubuntu.com."

---

### Post by howefield on 2010-03-10
I hate to contradict you, but it sure doesn't look like it...

If you want a triple check, what kernel are you running ?

In terminal type

```
uname -a
```

---

### Post by ale52 on 2010-03-10
> **howefield said:**
> I hate to contradict you, but it sure doesn't look like it...  * I agree with you totally.*

If you want a triple check, what kernel are you running ?

In terminal type

```
uname -a
```

Linux ubuntu-shop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU

What baffles me is that I've downloaded it from Ubuntu.com and when putting in the disk on this Ubuntu box it shows as 9.10 :o

---

### Post by howefield on 2010-03-10
That is a "Gutsy" kernel.

There are loads of other ways to determine what version you are running, but it isn't 9.10.

What exactly was the URL you downloaded from ?

---

### Post by ale52 on 2010-03-10
I'll try downloading again and reinstalling.  This has me befuddled.

thanks for your help as I'm sure I'll be back with another boner to figure out.

Alan <>< :KS

---

### Post by ale52 on 2010-03-10
> **howefield said:**
> That is a "Gutsy" kernel.

There are loads of other ways to determine what version you are running, but I'm pretty sure it isn't 9.10.

What exactly was the URL you downloaded from ?

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

