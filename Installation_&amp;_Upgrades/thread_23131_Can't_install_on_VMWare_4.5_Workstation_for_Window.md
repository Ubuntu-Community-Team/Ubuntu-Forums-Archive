---
title: "Can't install on VMWare 4.5 Workstation for Windows"
date: 2005-03-31
forum: Installation &amp; Upgrades
---

### Post by adwolf1 on 2005-03-31
Here's a stumper...

Trying to install using VMWare 4.5 Workstation for windows,  the system gets as far as the partitioning step, but then says it can't find any suitable disc to partition.

I even tried writing over a previously-good virtual machine with mandrake already installed, to see if it could see that disc, but it couldn't.

I've never seen this sort of a problem on installing a linux distro, any help would be appreciated!

(BTW, the live CD works perfectly on the same copy of VMware. Hoary looks amazing!)

---

### Post by lao_V on 2005-03-31
I was just waiting for someone to ask this question because i have the solution :-)

Here it is...
When creating your virtual disk, chose custom and when asked to select the type (ide/scsi) chose **ide** then try to re-install your ubuntu!

Let us know how it goes!

---

### Post by adwolf1 on 2005-04-01
that did the trick, thanks!

---

### Post by adwolf1 on 2005-04-01
on a similar note, i can't get vmware-tools installed, even following the directions given in other threads.  Definitely worth a 'how-to' if i can figure it out..

---

### Post by lao_V on 2005-04-01
I've found it a real pain to install vmware-tools on a number of distros now. It almost destroyed a number of them after installing it! 

If you are installing them after logging into gnome/kde then you will have to nip into another terminal by pressing ctrl-alt-space-f2 and follow the instructions in vmware help. One time where I managed to install it perfectly (on FC3 i think), I didn't really find any use of the tools. 

So good luck!

---

