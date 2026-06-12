---
title: "synaptic package manager problem"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by terryfunk4life on 2006-09-20
well my probem is this I install ubuntu and every thing is fine so far
but then i go to install wine. but i enter the wrong url in the package manager and now ever time i start it up it gives me this and no packages show up
E: Type 'ttp://wine.budgetdedicated.com/apt' is not known on line 32 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

(i typed ttp instead of http :(    )
 so is there anyway to set back the date or undo this ? thank you

---

### Post by wieman01 on 2006-09-20
No problem. Execute this command and delete the corresponding line using the text editor & save afterwards (run from terminal):
> sudo gedit /etc/apt/source.list
Having removed the compromising line, Synaptic should run like a charm.

[COLOR="Red"][P.S.: Not sure if the file is called "source.list" or "source.lst"... Try both... I am not in front of my own computer.][/COLOR]

---

### Post by terryfunk4life on 2006-09-20
blagh it says that i cant save becuase its restricted......:(

You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again.

---

### Post by enopepsoo on 2006-09-20
try opening it with 
[HTML]sudo gedit /etc/apt/sources.list[/HTML]

your regular user account will not be able to write to files outside of your /home folder.  sudo enables you to do anything.

:D :KS

---

### Post by jISh on 2006-09-20
Actually, it's
gksudo gedit /etc/apt/sources.list

Obviously you didn't do sudo because you don't have root authority to modify it.

And gksudo for GTK apps, save yourself some trouble.

Also, your line should read this:
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

---

### Post by terryfunk4life on 2006-09-20
wooot thank you very much :)

---

### Post by enopepsoo on 2006-09-20
sorry for saying sudo. :confused: 

it works for me though!

---

### Post by wieman01 on 2006-09-20
Apologies, guys. Yeah, was not sitting in front of my own computer. Got the path wrong. 

Adding "sudo" is sufficient usually. "gksudo" is fine as well, does not make a difference.

---

