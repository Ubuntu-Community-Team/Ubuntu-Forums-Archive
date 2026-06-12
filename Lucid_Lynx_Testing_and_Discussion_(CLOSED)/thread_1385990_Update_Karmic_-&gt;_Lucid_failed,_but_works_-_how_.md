---
title: "Update Karmic -&gt; Lucid failed, but works - how to check if all is ok?"
date: 2010-01-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ernstblaauw on 2010-01-20
Hi,

I also like to have the latest packages, and thus I updated my laptop from Karmic to Lucid. It correcty downloaded all packages and installed them, but somewhere near the end it failed because there was a problem with localpurge.
However, everything works fine now. Of course, I want to know if all packages are updated to Lucid and/or all old packages are removed. How can I do that?

Thanks for your help!
Ernst

---

### Post by ranch hand on 2010-01-20
Well, you could run;
```

uname -a

```
To see if your kernel upgraded to 2.6.32.

And you could run (should run);
```

sudo dpkg --configure -a

```
to see if anything is not finished.

I would open synaptic and see if it lists any broken packages.

---

### Post by ernstblaauw on 2010-01-20
I;m running the 2.6.32 kernel (just upgraded to -11) and also sudo dpkg --configure -a does not give errors.

I have looked through Synaptic local/obsolete and remove a couple of packages which I did not installed myself and did not have a Lucid version. And with 'aptitude why' I could see why packages are installed.

So, everything works now, no obsolete packages and thus I think everything is correct. Or is it possible some config files are not updated?

---

### Post by ranch hand on 2010-01-20
Sounds to me like you are going to be fine (alpha fine anyway).

Have FUN.

---

### Post by cariboo on 2010-01-20
Just to make sure there are no missing dependencies, run:

```
sudo apt-get -f install
```

---

