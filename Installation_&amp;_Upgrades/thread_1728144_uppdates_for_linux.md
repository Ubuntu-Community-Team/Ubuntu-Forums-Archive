---
title: "uppdates for linux?"
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by xic816 on 2011-04-13
Just wandering if the updates for Linux is interactive with programs and things I do in the system or if it's just like windows where general updates are put out?

R

---

### Post by ChrisWells on 2011-04-13
The update manager updates programs and system files. It tells you in the software centre if updates are supported for the program. Otherwise you have to add it yourself to the update list

---

### Post by xic816 on 2011-04-13
yeah okey, salute

---

### Post by KegHead on 2011-04-13
Hi!

This will work:

lower case only

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

Most likely you'll be asked to restart if your kernel updated!

KegHead

---

### Post by KegHead on 2011-04-13
Hi!

In addition to the info I supplied you earlier;

For Natty 11.04:
sudo apt-get install linux-image -f

Earlier versions;
sudo aptitude install linux-image -f

KegHead

---

### Post by xic816 on 2011-04-19
> **KegHead said:**
> Hi!

This will work:

lower case only

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

Most likely you'll be asked to restart if your kernel updated!

KegHead

what does sudo apt-get dist-upgrade -f do? O.o

---

### Post by sanderd17 on 2011-04-19
```
apt-get dist-upgrade -f
```

will force the update to install a newer versions of ubuntu (in this case the natty beta 2). 

I really don't know why KegHead mentions it. He probably misread your question.

---

### Post by xic816 on 2011-04-19
> **sanderd17 said:**
> ```
apt-get dist-upgrade -f
```will force the update to install a newer versions of ubuntu (in this case the natty beta 2). 

I really don't know why KegHead mentions it. He probably misread your question.

yeah okey, thanks

---

### Post by oldos2er on 2011-04-19
> **sanderd17 said:**
> ```
apt-get dist-upgrade -f
```will force the update to install a newer versions of ubuntu (in this case the natty beta 2). 

I really don't know why KegHead mentions it. He probably misread your question.

 apt-get dist-upgrade does not upgrade to a newer Ubuntu version, it's a "smarter" version of apt-get upgrade. **man apt-get** has all the info on it.

---

### Post by xic816 on 2011-04-21
> **KegHead said:**
> Hi!

In addition to the info I supplied you earlier;

For Natty 11.04:
sudo apt-get install linux-image -f

Earlier versions;
sudo aptitude install linux-image -f

KegHead

This didn't work; For Natty 11.04:
sudo apt-get install linux-image -f

---

### Post by tgm4883 on 2011-04-21
> **oldos2er said:**
> apt-get dist-upgrade does not upgrade to a newer Ubuntu version, it's a "smarter" version of apt-get upgrade. **man apt-get** has all the info on it.

Correct, it does not upgrade to a newer Ubuntu version. I'm not sure I'd say it's a smarter version though. Basically the difference between 'upgrade' and 'dist-upgrade' is that 'dist-upgrade' is allowed to install and remove packages based on new dependencies/conflicts. If there are new dependencies/conflicts and you use just 'upgrade' then you will have packages that are held back.

---

