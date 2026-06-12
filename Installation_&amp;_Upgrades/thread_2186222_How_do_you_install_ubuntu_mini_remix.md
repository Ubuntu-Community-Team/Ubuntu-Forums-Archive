---
title: "How do you install ubuntu mini remix?"
date: 2013-11-06
forum: Installation &amp; Upgrades
---

### Post by ali_williams on 2013-11-06
hey guys I am trying to just install a barebones Ubuntu OS is there a way to do this? I know you can boot to it as a livecd but how can you take it from a livecd to a installed OS? any tutorials or suggestions would be helpful :-D

---

### Post by fantab on 2013-11-06
Follow the instructions you get from the text based installer... they are simple to follow.

I wonder what you are doing with "8 GB DDR 667mhz" RAM? That is a very old RAM. Is it a very old computer with only CPU upgraded?
Why do you want to install "barebones Ubuntu OS" and not the regular Ubuntu from DVD/USB?

---

### Post by ali_williams on 2013-11-06
I am trying to do a barebones for a netbook install, but I do not see the text based installer on here. do you know where it is located?

---

### Post by ian-weisser on 2013-11-06
Why "barebones" for a netbook? Does the user want less functionality? Or are you using a (somehow) bloated distro?
With an i7 and 8GB of RAM, resources seem plentiful.

---

### Post by fantab on 2013-11-06
When you say 'barebones', I presume that you mean [mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD"). Am I correct?
If you are getting a command line then at prompt:
```
cli
```

For me, the mini.iso presents a very basic text-based installer to set up the basic system..

Next:
```
sudo tasksel
```

that should give you options to install desktop, if not

```
sudo apt-get install ubuntu-desktop

or

sudo apt-get install xubuntu-desktop

or 

sudo apt-get install lubuntu-desktop

or 

sudo apt-get install kubuntu-desktop
```

If you are a beginner then allow me to recommend you to install from [Ubuntu DVD/USB, a regular Ubuntu]("http://www.ubuntu.com/download/desktop").

---

