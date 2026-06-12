---
title: "About Game Install and Write Its Codes"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by Caghkan on 2007-12-15
Hi everyone! I am new user for ubuntu and I have a question. I want to install poker game and I found one. Its web address is [www.pok3d.com](www.pok3d.com) and it say below.

>     *
      Ubuntu GNU/linux gutsy

      Add the following lines to your /etc/apt/sources.list 
      deb [http://pok3d.net/gutsy](http://pok3d.net/gutsy) ./
      deb-src [http://pok3d.net/gutsy](http://pok3d.net/gutsy) ./

      If not present, 
      add deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe 
      
       Install the software and the graphics: apt-get update
      apt-get install python-poker3d poker3d-data 

      Run with /usr/games/poker3d


However, I don't understand how to install it because I am getting use to write codes!

Please help me! When I wrote this codes, root terminal didn't find them!

---

### Post by Partyboi2 on 2007-12-17
>        Add the following lines to your /etc/apt/sources.list 
      deb [http://pok3d.net/gutsy](http://pok3d.net/gutsy) ./
      deb-src [http://pok3d.net/gutsy](http://pok3d.net/gutsy) ./Open a terminal (Applications>Accessories>Terminal)
Then you need to open up the etc/apt/sources.list to add those lines.
```
gksudo gedit /etc/apt/sources.list
```(it will ask for your password enter it and press enter.)
Your etc/apt/sources.list will open at the bottom of the list add:

```
deb [http://pok3d.net/gutsy](http://pok3d.net/gutsy) ./
deb-src [http://pok3d.net/gutsy](http://pok3d.net/gutsy) ./

```then click on "save" (but don't exit yet)
>        If not present, 
      add deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe 
      Have a look through the rest of the lines in the /etc/apt/sources.list
for a line that says
```
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
``` if you find a identical line make sure there is no # in front of it.
If you do not find a identical line then at the bottom of the list add it.
then save then exit.
(If you are still stuck at this point then post your /etc/apt/sources.list and someone should be able to help)
If you are not stuck then we can continue.
>         Install the software and the graphics: apt-get update
      apt-get install python-poker3d poker3d-data Back in the terminal we need to update the changes that were made, to do this type:
```
sudo apt-get update
```Now you need to install the program
In a terminal type:
```
 sudo apt-get install python-poker3d poker3d-data 
```Then after that you should be able to run it.

---

