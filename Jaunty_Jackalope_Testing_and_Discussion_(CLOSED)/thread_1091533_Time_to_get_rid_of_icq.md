---
title: "Time to get rid of icq?"
date: 2009-03-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by eyelessfade on 2009-03-09
Today I got this again: The client version you are using is too old. Please upgrade at [http://pidgin.im](http://pidgin.im). Starting to hate icq. Although 99.9% of the time I use jabber.

---

### Post by TrueTom on 2009-03-09
[http://www.getdeb.net/app/Pidgin]("http://www.getdeb.net/app/Pidgin")

---

### Post by eyelessfade on 2009-03-09
Not for jaunty :)

---

### Post by TrueTom on 2009-03-09
The Intrepid packages work, though (at least for me, including fixing the problem)

---

### Post by freeediver on 2009-03-10
Did not work for me.
Guess I need step by step inst.
I tried the Deb page
selected 32 bit.
I had 4 parts to download after I removed my current pidgin.
I did that.
I was given no order in which to download the updates.
Some needed to be DL'ed before the others and not in order.
Well I did all that and it still does not work.
I also tried the Pidgin main page but cant find a step by step.
I have no idea what to do with a tar.bz2

---

### Post by JohnJackson on 2009-03-10
2.5.5 came through the updates this morning for me. There is a notice about ICQ on the Pidgin homepage.

---

### Post by meborc on 2009-03-10
> **freeediver said:**
> Did not work for me.
Guess I need step by step inst.
I tried the Deb page
selected 32 bit.
I had 4 parts to download after I removed my current pidgin.
I did that.
I was given no order in which to download the updates.
Some needed to be DL'ed before the others and not in order.
Well I did all that and it still does not work.
I also tried the Pidgin main page but cant find a step by step.
I have no idea what to do with a tar.bz2

just remove pidgin pidgin-data and libpurple... then download all the packages related to pidgin from getdeb ... do not "open" just download...

then go to the folder you downloaded them in terminal and use "sudo dpkg -i *.deb" command (installs all deb files in that directory)

then if you get some dependency errors, "sudo apt-get update && sudo apt-get -f install"

---

### Post by volanin on 2009-03-10
> **JohnJackson said:**
> 2.5.5 came through the updates this morning for me. There is a notice about ICQ on the Pidgin homepage.

Do you get the latest pidgin from a repository?
Which one?
:)

---

### Post by JohnJackson on 2009-03-10
> **volanin said:**
> Do you get the latest pidgin from a repository?
Which one?
:)

Standard Jaunty main repo

---

### Post by kcredden on 2009-03-10
Moved it to general help. Sorry

- Kc

---

### Post by freeediver on 2009-03-10
Now MSN quit in Pidgin

---

