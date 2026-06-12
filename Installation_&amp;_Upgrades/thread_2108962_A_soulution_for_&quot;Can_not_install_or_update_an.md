---
title: "A soulution for &quot;Can not install or update anything using Muon Software/Updates Mange"
date: 2013-01-26
forum: Installation &amp; Upgrades
---

### Post by Linuxour on 2013-01-26
[LEFT]A soulution for not being able to install or update anything using Muon Software/Updates Manger "  in Kubuntu 12.10


Hello,

The following problems faced me and i wanted to post it to help others if they suffer from it .

- Downloading updates through Muon updates manger was too slow than normal ( about 2Kb/s )

- Can not install any applicaion unless from Terminal

What i did was 

1- Downloading updates from the terminal - the download speed was normal - by typing

sudo apt-get upgrade

2- restarting

3-- installing any application through terminal by typing for example

sudo apt-get install kwordquiz

an error appeared and asked me to type

sudo dpkg --configure -a

so i did .

* Thats what i did , and all went well 



Notes : after the second step  i opened Muon update manger and i found that 

linux-headers-generic and linux-image-generic were not downloaded , and when i tried to this message appeared
 
 " Another application seems to be using the package system at this time. You must close all other package managers before you will be able to install or remove any packages. "


although Muon update manger was the first program i opened .

And the same message appeared every time i tried to install any application using Muon Software Center .

But installing applications through went well then .
[/LEFT]

---

