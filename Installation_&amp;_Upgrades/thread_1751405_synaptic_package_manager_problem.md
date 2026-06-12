---
title: "synaptic package manager problem"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by swaroopkanuru on 2011-05-06
when i tried to open synaptic package manager in ubuntu 11.04 i am getting this error


E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by matt_symes on 2011-05-06
Hi

Open a terminal and type

```
sudo rm -rf /var/lib/apt/lists/*
```

Enter your password. It will not be echoed to the screen. This is normal. Then type

```
sudo apt-get update
```

Kind regards

---

### Post by swaroopkanuru on 2011-05-06
thanks a lot my problem get solved :D:)

---

### Post by Vebea on 2011-05-07
I had this problem too and did as** matt_symes **said...but it says to me: 
Building old list of packages... [done]
Building old list of available updates... **Error: No information about packages! (Maybe no deb entries?)**
[done]
Building old list of watched packages... [done]
E: **Lists directory /var/lib/apt/lists/partial is missing.**

what should I do now?

---

### Post by matt_symes on 2011-05-07
Hi

Try this

```
sudo mkdir /var/lib/apt/lists/partial
```

Enter your password. It will not be echoed to the screen. This is normal.

Then type

```
sudo apt-get update
```

Kind regards

---

### Post by Vebea on 2011-05-07
it worked...^.^ Thanks a lot!

---

