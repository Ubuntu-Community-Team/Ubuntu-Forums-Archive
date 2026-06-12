---
title: "Cannot Install Opera 10"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2009-09-23
Running Karmic and either way I try and Install Opera I get either: 
Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package opera has no installation candidate

Doesnt matter what mirror either.  Any ideas?

---

### Post by LKjell on 2009-09-23
use dpkg -i to install

---

### Post by patasenko on 2009-09-23
I hade the same thing with Skype beta... I think something got broken in the updates.

---

### Post by kansasnoob on 2009-09-23
Well, after updates a few hours ago Karmic just keeps freezing up, but what I'd done a few days ago when I reinstalled was edit /etc/apt/sources.list by adding:

> ##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Opera - [http://www.opera.com/](http://www.opera.com/)
## Run this command: sudo wget -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny non-free


As it says be sure to add the GPG key:

```
sudo wget -O - http://deb.opera.com/archive.key | sudo apt-key add -

```

Of course then either reload Software Sources, or click reload in Synaptic, or just run apt-get update, then apt-get install opera.

That had seemed to work ok for me.

Not sure why things are hosed right now.

---

### Post by sports fan Matt on 2009-09-23
I was going to have it as a backup but its ok..it is not that essential.

---

### Post by oboedad55 on 2009-09-23
> **LKjell said:**
> use dpkg -i to install

I have the same issue with fotoxx and picasa. Unfortunately your idea didn't work, but thanks for the suggestion. Any other ideas?

---

### Post by ronacc on 2009-09-24
download orera 10 from the opera site and install it with gdebi .
[http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

---

### Post by froggyswamp on 2009-09-24
I have exactly the same issue with (not) installing Google Chrome as reported in 1st post. So it's a bug somewhere. Anybody filed a bug yet?

---

### Post by moviemaniac on 2009-09-24
> **ronacc said:**
> download orera 10 from the opera site and install it with gdebi .
[http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)
I always get the latest ones from here: [http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)

Never had any problems getting these packages to install with gdebi. Sure, those builds are bleeding edge but even the Opera Alphas work better for me than many "stable" releases of Firefox.

---

### Post by Eestlane on 2009-09-24
I have same problem with latest Skype and latest Opera weekly. Is there something messed up with .deb installer? From googleing I found that installing from the cli version of .deb installer might work, haven't tested it, though.

EDIT: I thought I was the only one, so I'm glad I'm not.
EDIT2: cli version of gdebi from terminal works indeed.

---

### Post by ronacc on 2009-09-24
> **moviemaniac said:**
> I always get the latest ones from here: [http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)

Never had any problems getting these packages to install with gdebi. Sure, those builds are bleeding edge but even the Opera Alphas work better for me than many "stable" releases of Firefox.

I always run the latest build from the desktop team also . I just thought that since the OP was having problems I should point him at the "stable" build .

---

### Post by moviemaniac on 2009-09-24
> **ronacc said:**
> I always run the latest build from the desktop team also . I just thought that since the OP was having problems I should point him at the "stable" build .
Well, as the current Opera dev-builds build upon the stable 10.00 code and mainly fix stuff for unite there shouldn't be any problem using these at the moment.

---

### Post by sports fan Matt on 2009-09-25
After a complete reinstall..the same problem.  Im not mad, just pointing out a fact.  Opera says "bad file descriptor"

---

### Post by rburkartjo on 2009-09-25
sox i got the same error message you did when tried to install some updates for clamtk

---

### Post by cgroza on 2009-09-25
Download the deb. file and use dpkg to install.I had the same problem...maybe its my repositories...

---

### Post by froggyswamp on 2009-09-25
> **sox fan Matt said:**
> After a complete reinstall..the same problem.  Im not mad, just pointing out a fact.  Opera says "bad file descriptor"

It has nothing to do with Opera itself, it's Ubuntu's graphical installer, thus, until fixed (if ever hehe) use "sudo dpkg -i *.deb" to install any .deb you want.

---

### Post by sports fan Matt on 2009-09-25
So the command would be sudo dpkg -i *.deb opera? or something to that affect?

---

### Post by FewClues on 2009-09-25
> **ronacc said:**
> download orera 10 from the opera site and install it with gdebi .
[http://www.opera.com/browser/download/](http://www.opera.com/browser/download/)

I know this was a fix for Opera but it also worked for my Skype install.  I double clicked the package and the debian installer said Bad File Descriptors.  However if I right click and use gdebi it went in without a struggle.  

Thanks for the tip!!:P

---

### Post by Eestlane on 2009-09-25
Has anyone reported a bug about it already?

Okay, found it: [https://bugs.launchpad.net/ubuntu/+source/vte/+bug/388953](https://bugs.launchpad.net/ubuntu/+source/vte/+bug/388953)

---

