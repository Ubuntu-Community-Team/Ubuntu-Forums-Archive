---
title: "help me"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by krishnakrishna on 2008-03-04
i had received the open source cd UBUNTU 7.10..
Iam eager to play music and video files in this platform..
But it's asking some plugins to install
I searched all over to my extent in internet
But i cant get a right plugin that supports my PC(Intel Pentium4 -2.8ghz)
Please any one of them heip me!!!!!!!

---

### Post by vijaym on 2008-03-04
i am assuming you are using the i386 ubuntu cd

depending on how your system is installed...

and what media player you want to use

check out these links
[www.medibuntu.org](www.medibuntu.org)
it will give you all the links and advice

or 
use synaptic to install the plugins
found on system - administration

---

### Post by zvacet on 2008-03-04
Just to be sure check that you have all repos open.Go to the **system>admin<software sources**>check all boxes under Ubuntu software and updates tab.Reload.Now go to the applications>accessories<terminal and type

```
gksudo gedit /etc/apt/sources.list
```

add this line 

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

Save and close the file.In terminal type

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
sudo apt-get update
```

Now you have medibuntu repo,but you need plugins also 

```
sudo apt-get install ubuntu-resricted-extras
```

After this go to the synaptic and in search box type w32 codecs and when you find them mar fopr installation and install.

---

