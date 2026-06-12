---
title: "Missing and removed packages after upgrade"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by Simoo on 2011-01-15
Hi,

I just upgraded an Ubuntu box from 9.10 to 10.10 using the Alternate CDs. I upgraded 9.10 fully using the internet first, then one after the other, ran the upgrades from the CDs.

Unfortunately it looks like the upgrade procedure has made a bit of a mess regarding packages and I am hoping someone can help me understand what went on.

When all was finished, Evolution had been removed completely and new features of 10.10 such as the 'me-menu' and packages like 'indicator-me', 'indicator-session' were not installed.

I managed to install some of what I knew was missing myself but I am concerned that not all Ubuntu 10.10 packages are there.

Why has this happened and how can I make sure I am left with a 'proper' or 'default' 10.10 install?

Thanks

---

### Post by sikander3786 on 2011-01-15
In order to see if there are any broken packages/dependencies, run these commands.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get dist-upgrade
```

Make sure your /etc/apt/sources.list contains entries for Maverick only or you might run into further problems.

---

### Post by Simoo on 2011-01-20
Delete me

---

### Post by Simoo on 2011-01-20
Thanks for those useful commands

I made sure that Maverick was the only repo listed in /etc/apt/sources.list then ran all four of them.

None of them actually did anything which I guess is a good thing as it would suggest that the system is a fully updated Maverick install.

However, I'm suspicious that is not the case as it would mean that the 3 or 4 packages that I happened to realise were missing and know how to install were, coincidently, the only ones missing...

Basically I'm not convinced everything is installed properly after the upgrade. It may be unrelated but the 'Login Screen Settings' GUI does not function properly now either. I wanted to set it to automatically login as a specific person and the changes I make have no effect and there are also no users in the drop down menu.

I realise this is probably not going to be fixed easily, just thought I should report back. 

Thanks :)

---

