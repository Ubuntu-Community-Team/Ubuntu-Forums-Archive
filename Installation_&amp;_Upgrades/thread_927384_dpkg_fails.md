---
title: "dpkg fails?"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by clickypens on 2008-09-22
I supppose this goes here:

whenever I try to update my hardy (or add or remove programs) I get an error telling me that dpkg was interrupted and that I should manually run "dpkg --configure -a" to corrrect it (it also says "E: _cache->open() failed, please report").
so, I do such. I open a terminal and type that in. it says I don't have permission and asks if I'm su. I installed ubuntu onto my lap from a live disc, it never asked for an su password. I type in the regular user password, and (of course) this is denied.

So how do I correct the problem?

---

### Post by lisati on 2008-09-22
From the terminal (on the Applications->Accessories->terminal) run ```
sudo dpkg --configure -a
```

It will ask for your password - use the same one that you logged in with. Don't panic if it doesn't show, just type in your password as usual. This is a normal security process used by Ubuntu.

---

### Post by clickypens on 2008-09-22
SUDO! I always forget to add that. thanks

so I did that, and get this:
dpkg: error processing eject (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 eject

do I have to reinstall ubuntu?

---

### Post by frankleeee on 2008-09-22
are you sure you put the command in the terminal correctly, do it again and post the outcome.

---

### Post by clickypens on 2008-09-22
> **frankleeee said:**
> are you sure you put the command in the terminal correctly, do it again and post the outcome.


I put it in exactly as lisati said to. and [QUOTE=clickypens]
dpkg: error processing eject (--configure):
Package is in a very bad inconsistent state - you should
reinstall it before attempting configuration.
Errors were encountered while processing:
eject[/QUOTE]
is exactly what I got

---

### Post by frankleeee on 2008-09-23
I doubt if you have to due a install, somebody who recognizes your problem will probably post some solutions.

---

### Post by clickypens on 2008-09-23
well, thanks for trying.

anyone know what's up?

---

### Post by xeth_delta on 2008-09-23
> **clickypens said:**
> SUDO! I always forget to add that. thanks

so I did that, and get this:
dpkg: error processing eject (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 eject

do I have to reinstall ubuntu?

The "reinstall" refers to the package, not the entire system. What were you trying to do/install?

---

### Post by unutbu on 2008-09-23
What is the output if you type 
```

sudo apt-get -f install
sudo dpkg --configure -a
```
(I'm getting this from [http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html))

---

### Post by clickypens on 2008-09-23
> **xeth_delta said:**
> The "reinstall" refers to the package, not the entire system. What were you trying to do/install?

just regular updating.

> **unutbu said:**
> What is the output if you type 
```

sudo apt-get -f install
sudo dpkg --configure -a
```
(I'm getting this from [http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html))

well, first it installed that "-f"  program (obviously), though I did notice that when it read me the state information, I had "0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
**1 not fully installed or removed**"
could this be the problem? if so, what program is it?

 then when I ran the dpkg config command it didn't do anything.
am currently trying to run upgrades (the Update Manager has gotten stuck after I hit "Install Updates"

EDIT: that last command got it working. thanks ton, man.

---

### Post by xeth_delta on 2008-09-23
> **clickypens said:**
> just regular updating.



well, first it installed that "-f"  program (obviously), though I did notice that when it read me the state information, I had "0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
**1 not fully installed or removed**"
could this be the problem? if so, what program is it?

 then when I ran the dpkg config command it didn't do anything.
am currently trying to run upgrades (the Update Manager has gotten stuck after I hit "Install Updates"

Ok, there might be a problem with one of the packages.
"-f" is not a program, it is just an option of the command/program dpkg.

Please, do post all the output and how you write the commands, that way it will be much easier for us to help you. Just copy from the terminal and paste in the composing page. Please post the code between CODE tags (the # button on this page)

Run
```
sudo apt-get clean
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
Please post the whole error message.

---

