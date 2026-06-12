---
title: "Help -- utter newbie -- how to execute install programs in folders"
date: 2005-09-03
forum: Installation &amp; Upgrades
---

### Post by Phil2005 on 2005-09-03
Braaaand new to Linux.
How does one enter commands to unpack?
Once unpacked, how does one execute commands to install a program (here OO 2.0 beta)?
Thanks,
Phil2005 :)

---

### Post by tonym on 2005-09-04
What kind of file do you have in mind?  Is it a .deb,  .tar.gz,  ....etc?

---

### Post by Sale on 2005-09-04
I don't know what Phill2005 had in mind, but, since I'm an "utter newbie" myself, I'd really like to see some sort of a HOW-TO regarding the isntalatio from all those filetypes.

---

### Post by Phil2005 on 2005-09-04
[QUOTE=tonym]What kind of file do you have in mind?  Is it a .deb,  .tar.gz,  ....etc?[/QUOTE]
 tar.gz, whatever that is.
Is there any place that simply discusses how one accesses and enters commands to download programs, unpack them and install them?
Thanks,
Phil2005

---

### Post by tonym on 2005-09-06
Use tar -xvzf foo.tar.gz     (or foo.tgz)

For .tar.bz use tar -xvjf.

For most .tar.gz unpack as above then cd to the directory created.  Then

./configure
make
make install

However,  this is too simplistic,  for each package you need to read the instructions that come with it to check its specific details.

This is why you are best keeping to the packages provided by the distribution.  Ubuntu has lots of packages you can access through aptitude or synaptic applicatoins on the menu.  If you can't find a package you want,  have you edited /etc/apt/sources.list to add the universe and muliverse repositories?

---

### Post by hashimoto on 2005-09-06
[QUOTE=Phil2005]tar.gz, whatever that is.
Is there any place that simply discusses how one accesses and enters commands to download programs, unpack them and install them?
Thanks,
Phil2005[/QUOTE]

This filetype is used for source code. Which means that you must compile and install the program yourself. Could be a little complicated, though. I've been using linux for some years now and I still don't do it myself. With Ubuntu, it is very easy to find almost any software in deb packages which are very easy to install using Synaptic (graphical ui) or apt-get (text based) tools.

Go and read [http://ubuntuguide.org/](http://ubuntuguide.org/) It certailnly is your friend and gives you a lot of information. Be ready to use some text based commands, though. And as of OOo 2 beta you can install it thru Synaptic after you enable some repositories. Then your first stop is [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

