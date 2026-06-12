---
title: "installing wine with automatix"
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by shickidyshade on 2007-01-10
Hey guys i'm trying to install wine with automatix2 and it responded I have to type something into the terminal but i can figure out what it is

---

### Post by shickidyshade on 2007-01-10
this is the error im getting 
GPG error: [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

---

### Post by scrooge_74 on 2007-01-10
I dont use automatix, but you could do as easily sudo apt-get install wine

---

### Post by arnieboy on 2007-01-10
> **shickidyshade said:**
> Hey guys i'm trying to install wine with automatix2 and it responded I have to type something into the terminal but i can figure out what it is

```
winecfg
```

---

### Post by shickidyshade on 2007-01-10
> **arnieboy said:**
> ```
winecfg
```

This is what i got

```
W: GPG error: http://wine.lowvoice.nl edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems

```

---

### Post by scrooge_74 on 2007-01-10
> **shickidyshade said:**
> This is what i got

```
W: GPG error: http://wine.lowvoice.nl edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems

```

winecfg you will use it after you install wine.  winecfg is the config editor for wine in a GUI so you dont have to edit files manually

---

### Post by kisiyel on 2007-01-10
I get the same key error after I updated to wine to 0.9.29 yesterday. Solved problem with,

$wget [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg)
$gpg --import 387EE263.gpg
$sudo apt-key add 387EE263.gpg

---

### Post by arnieboy on 2007-01-10
Thanks for the link for the key. I was looking around for it myself. Apparently, the wine repos have recently been made GPG secure.

---

### Post by Matt27272 on 2007-01-12
Where would I put in that key listed two posts above me?

---

### Post by Hankers on 2007-01-12
In a terminal window. - Applications/Accessories/Terminal

---

### Post by Matt27272 on 2007-01-12
matt@matt-desktop:~$ $wget [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg)
bash: [http://wine.budgetdedicated.com/apt/387EE263.gpg:](http://wine.budgetdedicated.com/apt/387EE263.gpg:) No such file or directory
matt@matt-desktop:~$ $gpg --import 387EE263.gpg
bash: --import: command not found
matt@matt-desktop:~$ $sudo apt-key add 387EE263.gpg
gpg: can't open `387EE263.gpg': No such file or directory
matt@matt-desktop:~$



This is what happens when I put it in the terminal

---

### Post by Hankers on 2007-01-12
Try the commands without the "$" in front of the commands

wget [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg)
gpg --import 387EE263.gpg
sudo apt-key add 387EE263.gpg

---

### Post by scrooge_74 on 2007-01-12
Still don´t understand why you need the key, I installed wine from wihehq today no problem

---

### Post by abzolutxero on 2007-01-12
woot... thanks for the key, and the howto install it!

---

### Post by kisiyel on 2007-01-14
you'r welcome arnieboy for excellent app, really thanks...

---

### Post by kisiyel on 2007-01-14
> **scrooge_74 said:**
> Still don´t understand why you need the key, I installed wine from wihehq today no problem

I think in order to update from original wine repos in your sources;

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

you need to have the right key.

---

### Post by scrooge_74 on 2007-01-14
Maybe for edgy, in dapper did not ask for it, it only says repos are from unsign source

---

