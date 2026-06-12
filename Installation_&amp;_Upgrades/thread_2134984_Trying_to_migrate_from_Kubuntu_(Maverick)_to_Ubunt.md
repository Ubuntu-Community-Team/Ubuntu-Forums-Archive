---
title: "Trying to migrate from Kubuntu (Maverick) to Ubuntu"
date: 2013-04-12
forum: Installation &amp; Upgrades
---

### Post by Egoista on 2013-04-12
Alright everyone, how are you? I am running into problems with trying to migrate from Kubuntu to Ubuntu, after a lot of Googling, I thought it'd be best to come here and ask what I should do. This is what I ave done so far: 


In terminal:


```
sudo apt-get install ubuntu-desktop
```


and I get this:


```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ubuntu-desktop



```


So I Google'd what I should do after than and so then I tried this:


```
sudo apt-get update
```


and then this this appeared:

```
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

```
which is actually new because before it would just be a bunch of "Failed to Fetch" lines and at the end it stated 404 Not Found so I am guessing that those resources aren't there anymore? 

Anything helps, thanks in advance.

---

### Post by oldos2er on 2013-04-12
Right, Maverick is end-of-life, meaning its repositories have been moved to old-releases. [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by mörgæs on 2013-04-13
There is a solution to the 'lock' problem, but it's better to erase the whole system and install Ubuntu 12.10 from scratch. A long chain of upgrades is bound to fail.

---

