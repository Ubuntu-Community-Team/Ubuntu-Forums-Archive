---
title: "What files can I remove"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by Rayston on 2006-09-11
I just installed Xubuntu on an a very old Compaq Desktop with a 1.3 Gig HD and 64 Megs of ram. 

The very first time I have tried to login, I get an error saying that GDM cannot write to my authorization file for some reason. I am pretty sure that since its a very small HD its probably because its full, does anyone know some files I can safely remove from the default install of xubuntu without hurting anything so I can at least login? 


Thanx in advance

Rayston

---

### Post by kidders on 2006-09-11
Why not check your disk space? (Use df)

Take a quick look through your installed packages for things you don't want, if you need space. Be careful though:

[LIST]
[*]Don't delete individual files ... only remove entire packages.
[*]Don't uninstall something you don't recognise.
[/LIST]

What you can/can't delete is a very personal question that only you can answer, really :-(

---

### Post by Lord Illidan on 2006-09-11
Just how large is the harddisk anyway?

---

### Post by kidders on 2006-09-11
> I just installed Xubuntu on an a very old Compaq Desktop with a 1.3 Gig HD and 64 Megs of ram.

Do you suppose there's much point in trying to work Ubuntu with so little space? (Perhaps between the two of us, we can come up with a few suggestions?)

---

### Post by johnbl on 2006-09-11
Have similar problem. Knbow it's a basic question but just how from command line does one remove a file. del filename.ext does work.. 'Command not found'  is the only reponse.
help help lists every thing but there is no windows |pause equivalent I can see so on a small laptop, listings start some where in e... 
Help on either point most appreciated.

---

### Post by kidders on 2006-09-12
The command you're after is **rm**. Take a look at its manual page before using it though ... it's tough work to undo mistakes! (ie forensic data recovery.)

To solve your other problem, take a look at **less** and **more**. You can "pipe" the output of any command through either of these, and scroll around in it, search it, etc. Another possible help is **grep**, which you can use to filter something for the parts your interested in.

---

### Post by kerry_s on 2006-09-12
Personally I'd go for a OS like DSL(50mb) which is made for things like that. [http://damnsmalllinux.org/](http://damnsmalllinux.org/)

But if you must remove files i would get rid of the doc and man files. There just info files mainly but take up alot of space, i use the online ones through my browser. Most importantly it won't toast the system to remove.
The command is->
sudo rm -r /usr/share/doc
sudo rm -r /usr/share/man

---

