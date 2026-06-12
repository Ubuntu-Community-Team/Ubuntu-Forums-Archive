---
title: "Package Error"
date: 2011-08-09
forum: Installation &amp; Upgrades
---

### Post by snav3 on 2011-08-09
Hi, I have been having a hard time with my Ubuntu OS it's been  giving  me an error in the system but as it tries to make an error report  it  fails the reason being it can't identify the packet id.
Here the example of the error i've been getting while trying to update or install packages,
when using the terminal
**sudo apt-get install f-** 
or 
**sudo apt-get install 3kb**
<this is what it gives>

[B]'E: Encountered a section with no Package: header 
 E: Problem with MergList/var/lib/apt/lib/apt/list/extras.ubuntu.com_ubuntu_dists_natty_main_i18_Tran  slation-en
 E: The package lists or status file could not be parsed or opened.'
  
[/B]Tried the Update manager within the Ubuntu OS but as it  loads it   gave me the same error report but this time stating I should report this   to the 'update-manager' 

Please do advise,Evans. :confused:

---

### Post by jerrrys on 2011-08-09
to remove corrupted files

 sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

---

