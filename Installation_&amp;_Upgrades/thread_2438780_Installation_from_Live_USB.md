---
title: "Installation from Live USB"
date: 2020-03-18
forum: Installation &amp; Upgrades
---

### Post by karthyyy on 2020-03-18
Hi all,
 
   I am trying to install Ubuntu+Some programs to a PC which doesn't have internet connectivity. So I installed all my required programs onto a live USB (Ubuntu 16.04) with persistence from a PC which has internet connection. But when I installed the OS from the live USB to the PC (without internet) the installed programs are not showing at all. But those programs are still there in the casper-rw drive. How to retrieve the same ?. If I try to run the OS as live with persistence from the PC without internet all the programs are still working. Any work around for the same ?

  Thanks and Regards
     Karthik R

---

### Post by tea for one on 2020-03-18
Cubic will possibly help with your project.

[https://launchpad.net/cubic](https://launchpad.net/cubic)

A quick search on the internet will provide you with some advice/tutorials.

Good luck

---

### Post by yancek on 2020-03-18
Just because you have some software installed don the live Ubuntu with persistence does not mean they will be installed when you use that usb to install Ubuntu.  It doesn't copy everything from the usb but uses what the installer (ubiquity) installs by default.  If you have some program installed on the persistent usb, you might be able to then also copy them to the newly installed system but you would have to post detailed information on what they are.  Much software has dependencies required to be used.  This is most certainly not the standard or recommended way to install software.  

I'm not really sure what your end goal is as the persistent usb works.  Do you want it on another computer?

---

### Post by karthyyy on 2020-03-18
Hi,
  Wow. I think that's exactly what I need. I ll try to experiment with Cubic and see what can I do. Thanks a lot for pointing out this.
   Regards
       Karthik R

---

### Post by ubfan1 on 2020-03-18
Look in the live installer's /var/cache/apt/archives to see if you still have the package files you installed.  Use them to reinstall where you want.

---

### Post by C.S.Cameron on 2020-03-19
You can easily copy the home folder from a Persistent USB to an installed system using rsync or Grsync if you prefer a GUI.
This will copy all your settings and home data over. You would then only need to reinstall your third party programs.

---

