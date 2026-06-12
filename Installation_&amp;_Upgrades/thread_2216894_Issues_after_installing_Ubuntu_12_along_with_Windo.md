---
title: "Issues after installing Ubuntu 12 along with Windows 7"
date: 2014-04-14
forum: Installation &amp; Upgrades
---

### Post by tomz123 on 2014-04-14
Hi ,

I`ve installed Ubuntu 12x on my machine which already has Windows 7. 
As per recommendation i had installed and partitioned the available space in my machine for / , /boot and /home.

However once I reboot I do not get the option to choose Ubuntu.Windows automtically boots.

Can someone let me know if I missed something while installation.
Note: While installation there was no option asked to install along with Windows !!!!!.



Thankyou in advance.

---

### Post by su:bhatta on 2014-04-14
Hi and welcome to the forums.
I am assuming you have tried to install either 12.04 or 12.10.

In either case you should have got the screen which asks you where to install Ubuntu and it should have displayed 'Install Along side Windows'.
If that screen was not given how and where did you choose to install Ubuntu?

Did you check the downloaded ISO for errors?

Please give details of your machine: CPU, RAM, Graphics card, etc !
Does your machine have UEFI boot?

---

### Post by Mark Phelps on 2014-04-15
You should start by booting from Ubuntu install media, opening a terminal, and entering "sudo fdisk -lu" (lowercase L, not a one).  This will list out the partitions and filesystems on your drive.  Post that information back here so we can see how your drive is organized.

---

