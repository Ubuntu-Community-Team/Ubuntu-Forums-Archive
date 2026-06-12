---
title: "64bit Ubuntu 12.04"
date: 2013-05-18
forum: Installation &amp; Upgrades
---

### Post by Janos1 on 2013-05-18
Hi to all.Would like to have some help with 12.04/64bit.Right now i use 32 bit,like to install 64 bit but do not want to lose any of my saved bookmark or any of my pics.Thank you for your time and help.And most important all my email setup.

---

### Post by ajgreeny on 2013-05-18
Backup your /home folder, including all hidden folders and files, to an external disk of some sort, reinstall and then restore the parts of the /home folder you need.  All your data in files in /home will work on both 32 and 64 bit systems; you don't need to worry about that.

Life is much easier if you make a separate /home partition when installing, by choosing "Something Else" at disk preparation stage,and this is what I would recommend you do.  The details are shown at [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome), though this is for an older ubuntu version.  It should still help you figure out how to do it; just be aware that some of the wording is now changed in the installer, eg the "Something Else" you will now see was then called "Specify my own partitions".

It is still worth backing up home, just in case.  Nothing has ever gone wrong for me, but - - -?

---

### Post by Janos1 on 2013-05-18
Thank you for your time,will do as you sugest.And read thru the install separate home.Thank you

---

### Post by oldfred on 2013-05-18
If you do not have a separate /home you can move yours to one.
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Also if you have installed a lot of applications, you may want to make a list to make it easy to reinstall. If old version is old you may want to houseclean list, it is just a text file to make sure you have no old kernels or old applications like OO that is now LO as you do not need both.

      
 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages

---

### Post by Janos1 on 2013-05-19
Thank you oldfred,i read yor help on most subject.

---

