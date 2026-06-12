---
title: "sbackup-gtk not installable from 14.04"
date: 2014-05-05
forum: Installation &amp; Upgrades
---

### Post by Tsoomo on 2014-05-05
[COLOR=#333333][FONT=UbuntuRegular]I can't install sbackup on my laptop due to below reason.[/FONT][/COLOR]
```
$ sudo apt-get install sbackup-gtk 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 sbackup-gtk : Depends: python-glade2 but it is not going to be installed
               Depends: python-gnome2 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```
I did 
```
sudo apt-get clean && sudo apt-get update
```
but still getting same error for sbackup-gtk

---

### Post by gdesilva on 2014-05-05
Just for your info, I did not have any issues installing sbackup-gtk. 

I am running Ubuntu Studio 14.04 - 64bit version.

---

