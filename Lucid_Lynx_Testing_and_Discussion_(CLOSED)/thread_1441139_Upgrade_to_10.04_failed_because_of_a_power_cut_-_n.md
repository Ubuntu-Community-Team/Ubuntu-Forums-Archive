---
title: "Upgrade to 10.04 failed because of a power cut - now boots to command line only"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by MachaHack on 2010-03-28
I was upgrading Ubuntu to 10.04, when a tripswitch tripped, cutting power to the computer. When it was restarted, it booted into a command line prompt. Google tells me to try:

sudo dpkg --configure -a
This gets me a lot of output that ends with a list of packages. I can't tell you what the output is, as piping the output to more/less does not work (still just all scrolls by and moves to next prompt), and redirecting it to a file just results in an empty file.

Google also suggested:

sudo apt-get install -f
This also didn't work.

Is a fresh install the only solution at this point?

---

### Post by Sef on 2010-03-28
Moved to Lucid.

---

### Post by MachaHack on 2010-03-28
Umm, isn't the target of the update somewhat irrelevant to the problem here? It's the process of upgrading being interrupted that caused the problem, not the specific upgrade.

---

### Post by cariboo on 2010-03-28
Can you start in recovery mode and drop to a root prompt with networking and try:

```
apt-get -f install
```

again? You may have to run:

```
apt-get update
```

before any packages are installed.

---

### Post by sdowney717 on 2010-03-28
hpw about just this from command line.
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by kansasnoob on 2010-03-28
Try:

```
sudo apt-get clean
```

Then check your sources.list:

```
cat /etc/apt/sources.list
```

If it all says "Lucid" (other than the CD source) go ahead and try to just update/upgrade:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

If the sources.list still shows some Karmic we better have a look at that.

---

### Post by nanog on 2010-03-28
unless your upgrade died at the very beginning your sources should be fine. but it should be noted that checking /etc/apt/sources.list is not sufficient. you now should also examine files in:
[php]/etc/apt/sources.list.d/[/php]

if dpkg --configure -a and apt-get install -f worked then you just need to make sure ubuntu-desktop is installed (sudo apt-get install ubuntu-desktop) and issue a start command (sudo /etc/init.d/gdm start). (failed upgrades often result in broken x and/or broken gdm)

see my sig for useful commands. if you cannot get error output in your boot shell then follow instructions for chrooting in my sig. this will give you a full terminal environment which makes troubleshooting easier.

---

### Post by MachaHack on 2010-03-29
None of this worked. So I just did a fresh install.

---

### Post by nanog on 2010-03-29
Actually, chrooting would have worked. You can even replace and configure ever package in a chroot environment,

---

