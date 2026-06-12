---
title: "Installing Freenx"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by dagarshali on 2008-04-17
Hi,
I just installed Ubuntu and I have to setup something equivalent to remote desktop for accessing my xp machine from the machine on which I have installed Ubuntu. From the internet I found that Freenx  does that. When I tried installing that my problems began.

1) First, in some of the websites, they told to add some line into /etc/apt/souces.list
    Being a windows user for as long as I can remember, I tried using gvim to edit this file. I have not clue how to add this line there. I then tried to add the same line in software sources, that you can accesss thru System>Administration>software sources. I added the line in the third party sources. No matter what deb... that i add there, when I apply, it says it couldn't find some package and that either the link is outdated or the network connection is missing.

Could anybody give me step by step instruction as to how this is done. I really have no clue about this.

Regards,
Vishwa

---

### Post by Partyboi2 on 2008-04-17
Open a terminal and type
```
 
gksudo gedit /etc/apt/sources.list

``` This will open the sources.list file then at the bottom of the file add the line or lines that the instructions are asking you to add. Then save and close. Back in the terminal
```
 
sudo apt-get update

```
then finally iinstall the package.

---

