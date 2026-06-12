---
title: "Kernel upgrade"
date: 2005-11-05
forum: Installation &amp; Upgrades
---

### Post by samdude9 on 2005-11-05
Hi i really need some help with upgrading the ubuntu 5.10 kernel to 2.6.14.
i have...
Downloaded the kernel source and patch (if i patch can i change processor settings?).
Unzipped to /home/samdude9/scr/ (tried /usr/scr/ but didnt work).
Tried to "Make menuconfig" but it didnt work.

All i need is for some kind person to tell me how to make the text based menu.

thanx
newbie:smile:

---

### Post by tseliot on 2005-11-05
Try my guide: [http://www.ubuntuforums.org/showthread.php?t=85064]("http://www.ubuntuforums.org/showthread.php?t=85064")

and get to the following section "NOTE: HOWTO compile from a vanilla kernel from kernel.org"

---

### Post by samdude9 on 2005-11-05
i dont have the net on my laptop though

---

### Post by tseliot on 2005-11-05
Download the files you need (.deb and according to your architecture) from here [http://archive.ubuntu.com/ubuntu/pool/main/]("http://archive.ubuntu.com/ubuntu/pool/main/")

then move the files to your laptop and install them there by doing "sudo dpkg -i nameofthefile.deb"

Then follow the guide

---

### Post by samdude9 on 2005-11-05
do i have to download everysingle one

---

### Post by samdude9 on 2005-11-05
ive downloaded these ones...
sudo apt-get updatesudo apt-get install build-essentialsudo apt-get install kernel-packagesudo apt-get install gcc (this will install gcc-4.0 for kernel 2.6.13 or superior)sudo apt-get install gcc-3.4sudo apt-get install libncurses5sudo apt-get install libncurses5-devsudo apt-get install libqt3-mt-devsudo 

but i cant find libncurses

thanks for the help its really useful.

p.s
ignore above post

---

### Post by tseliot on 2005-11-05
[QUOTE=samdude9]ive downloaded these ones...
sudo apt-get updatesudo apt-get install build-essentialsudo apt-get install kernel-packagesudo apt-get install gcc (this will install gcc-4.0 for kernel 2.6.13 or superior)sudo apt-get install gcc-3.4sudo apt-get install libncurses5sudo apt-get install libncurses5-devsudo apt-get install libqt3-mt-devsudo 

but i cant find libncurses

thanks for the help its really useful.

p.s
ignore above post[/QUOTE]
Try here: [http://archive.ubuntu.com/ubuntu/pool/main/n/ncurses/]("http://archive.ubuntu.com/ubuntu/pool/main/n/ncurses/")

BTW if you have a Ubuntu CD you can add it as one of the repositories in Synaptic/Kynaptic and install the packages from there.

In synaptic do this: Edit/Add CD-rom

---

