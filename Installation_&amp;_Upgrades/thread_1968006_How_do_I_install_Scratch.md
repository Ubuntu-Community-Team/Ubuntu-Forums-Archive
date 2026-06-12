---
title: "How do I install Scratch?"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by Zonnebrillie007 on 2012-04-28
I´m new to xubunto, and I have downloaded Scratch. It is in the .deb format. How do I install this on my computer? You can find it on the website _[COLOR=Blue]http://info.scratch.mit.edu/nl/Scratch_1.4_Download[/COLOR]_.

Thanks for your help!
Zonnebrillie007

---

### Post by Toz on 2012-04-28
Hello and welcome to the forums.

You didn't mention what version of xubuntu you are using. There is a PPA available for Natty (11.04) and below, but it hasn't been updated in a year. See: [https://launchpad.net/~scratch/+archive/ppa]("https://launchpad.net/~scratch/+archive/ppa").

To install the "Scratch_1.4.0.1-0ubuntu5_i386.deb" file from that webpage:
1. Download the file
2. From a terminal window:
```
sudo dpkg -i scratch_1.4.0.1-0ubuntu5_i386.deb
```

On my oneiric (11.10) system, there were no dependencies and it installed fine.

---

### Post by Zonnebrillie007 on 2012-04-29
I used the code in the terminal but it didn´t work.
This was the screen I got.

Greets,
Zonnebrilie007

---

### Post by Zonnebrillie007 on 2012-04-29
I installed GDEBI from the ubuntu softwarecentrum on my computer and I installed Scratch succesful on my computer.

Thanks daddy for your help :P
Zonnebrillie007

---

### Post by Toz on 2012-04-29
> **Zonnebrillie007 said:**
> I used the code in the terminal but it didn´t work.
This was the screen I got.

Greets,
Zonnebrilie007

Glad you got it worked out. As a quick note, the reason the command line didn't work is because you forgot the -i parameter.

---

