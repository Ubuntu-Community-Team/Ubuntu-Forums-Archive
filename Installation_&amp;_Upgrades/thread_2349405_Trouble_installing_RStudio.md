---
title: "Trouble installing RStudio"
date: 2017-01-14
forum: Installation &amp; Upgrades
---

### Post by casaj2 on 2017-01-14
Hi all, new Ubuntu user here so please bear with me. When trying to install rStudio through the terminal I am getting the following errors:

dpkg: dependency problems prevent configuration of rstudio:
 rstudio depends on libjpeg62; however:
  Package libjpeg62 is not installed.
 rstudio depends on libgstreamer0.10-0; however:
  Package libgstreamer0.10-0 is not installed.
 rstudio depends on libgstreamer-plugins-base0.10-0; however:
  Package libgstreamer-plugins-base0.10-0 is not installed.

dpkg: error processing package rstudio (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info (1.7-1) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'

---

### Post by casaj2 on 2017-01-14
pls respond

---

### Post by steeldriver on 2017-01-14
Please be patient

This is a volunteer forum - there is no guarantee that someone with insight into your problem will be active on the site at any particular time

Meantime, please describe exactly **how **you are trying to install rstudio (PPA? .deb? from where?) - what is the exact command you are typing? Please also include information about the **version **of Ubuntu that you are using.

---

### Post by casaj2 on 2017-01-14
Installing through the terminal.

the commands are as follows

sudo apt-get install gdebi-core
wget [https://download1.rstudio.org/rstudio-1.0.44-amd64.deb](https://download1.rstudio.org/rstudio-1.0.44-amd64.deb)
sudo gdebi -n rstudio-1.0.44-amd64.deb
rm rstudio-1.0.44-amd64.deb

and I am running the latest version of ubuntu: 16.10

---

### Post by casaj2 on 2017-01-14
I managed to fix the problem. 

There was an error in the software from a 'ppa.launchpad.net' location which did not have a release file. After removing it from the other software tab of software and updates I was able to install Rstudio without a problem.

---

