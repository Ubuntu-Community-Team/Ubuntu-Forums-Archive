---
title: "how to clear space by del temp installation data?"
date: 2012-03-13
forum: Installation &amp; Upgrades
---

### Post by jekylhyde on 2012-03-13
Hi
how to clear hdd space by del temp installation data?
is there a way to clear more space?
i cleared the browser cache...
what more?
thanks

---

### Post by gordintoronto on 2012-03-14
sudo apt-get clean

---

### Post by wojox on 2012-03-14
Check out Bleachbit as well. It's in the repo's.

---

### Post by raja.genupula on 2012-03-14
yup +1 to all 
we have two efficiant and good ways 

```
sudo apt-get autoclean
sudo apt-get autoremove 
```

or use bleachbit 

```
sudo apt-get install bleachbit
``` .

---

### Post by jekylhyde on 2012-03-14
> **raja.genupula said:**
> yup +1 to all 
we have two efficiant and good ways 

```
sudo apt-get autoclean
sudo apt-get autoremove 
```

or use bleachbit 

```
sudo apt-get install bleachbit
``` .

what is the difference between autoclean to autoremove ?

oh... & why when i install an app it will not appear in the menu only after i rebbot? 
(& because i can't see bleachbit in the menu - after i installed it - what to write in the console to run it?)

thanks

---

### Post by raja.genupula on 2012-03-14
> **jekylhyde said:**
> what is the difference between autoclean to autoremove ?

oh... & why when i install an app it will not appear in the menu only after i rebbot? 
(& because i can't see bleachbit in the menu - after i installed it - what to write in the console to run it?)

thanks

[http://askubuntu.com/questions/3167/what-is-difference-between-the-options-autoclean-autoremove-and-clean](http://askubuntu.com/questions/3167/what-is-difference-between-the-options-autoclean-autoremove-and-clean)

in terminal type as [COLOR="Blue"]bleachbit[/COLOR] to launch it .

---

