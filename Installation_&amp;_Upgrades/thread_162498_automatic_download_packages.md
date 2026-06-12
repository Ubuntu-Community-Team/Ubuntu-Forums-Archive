---
title: "automatic download packages"
date: 2006-04-19
forum: Installation &amp; Upgrades
---

### Post by Smika on 2006-04-19
Hello,

I heard from a friend that it is possible to download packages automatical when a program need some. So when i open the terminal and I install Mythtv, it isays that it needs some packages (libraries). So first you need to install this before you can install mythtv (this is an example). But i heard that when you install mythtv from the terminal and it needs the packages that it can be automatical download when you change something in some systemsfiles. OIs there anyone who can tell me how this is possible?

Thanks a lot,

Smika

---

### Post by localzuk on 2006-04-19
Well, if you install mythtv via apt (or one of the graphical front ends such as synaptic) from the repositories, it will tell you that you need certain dependancies and ask if you wish to install them also. Is this what you mean?

---

### Post by Smika on 2006-04-19
Thanks for your reaction, but this is not what i mean. I mean that it is also possible when you do it on the terminal.

---

### Post by localzuk on 2006-04-19
What do you mean on the terminal. If you run apt-get you are doing so on the terminal? Do you mean when compiling a file?

---

### Post by Smika on 2006-04-19
When i am on the terminal and type for example:

sudo dpkg -i slcreator.deb

It will install slcreator, but it doesn't because it needs gambas. Now i can go to synaptec for downloading gambas and everything is fine. But I heard that it is also possible that when i type:

sudo dpkg -i slcreator.deb

and it needs gambas that it will be installed automatical, so i don't need to go to synaptec for installing gambaz, because it is already done in the terminal.

---

### Post by jobezone on 2006-04-19
It's:

sudo dpkg -i slcreator.deb
sudo apt-get -f install


The second command will either finish installing the package, along with its dependencies, or remove the package. You could also have a look at **gdebi** .

---

