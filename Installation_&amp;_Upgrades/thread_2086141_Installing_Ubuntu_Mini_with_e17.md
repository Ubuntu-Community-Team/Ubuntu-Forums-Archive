---
title: "Installing Ubuntu Mini with e17"
date: 2012-11-20
forum: Installation &amp; Upgrades
---

### Post by PremiumG on 2012-11-20
In my quest to built a personally optimized OS, I have decided to give Ubuntu Mini a try! For this, I will be going with 64bit 12.04.

Installation is a breeze. I then log into the Ubuntu command prompt and immediately ```
sudo apt-get update
```After that, I am unable to figure out what to do next, after trying many webpages of tutorials. Do I need to install anything important for the system before installing e17 so I can start using my computer? 

As for installing e17, I tried following the instructions on this website ([https://launchpad.net/~hannes-janetzek/+archive/enlightenment-svn?field.series_filter=precise](https://launchpad.net/~hannes-janetzek/+archive/enlightenment-svn?field.series_filter=precise)) for Precise Pangolin 12.04. The site states to input ```
deb [http://ppa.launchpad.net/hannes-janetzek/enlightenment-svn/ubuntu](http://ppa.launchpad.net/hannes-janetzek/enlightenment-svn/ubuntu) precise main 
deb-src [http://ppa.launchpad.net/hannes-janetzek/enlightenment-svn/ubuntu](http://ppa.launchpad.net/hannes-janetzek/enlightenment-svn/ubuntu) precise main
```and this results from the first entry:```
deb: command not found
```I think I can get programs in the terminal on my own once I get the machine working, for now, I just need help being able to use my machine in e17 desktop.

---

### Post by PremiumG on 2012-11-20
Also, I figured I should put ```
wget http://ppa.launchpad.net/hannes-janetzek/enlightenment-svn/ubuntu precise main
```

---

### Post by Bucky Ball on 2012-11-20
When you say the mini do you mean you are attempting a Ubuntu minimal install using the mini.iso??? As in this:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

If not, then that will let you do a really custom install. ;)

---

### Post by PremiumG on 2012-11-20
> **Bucky Ball said:**
> When you say the mini do you mean you are attempting a Ubuntu minimal install using the mini.iso??? As in this:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

If not, then that will let you do a really custom install. ;)


Yes, now do you know how to fix this deb issue?

---

### Post by Bucky Ball on 2012-11-20
What have you already installed? Anything to deal with deb files?

You need to write a list of everything you are going need and start installing. Easiest would be to start with Synaptics:

```
sudo apt-get install synaptics
```... and a desktop environment, unless you are intending to run wholly from the terminal. I use Xfce:
```

sudo apt-get install xfce4
```I would deal with the essentials before bothering with third-party repos. Those deb lines go into your software sources, not a terminal, per se.

---

### Post by PremiumG on 2012-11-20
> **Bucky Ball said:**
> What have you already installed? Anything to deal with deb files?

You need to write a list of everything you are going need and start installing. Easiest would be to start with Synaptics:

```
sudo apt-get install synaptics
```... and a desktop environment, unless you are intending to run wholly from the terminal. I use Xfce:
```

sudo apt-get install xfce4
```I would deal with the essentials before bothering with third-party repos. Those deb lines go into your software sources, not a terminal, per se.

Well... I am installing e17 as my post title suggests, not Xfce.

---

### Post by Bucky Ball on 2012-11-20
Well, all good then. Use whatever package manager that uses and start installing what you need.

---

### Post by PremiumG on 2012-11-20
> **Bucky Ball said:**
> Well, all good then. Use whatever package manager that uses and start installing what you need.

Yes, that is what I am trying to figure out. Can anyone help me do this for e17?

Once I hit those deb inputs I get that error as suggested earlier... This is my problem.

---

### Post by Bucky Ball on 2012-11-20
Like I said, those lines don't go in a terminal. You need to put them in sources.list, if that exists. I know nothing of E17. Is that a desktop environment or a full OS?

---

### Post by zombifier25 on 2012-11-20
> **Bucky Ball said:**
> Like I said, those lines don't go in a terminal. You need to put them in sources.list, if that exists. I know nothing of E17. Is that a desktop environment or a full OS?

e17, full name Enlightenment version 17, is a lightweight desktop environment.


As for those deb lines, like Bucky Ball suggested, put them at the end of /etc/apt/sources.list . But they provide a PPA, so don't go through the pain of manually editing the file and do this:
```
sudo add-apt-repository ppa:hannes-janetzek/enlightenment-svn
```

---

### Post by PremiumG on 2012-11-20
> **zombifier25 said:**
> e17, full name Enlightenment version 17, is a lightweight desktop environment.


As for those deb lines, like Bucky Ball suggested, put them at the end of /etc/apt/sources.list . But they provide a PPA, so don't go through the pain of manually editing the file and do this:
```
sudo add-apt-repository ppa:hannes-janetzek/enlightenment-svn
```

How do I add it to the end of that though? Also, when I put that command I get
```
sudo: add-apt-repository: command not found
```

---

### Post by Bucky Ball on 2012-11-20
I'm presuming you have apt installed ...

Wben doing the minimal install it is always a good idea to research then make a list of what you are going to need installed prior to beginning. You can then install everything as part of the process. This includes essential stuff, like apt, and apps you use regularly. You will also need gcc somewhere along the line.

---

### Post by QIII on 2012-11-20
Just a note...

Jeff Hoogland over at Bodhi Linux gave some instructions (I think) about how to install E17 in Ubuntu.  Bodhi Linux 2.0 uses E17 and is based on Ubuntu 12.04.

You might have to dig around bodhilinux.com a bit to find it.

---

### Post by PremiumG on 2012-11-21
> **QIII said:**
> Just a note...

Jeff Hoogland over at Bodhi Linux gave some instructions (I think) about how to install E17 in Ubuntu.  Bodhi Linux 2.0 uses E17 and is based on Ubuntu 12.04.

You might have to dig around bodhilinux.com a bit to find it.


Thank you for your straightforward answer, a rare thing to find on linux help forums... I will begin my search once I get off work. Until then, I will have to settle with Bodhi.

---

### Post by zvacet on 2012-11-22
```
sudo: add-apt-repository: command not found
```

That is wrong command.It should be 

```
sudo add-apt-repository ppa:hannes-janetzek/enlightenment-svn
```

EDIT: You can try Bodhi linux if you want.E17 is very well integrated there.

---

### Post by nothingspecial on 2012-11-22
the command add-apt-repository is not included in the mini install

```
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:hannes-janetzek/enlightenment-svn
sudo apt-get update
```

---

