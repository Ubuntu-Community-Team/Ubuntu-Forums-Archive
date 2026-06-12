---
title: "wine for ubuntu without internet"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by hill0093 on 2007-07-05
Have an isolated desktop computer that runs Ubuntu 
for analysis overnight, etc, and have a windows 
program that I would like to install. I am told that
it runs satisfactorily under wine. What wine do I 
download on another computer to install 
on my isolated desktop computer.

---

### Post by dfreer on 2007-07-05
```
sudo apt-get install wine
```

---

### Post by hill0093 on 2007-07-05
I thought that was only for 
computers hooked up to the internet.
But I can try it tonight without if
you think it would work.

---

### Post by dfreer on 2007-07-05
Sorry, didn't understand your original post. So you want to know what you need to download for wine to work on a machine that can't connect to the internet? Ok, here's a useful site:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Here I have already selected the latest version of wine in the official repos, and you can see each package that is required.
[http://packages.ubuntu.com/feisty/otherosfs/wine](http://packages.ubuntu.com/feisty/otherosfs/wine)
Eh, that's a lot of dependencies, I'm sure you will have most of those installed already. Hmmm, I would need to find one of my live CD's and see what packages are needed from a fresh install. I'll see if I can scrounge one up, no promise's though.

EDIT: the other solution is to find a repository on CD/DVD that you can download/buy. However, for just one program it seems kind of like a waste.

---

### Post by Afoot on 2007-07-05
You can find the official (I think) non-repository debs available for download:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

> **dfreer said:**
> Sorry, didn't understand your original post.
"wine for ubuntu without internet". :P

---

### Post by hill0093 on 2007-07-05
I downloaded from 
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
the
wine_0.9.40~winehq0~ubuntu~7.04-1_i386.deb
will try it tonight
Thanks so much.

---

### Post by dfreer on 2007-07-06
> **Afoot said:**
> "wine for ubuntu without internet". :P
I am obviously a tool of a man :P for some reason I never really *read* the thread titles, naively assuming all needed info would be in the post itself lol

You can simply try installing the wine_XXXX_.deb, it'll let you know whether you need other packages. But then you will need to scurry between the machine with internet and the machine without until you get all the needed dependencies (reminds me of my 56K Red Hat days). Having said that, I don't believe wine needs more than a few packages to install correctly. Good luck!

---

### Post by hill0093 on 2007-07-06
I tried the downloaded
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
last night and it completed giving a half dozen fixme
that I don't understand. I don't think my windows 
program installed right.
Can't scurry between computers, so I suppose
I'll have to carry my desktop to the
ethernet for installing wine.

---

### Post by dfreer on 2007-07-06
> **hill0093 said:**
> I tried the downloaded
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
last night and it completed giving a half dozen fixme
that I don't understand. I don't think my windows 
program installed right.
Can't scurry between computers, so I suppose
I'll have to carry my desktop to the
ethernet for installing wine.

It may not work with wine, not all programs do. You can check wine's appdb out and see if anyone has gotten your software to work.

---

