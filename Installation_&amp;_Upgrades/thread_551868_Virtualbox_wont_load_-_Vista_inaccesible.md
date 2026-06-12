---
title: "Virtualbox wont load - Vista inaccesible"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by 2fried on 2007-09-15
I have Vista installed with Virtualbox on Ubuntu Feisty and it was working fine until I got the following message:


Could not load the settings file '/home/phil/.VirtualBox/Machines/Vista/Vista.xml' (VERR_OPEN_FAILED).
FATAL ERROR: Invalid character in attribute value serialnumber (Unicode: 0x4)
Location: '/home/phil/.VirtualBox/Machines/Vista/Vista.xml', line 39, column 188.


Result Code: 
0x80004005
Component: 
Machine
Interface: 
IMachine {0332de0e-ce75-461f-8c6f-0fa42616404a}

 I can't even find that file on my machine.  Have I lost something?  Any help would be appreciated

---

### Post by apureevil1 on 2007-09-24
I got that same error today, I deleted the vista machine from the virtualbox dashboard, I then started a new install however I reloaded the existing vista vdi drive and it works fine again. hope this helps

---

