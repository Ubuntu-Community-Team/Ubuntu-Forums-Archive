---
title: "So many options ..."
date: 2012-01-20
forum: Installation &amp; Upgrades
---

### Post by sudo_rm_ignorance on 2012-01-20
After over a year of running Ubuntu, I seem to still be able to boot into every kernel I've ever downloaded / updated to.  I can still boot into kernels all the way back to 30.1!  Consequently, in my BIOS menu (since I have Windows installed as well) I have about 25 options to boot into, including: Windows, Dell's partition utility, and the rest are various and sundry Ubuntu kernel revisions and their associated recovery modes.  Is there a safe way that I can not have all of those appear every time?  I don't even think I need the oldest ones anymore (I'd like to keep the most current + the two just before it); do I just remove the packages for the other kernels or what?

Thanks in advance ... :confused:

---

### Post by Frogs Hair on 2012-01-20
I use the janitor / package cleaner in Ubuntu Tweak for removing old kernels . Use correct link for older versions of Ubuntu . [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by JOHNNYG713 on 2012-01-20
Safely clean your system like this !
Open teminal and run these commands !

```
sudo apt-get update
``````
sudo apt-get upgrade
``````
wget Http://www.opendesktop.org/CONTENT/content-files/71529-ubucleaner.sh

``````
sudo chmod +x 71529-ubucleaner.sh
``````
sudo ./71529-ubucleaner.sh
```This will safely remove old kernels,clean apt cache, and all trash even from ~/.local and .local "root" ! I use it before building a .ISO ! Script will place a ubucleaner.sh in your home folder, and you can run it at any time to keep your system clean and up to date and running Smooooth ! 

**Note**: If a new kernel is installed, boot new kernel and **test thoroughly** before cleaning old one to insure all is well !! Then proceed as normal.
:guitar:
                            :KSCopy commands and save for future use !:KS

---

### Post by sudo_rm_ignorance on 2012-02-02
Thanks for the advice all, I will look into ubuntu tweak ...

---

