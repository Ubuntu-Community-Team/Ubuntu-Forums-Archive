---
title: "Restoring your previous GRUB2 boot screen after reinstalling Windows in a simple way!"
date: 2011-07-02
forum: Installation &amp; Upgrades
---

### Post by gnome1919 on 2011-07-02
Hi guys, 

I have recently installed Ubuntu 11.04 beside Windows 7 to have both of them on demand. after some weeks I needed to reinstall Windows 7, but after that the GRUB boot screen is wiped out by Windows (obvious result after installing a greedy OS like Windows!). I have searched through the forums and net to find a solution for bringing GRUB back but all to no avail, every provided solution has failed me and ended generating an error somewhere:(! *after I gained some knowledge from all the solutions I finally find a simple way to work around my problem and I think that I should share it with other people who have this problem like me ;), here are the steps:

1) Download "Super Grub2 Disk" (1.44MB) form this link : [http://www.supergrubdisk.org/category/download/supergrub2diskdownload/](http://www.supergrubdisk.org/category/download/supergrub2diskdownload/)
(Of course there is a software like "Rescatux" as well which makes solving the problem easier but it is about 300MB in size that makes it hard to download for many users in areas with low bandwidth connection)

2) Burn the downloaded ISO image to a CD or DVD using software like Nero in Windows or K3b in Linux.

3) Start the computer using the CD or DVD which you have created.

4) From appeared menu select the first choice named "Detect any OS".

5) Now you should see all Operating Systems which you used to have before new Windows installation wiping them out.

6) Select your target Linux distribution like Ubuntu from the list.

7) After loading Ubuntu (or any other Linux distribution), mount your main drive which system uses as boot partition. In Ubuntu simply click on it at the left pane in file manager.

8 ) Open a Terminal window and type: $ sudo update-grub2
(or "$ sudo update-grub" for distributions which use GRUB instead of GRUB2)

9) Restart the computer and it's done!

Hope it could solve your problem.
Good Luck

---

### Post by charliewhizbeez on 2011-07-03
Great solution.  If you want to use the windows boot loader you could also use EasyBCD, and go to grub from there.  It's a little hard though, and I've never been able to figure it out.

I prefer grub

---

