---
title: "Looking for help with aptondcd how to clone my system"
date: 2010-09-18
forum: Installation &amp; Upgrades
---

### Post by #1 fisherman on 2010-09-18
Hi i just have a computer with no internet connection i made a cd of all packages from my other system i would like to clone the system of the computer that has internet onto my laptop with no connection.can someone help me with instalation of the cd i created.How do install all of the packages to the laptop

---

### Post by anagor_lv on 2010-09-25
You can solve your problem using Synaptic.
Have a look at the Synaptic guide on
[https://help.ubuntu.com/community/SynapticHowto?action=show&redirect=Synaptic](https://help.ubuntu.com/community/SynapticHowto?action=show&redirect=Synaptic)
[https://help.ubuntu.com/community/Synaptic/PackageDownloadScript](https://help.ubuntu.com/community/Synaptic/PackageDownloadScript)

Here is an easy solution (I found it on the Synaptic web pages stated above):

1) create a download script on your PC using Synaptic (see the above guide)
2) save the download script to a newly created folder
3) execute the script
  (see [https://help.ubuntu.com/community/Synaptic/PackageDownloadScript](https://help.ubuntu.com/community/Synaptic/PackageDownloadScript))
   it will download the packages to a specific folder
4) Copy the contents of the folder to a CD or USB
5) Insert the CD or USB to your notebook with no Internet connection
6) Copy the folder from the CD or USB to the computer
7) Run Synaptic, select the same packages you selected on your PC
8 ) "File" -> "Add Downloaded Packages"
9) Browse to the folder you saved and open it. Synaptic will offer you to install the packages from the folder

P.S. Have a look at this thread, just for interest
 [http://ubuntuforums.org/showthread.php?t=2854](http://ubuntuforums.org/showthread.php?t=2854)
 
Anything unclear? Post a question, I will try to help!

---

