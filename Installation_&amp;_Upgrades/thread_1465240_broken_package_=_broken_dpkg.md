---
title: "broken package = broken dpkg"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by violetman on 2010-04-29
Hello I try to install Cinelerra in Ubuntu Lucid wich suppose to be available..[Cinelerrawebsite]("http://cinelerra.org/getting_cinelerra.php#ubuntu")
 
I add the repository & install key then when I did the update
everything was ok , then in the midle of the installation just quit, now I got a broken package wich I cant remove... I can't install any programs, cant update my comp .. need some help please.
 
 
I used synaptic package manager and try to remove broken package
but no luck .. 

[IMG]http://www.adrive.com/home/downloadfile/aece8677fb9e779cd867e54791fa37fa8fd0fd7a45e00d38aa94139777253b45[/IMG]
 
 
I try this no luck either ...
 
 
 What to do if an installation process fails and you find it is no longer possible to install or remove packages: 
[LIST]
[*]Open a Terminal and type the following commands, pressing the Return or Enter key after each (you may have to type in your [password]("https://help.ubuntu.com/community/RootSudo")): 
[/LIST] 
 sudo dpkg --configure -a
 sudo apt-get install -f
 
 [IMG]http://www.adrive.com/home/downloadfile/f9a9bc838d5aa25f8419c01689d2bcb4f8bf8f47b85785b72b70ff6827225265[/IMG]
 
 
 
the rest of my sofware works , I dont want to re-format hd
 
any ideas please? Can I removed manually? whats wrong ? 

*pd* hope this time there is no broken pics
 
 
Thank you...

---

