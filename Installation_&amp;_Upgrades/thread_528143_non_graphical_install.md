---
title: "non graphical install"
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by edan on 2007-08-17
hi 
i want to install ubuntu fiesty amd 64, i have a nvidia 8800gts and when i try to install i get a blank screen from my understanding this is because of the drivers...
can you help get to the non graphical install?

thnx alot

if anyone have a better solution...

---

### Post by Pumalite on 2007-08-17
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Mark the box below the green sign that says: 'Start Download'.

---

### Post by merlinus on 2007-08-17
Have you tried Safe Video Mode?

Alternate Desktop install cd:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

-merlin

---

### Post by Pumalite on 2007-08-17
Hey Merlin; we have to stop meeting this way. (lol)

---

### Post by edan on 2007-08-18
thnx for your help 
i successfully installed ubuntu with the text based install but when i try to boot all i get is a blank screen....
i have no idea what to do 
thnx ahead

---

### Post by merlinus on 2007-08-18
Can you boot into Recovery Mode and get to a command line?

-merlin

---

### Post by edan on 2007-08-18
yes i can

---

### Post by merlinus on 2007-08-18
Then try this:

```

sudo dpkg-reconfigure xserver-xorg

```
You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:
```

startx

```
or reboot.

This should at least get you to a GUI, then you can search how to install the correct video drivers for your card.

-merlin

---

### Post by edan on 2007-08-18
thanx alot merlinus!!!!
worked perfectly

---

