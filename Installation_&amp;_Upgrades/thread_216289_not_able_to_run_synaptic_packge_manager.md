---
title: "not able to run synaptic packge manager"
date: 2006-07-15
forum: Installation &amp; Upgrades
---

### Post by nishant on 2006-07-15
hi everyone

i m not able to run synaptic package manager(SPM).

d problem i m getin is dat when i click on (SPM) it is akin for passwd. after entering passwd nothing is appearing. if i try again to start it it not starting dat is not askin 4 passwd.




pls help me out as fast as possible

---

### Post by rcarring on 2006-07-15
Sounds like the user you have setup is not authorized to perform system admin tasks.

When you installed Ubuntu did you create a user or are you using an out-of-the-box virtual machine image?

It may be possible to boot the machine in rescue mode, which will put you in as root@nameofyourmachine, then you can do startx, and when the desktop loads, go to user maintainance on the Admin menu in Gnome (dont know for Kubuntu) and make sure that your user is in the admin group and that you can perform system admin tasks. Once done, reboot and see if you still have the problem.

---

### Post by arkangel on 2006-07-15
try to run in the console  #sudo synaptic

if it doesnt work   try to reinstall (it might be a good idea to remove it first #sudo apt-get remove synaptic) 
#sudo  apt-get install synaptic

---

