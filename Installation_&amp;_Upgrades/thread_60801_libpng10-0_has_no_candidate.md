---
title: "libpng10-0 has no candidate"
date: 2005-08-29
forum: Installation &amp; Upgrades
---

### Post by pisuke on 2005-08-29
Hi, sorry if this is a newbee question, but:

While trying to install mattricks (an app for hattrick online game)

$ sudo dpkg -i mattricks_0.7-1_all.deb

says that libwxgtk2.4-python is not installed, so:

$ sudo apt-get install libwxgtk2.4-python

but, says 
This packages had unsatisfied dependcies
  libwxgtk2.4-python: Depends on: libwxgtk2.4 (>= 2.4.2.6ubuntu1) but wouldn't be installed, so:

$sudo apt-get install libwxgtk2.4

And then it says:

  libwxgtk2.4: Depends on: libpng10-0 (>= 1.0.18) but its not installable
E: Broken packages if i try with

$sudo apt-get install libpng10-0

says that libpng10-0 has no installation candidate  :???: 

Any clue on what can i do?

Thank you so much.

---

### Post by pisuke on 2005-08-29
[QUOTE=pisuke]Hi, sorry if this is a newbee question, but:

While trying to install mattricks (an app for hattrick online game)

$ sudo dpkg -i mattricks_0.7-1_all.deb

says that libwxgtk2.4-python is not installed, so:

$ sudo apt-get install libwxgtk2.4-python

but, says 
This packages had unsatisfied dependcies
  libwxgtk2.4-python: Depends on: libwxgtk2.4 (>= 2.4.2.6ubuntu1) but wouldn't be installed, so:

$sudo apt-get install libwxgtk2.4

And then it says:

  libwxgtk2.4: Depends on: libpng10-0 (>= 1.0.18) but its not installable
E: Broken packages if i try with

$sudo apt-get install libpng10-0

says that libpng10-0 has no installation candidate  :???: 

Any clue on what can i do?

Thank you so much.[/QUOTE]
 Answering my own question:

After my last $sudo apt-get update

libpng10-0 and all other dependencies had been resolved and installed.

But now i have another problem i can't solve (i'm not very clever i know)

 mattricks depens on python (<< 2.4); but*:
 python version on system is 2.4.1-0ubuntu2

What i understand about that is I have a newer python that the one needed by mattricks.

What can I do?

---

