---
title: "Making Sense of Package Lists"
date: 2012-01-24
forum: Installation &amp; Upgrades
---

### Post by MikeFried on 2012-01-24
Starting with the complete "list of sections in oneiric", 
I've been looking for:

a) what set of packages makes up a "base" or "core" of a 
system (my terms for what is common to desktop and server 
editions) and 

b) what set of packages is added to that "base" to make a 
"server" and lastly 

c) what set is added to that "base" to make a typical desktop.


For simplicity lets say I am thinking of a basic LAMP server
and a simple gnome-desktop without too many extras.

For reference - the categorized list is:
    [http://packages.ubuntu.com/oneiric/](http://packages.ubuntu.com/oneiric/)

and the raw list is:
[http://packages.ubuntu.com/oneiric/allpackages](http://packages.ubuntu.com/oneiric/allpackages)

Can anyone point me in the right direction for this information?

Thanks.

---

### Post by jerrrys on 2012-01-24
sudo apt-get install lightdm gnome-session-fallback

That will give you a desktop (GUI) with just about nothing in it.

[http://packages.ubuntu.com/oneiric/lightdm](http://packages.ubuntu.com/oneiric/lightdm)

[http://packages.ubuntu.com/uk/oneiric/gnome-session-fallback](http://packages.ubuntu.com/uk/oneiric/gnome-session-fallback)

For a full blown system add "ubuntu-desktop".

[http://packages.ubuntu.com/oneiric/ubuntu-desktop](http://packages.ubuntu.com/oneiric/ubuntu-desktop)

---

### Post by MikeFried on 2012-01-25
Maybe I should ask it a different way.

I am wondering what the theoretical package list is, or some kind
of installation that results in a basic system with nothing but a shell.  
No applications, tools, nothing other than maybe dpkg/apt to install
the rest.

From there I understand that part of your answer is how to put a 
light weight desktop on that. But my interest is to find a starting 
point for a specialty distribution or any distro for that matter.

---

### Post by jerrrys on 2012-01-25
The starting point for any build would be a terminal install.  This can be accomplish with either the "alternate install cd" (the F4 option) or mini iso.

---

### Post by MikeFried on 2012-01-25
[I]>>The starting point for any build would be a terminal install

[/I]And what is (or where is) the package list for that?

---

### Post by amauk on 2012-01-25
the package "ubuntu-minimal" is the closest thing to a base package
This is a meta-package that depends on all the core stuff to get a minimally operational system
(Eg. for a single-purpose embedded device)

you can see what ubuntu-minimal pulls in by doing
```
apt-cache depends ubuntu-minimal
```

The next rung up the ladder is ubuntu-standard
This is a meta-package that depends on all the standard stuff to get a conventional multi-user install
(Eg. for a multi-purpose "server")

After that, you've got the desktop meta-packages
ubuntu-desktop, ubuntu-netbook
plus the variants on each (kubuntu, lubuntu, xubuntu, etc.)

---

### Post by jerrrys on 2012-01-25
And that would be ubuntu-standard

[http://packages.ubuntu.com/lucid/ubuntu-standard](http://packages.ubuntu.com/lucid/ubuntu-standard)

EDIT: amauk has it right.

EDIT#2:  [http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=ubuntu-minimal+details+of+package&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=ubuntu-minimal+details+of+package&sa=Search&cof=FORID:9)

---

### Post by MikeFried on 2012-01-25
[]("http://ubuntuforums.org/member.php?u=384906")Thanks Amauk.  That's what I was looking for.

---

### Post by jerrrys on 2012-01-25
and one last link

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

