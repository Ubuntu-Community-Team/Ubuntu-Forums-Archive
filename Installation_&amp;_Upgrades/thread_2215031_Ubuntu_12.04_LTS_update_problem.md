---
title: "Ubuntu 12.04 LTS update problem"
date: 2014-04-04
forum: Installation &amp; Upgrades
---

### Post by Nostronna on 2014-04-04
Hello everybody,
I'm using ubuntu 12.04 LTS on a toshiba satellite U920T and recently I'm having a problem with the update.
It shows me the list of available updates but when I click on "install updates" an error message appears and it says 
"CD/DVD 'Ubuntu 13.10_Saucy Salamander_-Release amd64 (20131016.1)' is required"
it needs the cd/dvd to install software packages from it.
Why that? I don't want to upgrade to Saucy Salamander for now, just want to update my existing system.....
Any suggestion?
Thank you,
Michela

---

### Post by Bashing-om on 2014-04-04
Nostronna; Hi !

As a place to start , check and make sure in Ubuntu Software Center -> Other Software (?) that the CD/DVD box is not checked.
 Also/else; take a look at the control file "/etc/apt/sources.list" from terminal. Make sure all references to the CD/DVD are commented out.

 [INDENT]just what 
[INDENT][INDENT][INDENT]I would do
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gifford on 2014-04-05
In Ubuntu software center, under edit is software sources. In software sources in Ubuntu software, make sure the CD/DVD is not checked.
Then under updates, notify me of a new Ubuntu version should be for long-term support versions.

---

