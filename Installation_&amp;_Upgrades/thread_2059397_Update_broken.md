---
title: "Update broken?"
date: 2012-09-17
forum: Installation &amp; Upgrades
---

### Post by Richard Flisrand on 2012-09-17
I am a Windows support person and have received an Ubuntu computer with and installation problem. The computer has an AMD Athlon 3400+ with 2GB RAM and has been running Ubuntu 12.04 LTS 64bit.

There has been an (unidentified) error when Ubuntu finishes loading. I tried to install available updates (about 350+). It hung part way through and now has an "update broken" error message.

I'm thinking of re-installing Ubuntu.

Recommendations?

Thanks . . ****

---

### Post by jerrrys on 2012-09-17
Try this first

[open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo apt-get update

And post any errors

---

### Post by irv on 2012-09-17
You can also try installing Synaptic package manager by opening a terminal and typing:
```
sudo apt-get install synaptic
```
Then open synaptic packager manager and go to custom filters and select Broken and remove all broken packages and then do the update upgrade.
[ATTACH]224299[/ATTACH]

---

### Post by jerrrys on 2012-09-17
> **irv said:**
> You can also try installing Synaptic package manager by opening a terminal and typing:
```
sudo apt-get install synaptic
```Then open synaptic packager manager and go to custom filters and select Broken and remove all broken packages and then do the update upgrade.
[ATTACH]224299[/ATTACH]

sudo apt-get install -f  :confused:

---

### Post by irv on 2012-09-18
> **jerrrys said:**
> sudo apt-get install -f  :confused:
I typed in 
```
sudo apt-get install synaptic
```
and it worked for me?

EDIT: maybe try it this way:
On the terminal type in the following commands (one line at a time) >>

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install synaptic
```

---

### Post by Richard Flisrand on 2012-09-18
Thanks gurus . . I did need the -f addition, then updates were all installed. 

**sudo apt-get update
**sudo apt-get upgrade

Now the start-error is gone.

Much appreciated!

---

