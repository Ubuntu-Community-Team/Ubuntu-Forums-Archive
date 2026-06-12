---
title: "cannot instal openFOAM on natty desktop"
date: 2011-07-19
forum: Installation &amp; Upgrades
---

### Post by nagi.kj on 2011-07-19
friends

trying to install openFOAM on natty desktop

seems to be a problem adding openFOAM to the repo

and later some compilation error

thnx

---

### Post by aeftimia on 2011-08-18
Open terminal and run the following as root (type "sudo su" without quotes and then whatever root password you set during installation--try your own password if you are not sure.)
Now copy and past this block of code into the terminal:

sh -c "echo deb [http://www.openfoam.com/download/ubuntu](http://www.openfoam.com/download/ubuntu) maverick main >> /etc/apt/sources.list" 
apt-get -y update
apt-get -y install openfoam201 paraviewopenfoam3101
echo "
source /opt/openfoam201/etc/bashrc
" >> ~/.bashrc
. ~/.bashrc


That seemed to work for me. I have not tested it too much yet (I have been working on some other stuff) so let me know if something goes wrong.

---

