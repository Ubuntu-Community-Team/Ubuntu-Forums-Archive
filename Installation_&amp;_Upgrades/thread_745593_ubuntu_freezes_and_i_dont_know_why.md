---
title: "ubuntu freezes and i dont know why???"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by wtes71 on 2008-04-04
My ubuntu has been freezing a lot. lately and it wont let me download updates. It tells me to do a parital upgrade then said

 Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first. 

Problem is I dont know how to close it. I try and it said I don't have super user privileges 
Please Help Me

---

### Post by Pumalite on 2008-04-04
Copy and paste here the output of:
sudo apt-get update
sudo apt-get upgrade

---

### Post by wtes71 on 2008-04-07
I did that and this is what it gives me
 dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
I dont know what that means
Help Please!!!!!!

---

### Post by Pumalite on 2008-04-07
Run at the Terminal:
sudo dpkg --configure -a
Post the output here.

---

### Post by wtes71 on 2008-04-10
wally@wally-desktop:~$ sudo dpkg --configure -a
[sudo] password for wally:
Setting up language-pack-en (1:7.10+20080229) ...
Setting up language-pack-gnome-en (1:7.10+20080229) ...
wally@wally-desktop:~$ 

Last time I try this or what it said to run It told me I did not have super privileges?

Thanks agian for helping

---

### Post by Pumalite on 2008-04-10
Can you install anything at the command line now?

---

### Post by wieman01 on 2008-04-10
Do you use wireless networking and 'ndiswrapper' by chance?

---

