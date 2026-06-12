---
title: "Internet connection"
date: 2009-02-11
forum: Jordan Team
---

### Post by al3zand3r on 2009-02-11
Hello all,
I am switching to Ubuntu because I am tired of Windows and after familiarizing myself with Ubuntu I find it to be excellent and maximizes my system and its resources.  The only problem I have is obtaining an internet connection.  I have Orange ADSL.  I have tried the instructions in the documentation, but still no connection.  Ideas?  Any help is appreciated.

Sincerely,

Joseph

---

### Post by Uchiha_madara on 2009-02-21
hi .....

to solve your problem do these steps :

1 - open the terminal and type:
> sudo pppoeconf

then do the next steps untils you face a dialog box then..

2 - write your username :
> username@provider

for example :
> ey65@Orange-adsl

3- then type the password.
4 - to continue by select "next" to each dialog.
you can switch if the Connection set Automatically or not.

5- manually :
to set the connection :
> sudo pon dsl-provider;

to unset the connection :
> sudo poff dsl-provider;

---

