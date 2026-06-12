---
title: "Minimal install help"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by wrose51106 on 2010-01-12
I am rather new to Linux but am loving it so far. I tried a few different distros and Ubuntu is the one I like the best, except I do not care for all the stuff that comes with it. So I will make my own, I just need a little help from the community.

1) I downloaded minimal ISO, burned and installed no problem but some questions. I choice to use the entire disk, it was a 60 gig drive and / used 58 gig and the swap used 2 gig. These are the only two partitions then?

2) I was asked if I wanted to install security updates by default, manually do them or ignore them. I choice to auto install them. How do I know if updates are available? With no GUI I am rather confused.

3) I need to install X-server then I can install a Gnome?

-Bill

---

### Post by ICEB3AR on 2010-01-12
1) if you do not have manually configured any other partitions or installed the LVM these two partitions are the only one. 

2) sudo apt-get update (new package list)
   sudo apt-get upgrade will install the updateable packages

3) when you install gnome (apt-get install ubuntu-desktop I believe) it is automatically installed to. like to see here: [http://packages.ubuntu.com/dapper/base/ubuntu-desktop]("http://packages.ubuntu.com/dapper/base/ubuntu-desktop")

---

### Post by wrose51106 on 2010-01-12
From what I have been reading regarding partitions I see SDA1 as / and SDA5 as swap. Where/what is sda 2,3,4?

I also have been reading [http://knol.google.com/k/ubuntu-minimal-desktop-installation-guide#](http://knol.google.com/k/ubuntu-minimal-desktop-installation-guide#) but I have lots of questions and only like to ask a few ask once. I get confused easy on new things :/

---

### Post by ICEB3AR on 2010-01-12
/dev/sda2;3;4 are not existing, if there is no entry. 

This is because Linux is using Number 1-4 for Primary or Extended Partitions. Beginning at number 5 this are Logical Partitions. So you have 1 Primary Partition and the logical one which is Swap at your configuration. (The Logical Partitions are in a Extended Partition, but this is not mentioned because it is only a type of Container for Logical Partitions)

---

### Post by wrose51106 on 2010-01-12
That makes sense!

What does this do exactly? alias?

alias nano='nano -w'
alias update='sudo aptitude update'
alias upgrade='sudo aptitude update && sudo aptitude safe-upgrade'
alias iapt='sudo aptitude install'
alias suapt='sudo aptitude'
alias sudeb='sudo gdebi' 
sudo aptitude update
sudo aptitude safe-upgrade
sudo aptitude full-upgrade

---

### Post by ICEB3AR on 2010-01-12
alias are commands for the console which are an alias for the real command. so for example if you have defined an alias:

alias ll='ls -l'

and you type in your console ll it will execute the command ls -l

the commans you will find for sure at google ;)

---

