---
title: "Synaptic Package Manager WON'T Open!!!"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by amaurynieto on 2006-12-23
Hello there friends, I don't know WHAT's going on, but every since I installed
and uninstalled Wine through synaptic, it won't open anymore. It opens, sometimes
says that there's been an error in python, sometimes says nothing, and just 
closes as soon as it opens without any warning of any kind

Please I'm desperate, how can I make this work????

A.

---

### Post by bulldog on 2006-12-23
Try to reinstall synaptic through your terminal```
sudo aptitude install synaptic
```

---

### Post by boondongle on 2007-12-14
I'm having the same problem as the original poster, but I haven't received any error messages. When I try to reinstall synaptic using "sudo aptitude install synaptic," I get the following: 

Reading package lists... Done
Segmentation faulty tree... 0%

And the problem stays the same. Any suggestions?

---

### Post by boondongle on 2007-12-14
Okay, nevermind. I found an answer myself that worked. I used the following:

```
sudo rm /var/cache/apt/*.bin
```

followed by:

```
sudo aptitude install synaptic
```

---

### Post by btolle on 2008-05-03
> **boondongle said:**
> Okay, nevermind. I found an answer myself that worked. I used the following:

```
sudo rm /var/cache/apt/*.bin
```

followed by:

```
sudo aptitude install synaptic
```

Boondoggle,

Thanks. I am running Hardy Heron and had the same problem you had and your 'fix' worked for me also.

---

