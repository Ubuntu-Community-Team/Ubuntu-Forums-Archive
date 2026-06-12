---
title: "New to Linux, so a few questions =]"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by Ensamvarg on 2007-11-14
Hey all,
I'm currently studying a BTEC National Diploma in IT, and for my previous lesson, I installed Ubuntu using VMWare. I was immediately impressed by the visuals, and some of the programs I used. I was just wondering if you could install some of the following programs on it.
MSN Live Messenger
Photoshop
Dreamweaver
Visual Basic 6
EVE Online
Firefox
Thunderbird
And perhaps more I cannot remember.

Also another question, I've been reading that people use Wine for certain uses, what is it and what does it do?

Thanks in advance.

---

### Post by 1/0 on 2007-11-14
First of all. I would install programs that are native Linux ones. Check:

[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)
[http://en.wikipedia.org/wiki/List_of_open_source_software_packages](http://en.wikipedia.org/wiki/List_of_open_source_software_packages)

That doesn't help for the homework. But this might (all from Google btw):

[http://frankscorner.org/](http://frankscorner.org/)
[http://appdb.winehq.org/](http://appdb.winehq.org/)
[http://www.winehq.org/site/about](http://www.winehq.org/site/about)

---

### Post by PmDematagoda on 2007-11-14
Linux is different to Windows, this means that you cannot usually install programs meant for Windows, but you can find the Linux versions of the programs you want or you can use an alternative to the one you want which may be just as good as the one you want or even better.

Now, there are Linux versions for:-

Mozilla Firefox 

Mozilla Thunderbird

Firefox is usually pre-loaded on all Ubuntu flavours except Kubuntu where you can install it from the repositories by typing:-
```

sudo apt-get install firefox
```
into a terminal.

Thunderbird also is found in the repos, you can install it using:-
```

sudo apt-get install thunderbird
```
though even Evolution, which is also usually pre-loaded onto most Ubuntu flavours is also rather good.

Here are the alternatives for the programs you want:-

MSN messenger- aMSN 
```
sudo apt-get install amsn
```

Photoshop- GIMP
This is also pre-loaded on many Ubuntu flavours.

I'm not very sure about the other ones, but you can try using them through Wine. Wine is a Windows compatibility layer for Linux, it cannot be used for every Windows program but can be used for a very good number of applications anyway.

Wine can be installed using:-

```
sudo apt-get install wine
```

One more thing, a lot can be learned simply by googling your questions and doubts, so just have a look around before asking around the forums as there is plenty of information and help to solve your problems:).

---

