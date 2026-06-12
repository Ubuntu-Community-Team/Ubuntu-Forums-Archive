---
title: "Roche Newbler Installation ./setup.sh error"
date: 2012-10-17
forum: Installation &amp; Upgrades
---

### Post by cochch02 on 2012-10-17
Hi I am brand new to linux software. I am trying to install Newbler on my desktop (version Ubuntu 12.04.1 LTS) and have hit a few errors. I am attempting to install the Data Analysis 2.7 All package. I have all of the files successfully unzipped, but every time I try to run the setup.sh file I receive an error. 

Double clicking on the file opens it in geddit which is unhappy with the symbols used in the file. 

Trying to install it through the terminal window tells me that the computer can;t find the file or directory. 

It can find the Data Analysis package (which is a .tgz), but it won't do anything with it without a destination. Any suggestions?

---

### Post by Starcruiser322 on 2012-10-18
Did you set the setup.sh to be executable?
(NOTE: must be located on local drive, not removable)
Right click, properties, permissions, set the executable checkbox.
Failing that, you could use the equivalent terminal commands. Open terminal, cd to the file that setup.sh is located, then enter: sudo chmod +x ./setup.sh

---

### Post by drmrgd on 2012-10-18
It would be helpful to see the actual terminal commands you entered in order to better troubleshoot.  The error is either because you pointed to the wrong file in your command, or because the installer script has not yet been make executable (follow Starcruiser322's advice).

Also double check the Newbler source archive for either a README or INSTALL file, as that will give you some clues as to how to properly configure and build the package.

I also sort of remember seeing some help threads (albeit older ones) on SeqAnswers about installing Newbler on Ubuntu systems (never got around to it myself, though).

---

