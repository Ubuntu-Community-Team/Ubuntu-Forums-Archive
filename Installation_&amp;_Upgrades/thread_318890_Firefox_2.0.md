---
title: "Firefox 2.0"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by wildsrv on 2006-12-14
I'm trying to install firefox 2.0 and i can download it and "./firefox" for it to work but it doesn't put it in the menus for Ubuntu. I tried synaptic first but it still has 1.5. Pleas help. Thanks

---

### Post by meng on 2006-12-14
If you've already installed it, then simply use alacarte menu editor to create a new menu item.

---

### Post by Qrk on 2006-12-14
You'll have to add the menu entries in yourself. You can make a new launcher from the menu editor, just have it point to the new Firefox executable.

---

### Post by wildsrv on 2006-12-14
ok great. Is there a standard place things get installed. IE windows is program files? Thanks again.

---

### Post by Qrk on 2006-12-15
Wherever you were when you ran ./firefox is where it is. It all depends on where you installed it.

---

### Post by techstop on 2006-12-15
...I don't think you will need to supply the full path for the menu item, but if you do need to locate the firefox executable then you can run this from the command line;

```

which firefox
```

---

### Post by wildsrv on 2006-12-15
I installed FF 2.0 fine. I guess my question is, is there a "standard" place to install things. I noticed that most of the things that are installed in my box are in the /etc/lib if i remember correctly. And that was from Automatrix and Synaptic. This was the first time I installed some thing with out the apt-get command or others. I am getting better at this but i always have issues finding out what the executable is for every thing or if there is an installer. I know .deb files are installers for Ubuntu but thats the extent of my knowledge.

---

### Post by bulldog on 2006-12-15
Maybe you should take a look in /opt

---

### Post by techstop on 2006-12-15
[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)
[http://www.unix-tips.org/linux-tips/linux-tips/what-are-the-important-standard-directories-and-files-in-linux.html](http://www.unix-tips.org/linux-tips/linux-tips/what-are-the-important-standard-directories-and-files-in-linux.html)

...will explain the general filesystem structure...

As for installation, using apt is the best bet;

[https://help.ubuntu.com/community/AptGetHowto](https://help.ubuntu.com/community/AptGetHowto)

If you don't use apt (ie compile from source) then you need to follow the instructions in the readme that is usually included.

---

