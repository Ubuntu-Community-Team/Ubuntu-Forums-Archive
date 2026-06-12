---
title: "Synaptic package manager help"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by potterpoole on 2007-05-02
I did somthing stupid with synaptic!!! I was trying to access debian repository and entered a custom canel that has made it imposible for synaptic to load any repository data at all. can anyone help me?

---

### Post by taurus on 2007-05-02
What happens when you run these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by potterpoole on 2007-05-02
E: Type 'http:packages.debian.org/stable/' is not known on line 24 in source lis t /etc/apt/sources.list
E: Type 'http:packages.debian.org/stable/' is not known on line 24 in source lis t /etc/apt/sources.list
E: The list of sources could not be read.

this is the responce I get both times. As you can see I need to deleat line 24 in source list/etc/apt/sources.list but cant find the file im not that good with a TERMINAL or the file browser

---

### Post by taurus on 2007-05-02
There is something wrong with line 24 in your /etc/apt/sources.list.  So, you can edit it

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of line 24 to comment it out.  Then, run

```
sudo aptitude update
sudo aptitude upgrade
```
Or post your /etc/apt/sources.list here.

```
cat /etc/apt/sources.list
```

---

### Post by potterpoole on 2007-05-02
Thanks it works fine now

---

