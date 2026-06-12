---
title: "broken synaptic package manager please help"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by specter51095 on 2010-02-08
yesterday my computer lost power while installing sun virtualbox and when i turned it back on it had virtualbox in the applications tab under system tools but it wouldnt launch it gave me an error and told me to reinstall virtualbox so i went back to the package i downloaded and launched when i clicked install it said please close all other package programs first and i didnt have any open so i rebooted to try and close them that way when i logged back in it did the same thing and then i tried launching the synaptic package manager and it gave me this error 

E: dpkg was inturupted you must manualy run sudo dpkg --configure-a to corect the problem
E: _catche->open() failed, please report. 

i tried running sudu dpkg as it said but it didnt do anything other than bring up the avalible commands for dpkg and i had no idea what to do 

anyway what i need to know is how to get the package manager running again after that i can fix the rest by myself also if its possible can it be kept as simple as possible or step by step instructions because i have only been useing ubuntu for roughly 2-3weeks now 

thanks

---

### Post by dabl on 2010-02-08
```
sudo dpkg --configure -a
```

is the command to use.

---

### Post by Sef on 2010-02-08
> Code:
 	sudo dpkg --configure -a 
is the command to use.

Since the OP is on Kubuntu, the correct code would be this:

```
kdesu dpkg --configure -a
```

---

### Post by phillw on 2010-02-08
> **Sef said:**
> Since the OP is on Kubuntu, the correct code would be this:

```
kdesu dpkg --configure -a
```


Which kinda begs the question as to why Synaptics was giving the OP the Ubuntu command. Well spotted Sef - I'll bear that one mind for sudo issues with Kubuntu !!

Phill.

---

### Post by dabl on 2010-02-10
> **Sef said:**
> Since the OP is on Kubuntu, the correct code would be this:

```
kdesu dpkg --configure -a
```

Actually, no.

dpkg is not a graphical interface package, so there is no "gksudo" or "kdesudo" prefix needed (or appropriate).  I should have said "In a console window or at a tty console issue the command ..."

But "sudo" is the correct prefix for the dpkg CLI command.  ;)

---

