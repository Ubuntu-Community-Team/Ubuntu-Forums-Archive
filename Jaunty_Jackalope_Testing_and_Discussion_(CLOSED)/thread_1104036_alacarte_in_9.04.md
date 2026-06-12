---
title: "alacarte in 9.04"
date: 2009-03-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mrm48 on 2009-03-23
Hi all,

I cannot access alacarte in 9.04. If I run it from the terminal, this is what I get:

# alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
ImportError: No module named Alacarte.MainWindow

has anyone found a fix for this or is there another way to edit the menu?

Thanks,
Matt

---

### Post by dBuster on 2009-03-23
Do you not have an option in SYSTEM -> Preferences for MAIN MENU?  That is where I make all my changes.

I believe it is preferences, might be system though...  I am at work using unfortunately a windows box...

---

### Post by binbash on 2009-03-23
alacarte command works fine here

---

### Post by Aenima99x on 2009-03-23
Same problem here, can't edit the Main Menu at all.
Running Alacarte from a terminal gives same error as OP.
Right-clicking Main-menu icon and choosing "Edit Menus" does nothing.
Running Main Menu from System\Preferences does nothing. 

Any ideas? :(

---

### Post by Aenima99x on 2009-03-23
Fixed it by reinstalling Alacarte.
[The deb file is here if needed]("https://launchpad.net/ubuntu/jaunty/hppa/alacarte/0.11.10-0ubuntu1")

---

### Post by taavikko on 2009-03-23
> **Aenima99x said:**
> Fixed it by reinstalling Alacarte.
[The deb file is here if needed]("https://launchpad.net/ubuntu/jaunty/hppa/alacarte/0.11.10-0ubuntu1")

There's no need to distribute deb files that way,
since it's available in repositories. And part of an default install
If there's no network connection available, that might be the last resort.


```
sudo apt-get --reinstall install alacarte
```
would have sufficed.

---

### Post by Aenima99x on 2009-03-23
Ummm yeah, hence the phrase IF NEEDED. :roll:

---

### Post by mrm48 on 2009-03-23
Thanks,

Got it working by reinstalling alacarte like was suggested.

---

