---
title: "how to install desktop on ubuntu server 8.10?"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by se.srikanth on 2008-11-10
I just now installed Ubuntu 8.10 Server. I also have a 8.10 Desktop CD. How do I install ubuntu-desktop making use of the desktop cd and not through internet. I tried,

sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop

but still the installer try to install the ubuntu desktop from the internet repos. can some on help me?:confused:

---

### Post by cariboo on 2008-11-10
Have you tried commenting out all the other repostories in /etc/apt/sources.list? Open the file in nano and put a # at the front of every line starting with deb. at the prompt type:

```
sudo nano /etc/apt/sources.list
```

to save  pres Ctrl-o to exit Ctrl-x. Then run:

```
sudo apt-get update && apt-get install ubuntu-desktop
```

Jim

---

### Post by se.srikanth on 2008-11-11
> **cariboo907 said:**
> Have you tried commenting out all the other repostories in /etc/apt/sources.list? Open the file in nano and put a # at the front of every line starting with deb. at the prompt type:

```
sudo nano /etc/apt/sources.list
```

to save  pres Ctrl-o to exit Ctrl-x. Then run:

```
sudo apt-get update && apt-get install ubuntu-desktop
```

Jim

I will give it a try and post the results.

with warm regards
srikanth

---

### Post by se.srikanth on 2008-11-12
thank you jim. but it says "E: Couldn't find package ubuntu-desktop"
is there anything else i can do?

or should i install desktop first and install server packages individually?:confused:

with warm regards
-srikanth

---

