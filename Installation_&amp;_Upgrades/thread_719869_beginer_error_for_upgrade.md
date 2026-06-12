---
title: "beginer error for upgrade"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by syphonbear on 2008-03-09
when I try to install the current updates for gutsy I get use apt-get install -f when I type that in I get an error parse error near 8047 in `/var/lib/dpkg/statu' `adduser': 

`depends' field reference to `passwd': version contains `)' 
E: Sub-process /usr/bin/dpkg returned an error code (2)

I am really slow at linux and terminal please help. 

PS My laptop seems to have a bug from vista that I have not been able to erase is it maybe a hardware issue? an fixable?

Thanks in advance for helping me and my clumsiness

---

### Post by taurus on 2008-03-09
Just post the outputs of these two commands from a terminal.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by syphonbear on 2008-03-09
Apt-get update acted fie then with ap-get upgrade I got

reading package list...Done
Building Depedency tree
Reading state information.. Done
You might want to run 'apt-get -f install -f' to correct these.
the following packages have unmet dependencies:
adduser: Depends: passwd (>= (1:4.0.12) but 1:4.018.1-9 is installed
libgconfigf2.0-cil: Depends moo- r}ntime (>=1.0) but it is not installable
E: Unmet dependcies. try using -f

Thanks again

---

### Post by taurus on 2008-03-09
What happens when you run

```
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by syphonbear on 2008-03-10
same error messages as before.:mad:

---

