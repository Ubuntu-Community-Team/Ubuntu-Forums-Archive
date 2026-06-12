---
title: "Probelm in Installing Acrobat"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by rajez79 on 2008-09-03
Hi,

I tried of installing adobe acrobat in ubuntu 7.04. After downloading rpm file "AdobeReader_enu-8.1.2_SU1-1.i486.rpm" using the command 

sudo alien -i package-name.rpm 

i converted it to .deb file. Then i tried of installing the .deb file.

sudo dpkg -i adobereader-enu_8.1.2_SU1-1_i386.deb

But after everything finishes if i try to give

$ acroread 
bash: /usr/bin/acroread: Permission denied 

is the output am getting. I tried it as root user also. Am getting the same  output.

Please help me in solving this issue or temme how to install adobe acrobat.

-Rajez-

---

### Post by Elfy on 2008-09-03
You can get acroread from medibuntu - if you haven't got medibuntu set up, I would uninstall it - use synaptic to uninstall it - best not toi use rpm's unless you really have to. Then run each of these in terminal seperately.

```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get install acroread
```

---

### Post by rajez79 on 2008-09-03
Hi,

Fetched 5B in 3s (1B/s)  
Reading package lists... Done
**rajesh@rajesh-desktop:/$ sudo apt-get install acroread**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package acroread
rajesh@rajesh-desktop:/$

I uninstalled adobe and tried the commands given in the above post. Awhile giving the third command this is the output am getting. 

-rajez79-

---

### Post by Partyboi2 on 2008-09-03
Looks like acroread is not available for feisty in the medibuntu repo's anymore.

---

### Post by rajez79 on 2008-09-03
how can i install Acrobat reader for feisty fawn.. help me. :-(

-rajez-

---

### Post by Partyboi2 on 2008-09-03
Have you tried going to the adobe website and downloading and installing the deb package? You can go [[COLOR=Blue]here[/COLOR]]("http://www.adobe.com/products/acrobat/readstep2_allversions.html") and download it. Make sure you choose deb version under "Select an Installer" then once you have download double click on it to install.

---

