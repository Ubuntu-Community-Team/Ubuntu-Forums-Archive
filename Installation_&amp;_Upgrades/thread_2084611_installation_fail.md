---
title: "installation fail"
date: 2012-11-15
forum: Installation &amp; Upgrades
---

### Post by Tonybarracuda on 2012-11-15
it get stuck and it wont install, am using the windows installer, ubuntu desktop; and is a small intel cpu d2500 netbook

---

### Post by Tonybarracuda on 2012-11-16
i try with the kubunto installer and i get no video, just a blck screen with a mouse cursor on....

---

### Post by Tonybarracuda on 2012-11-16
still cant make it work

---

### Post by dannyboy79 on 2012-11-16
sounds like a graphics card module issue. sometimes ubuntu has a tough time distinguishing what graphics card driver to use.

can you hit ctrl-alt-f1 to get to the tty1 terminal session? 
enter this command to see what graphics card you have
```
lspci | grep VGA
```

---

### Post by Tonybarracuda on 2012-11-18
Cant press control alt f1, nothing happens...

---

### Post by Tonybarracuda on 2012-11-18
It gets stuck in there

---

### Post by mlentink on 2012-11-18
It would help if you could provide a bit more information like e.g.:

[LIST=1]
[*]is there already an operating system installed? If so, which one?
[*]Which version of Ubuntu are you trying to install?
[*]What are you using to install it? CD? USB-stick?
[*]Have you tried starting up with the live-CD/Live-USB and if so, what were the results?
[/LIST]

Please help others in helping you.
EDIT: Sorry, was a bit to quick: It seems you ahve Windows installed, and are trying to install through Wubi, is that correct?

Please try and start up the Ubuntu Live environment to see if there could be any hardware issues.

---

### Post by Tonybarracuda on 2012-11-18
From windows 7, am using the windowds installer wubi.exe am installing the latest version, it downloada automaticly. 
I got no option to start as livecd

---

### Post by Tonybarracuda on 2012-11-18
I cant start nothing, it just get stuck. I try to reinstall 3 or 4 times, it doesnt get better

---

### Post by mlentink on 2012-11-18
PLease download from here [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) (read the instructions) to create a Live-USB. Boot with that and see if Ubuntu starts at all. It will boot up in an environment that lets you try out Ubuntu without messing with your current system, so you can check for compatibilities.

---

### Post by Tonybarracuda on 2012-11-18
It boots untill here, then it dies

---

### Post by Tonybarracuda on 2012-11-18
nothing from no one ?

now the wubi wont even start; cant even remove the ubunto failed installation.

this installation system is even worst than windows

---

### Post by mlentink on 2012-11-19
> **Tonybarracuda said:**
> It boots untill here, then it dies

What boots until there? Are you sure you booted the Live-CD? I have never seen those messages when booting from the Live-CD or USB

> **Tonybarracuda said:**
> nothing from no one ?

now the wubi wont even start; cant even remove the ubunto failed installation.

this installation system is even worst than windows

AFAIK you can uninstall a Wubi install from the Windows configuration center or whatever it is called. You obviously cannot uninstall it from within the wubi install itself...

---

