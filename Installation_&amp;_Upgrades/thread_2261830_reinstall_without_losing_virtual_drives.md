---
title: "reinstall without losing virtual drives?"
date: 2015-01-21
forum: Installation &amp; Upgrades
---

### Post by Hamburgian on 2015-01-21
I'm about to buy a new PC (rather than trying to build a suitable box, which had always worked up until 14.04!)
I fully expect a few hiccups along the way and, as such, wil probably have to do a reinstall and use a sources.list to reinstall all my programmes.
Obviously I can set the reinstall to NOt format/delete existing data...but there is a small problem.
At the moment I have two installations...one a fresh 14.04 (64 bit), the other also 14.04 but is a 32 bit installation which has been constantly updated since Gutsy. 
I don't have /home for either..I moved them to a separate partition /WORK which has a /home64, a /home32 (each with a virtual drive - Win7 for the 64 bit and WinXp on the 32 bit) I also have a /home where all my docs, pics etc. are kept and shared between the two distros. The /WORK partition is also shared by my swap - i.e. an extended partition.

I'm thinking of getting rid of the 32 bit distro for a while...it has nothing extra except acroread which is no onger available, but in reality no better than ocular. So I could resize and use that as a swap. But If I have to reinstall will my Windows still work..or will I have to reinstall? This really would be a pain and would probably involve lengthy sessions with a windows administrator to reinstall. 

Has anyone any experience of doing this, or does anyone know of a workaround?

Ta in advance

---

### Post by MAFoElffen on 2015-01-21
It depends on your virtual machine hyper visor, but the concept is the same. I 32bit and 64 bit VM will both work under a 64bit Virtual Hyper-visor. You install the hypervisor (virtual machine manager). 

if the same Virtual manager, you copy over the VM and virtual disk and import the VM. 

If different-- Convert the virtual disk image if needed. Then You create a new VM, and use the opton to use existing virtual disk... 

Since you are getting a new PC (complete), you could just add your old disk to it (internally or externally) and would make things simpler on tranfering or including things back in.

---

### Post by Hamburgian on 2015-01-21
Wow...quick...I'm thankful and impressed! So I just have to back up my windows folder in the VirtualBox VMs folder...that's 3 files and a folder windows.vbox windows.vbox-prev and windows.vde  + logs and it will work on a fresh install?

---

### Post by MAFoElffen on 2015-01-21
Depending on what version of VirtualBox... 4.0 and newer, all your files associated with that VM are together in the same folder. But 3.x and older was different:
[https://forums.virtualbox.org/viewtopic.php?f=35&t=55003](https://forums.virtualbox.org/viewtopic.php?f=35&t=55003)

---

