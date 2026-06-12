---
title: "kernel image issues"
date: 2005-09-04
forum: Installation &amp; Upgrades
---

### Post by b4thatsunday on 2005-09-04
Ok, I've seen a few posts regarding this, but not really any solutions, so I'll try my luck.

First, to let you know what I'm expecting...

With Fedora which I installed Ubuntu over (I was sad during the process), I did simple yum update and it would install the next kernel onto my system which would be available during the next reboot....

I thought the same would happen with Ubuntu, but apparently not.

I've went from testing to stable and stable to testing and now back to stable.  When I do dselect Install... it always fail on the kernel image... it says there is a broken dependency with it....  

and it always want to remove it...

how do I get to understand that I'm not wanting to remove the kernel image... but just upgrade everything else on stable.

---

### Post by tonym on 2005-09-04
Normally it is easy to install kernel package.  You need to post the output to help us identify the problem.

---

### Post by b4thatsunday on 2005-09-04
here's one :

jvilla@villa:~$ sudo apt-get install totem-xine
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  linux-image-2.6.10-5-386: Depends: initrd-tools (>= 0.1.75ubuntu2) but it is not going to be installed
  totem-xine: Depends: libnautilus-burn0 (>= 2.8.3) but it is not going to be installed
              Depends: libstartup-notification0 (>= 0.8-1) but 0.8-0ubuntu1 is to be installed
              Depends: libxine1 (>= 1-rc3a) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


and then when using synaptic, I always get

Could not upgrade the system  Fix broken packages first

---

### Post by tonym on 2005-09-06
Check your /etc/apt/sources.list to make sure you have everything correct.  Try the following and post the output

sudo apt-get update
sudo apt-get install initrd-tools

Regards

Tony

---

