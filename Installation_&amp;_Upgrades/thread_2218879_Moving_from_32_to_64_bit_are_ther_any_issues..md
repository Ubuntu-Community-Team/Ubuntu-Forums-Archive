---
title: "Moving from 32 to 64 bit are ther any issues."
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by Morganman on 2014-04-22
Hi All
I have been happily running Ubuntu since 9.10
Up to press I have used the 32 bit version although my machine is a dual core 64 bit.

I am currently running 12.04 and am considering moving to 14.04.
I would like to move to 64 bit at the same time but am not sure if it is possible to go from 32 to 64 bit as an upgrade without a clean reinstall and if I can what likely problems might I encounter.

Thanks in advance

---

### Post by Topsiho on 2014-04-22
I am quite sure that you should do a clean install, using the 64-bits .iso of Ubuntu 14.04 LTS.

Topsiho

---

### Post by grahammechanical on 2014-04-22
I switched from Ubuntu 32bit to Ubuntu 64bit on my Intel dual core many years ago. But you need to do a clean install. We have no other option. It is simple and smooth to install Ubuntu. Many of us would recommend a fresh install instead of upgrading from 12.04 to 14.04 whether it is 32bit or 64bit. Just deactivate any proprietary video driver and take the user interface back to its default settings. Disable any PPAs and be prepared to reinstall any applications that are not part of a default install. Oh, and backup your data.

Regards

---

### Post by oldfred on 2014-04-22
I did the same as grahammechical. 
I used 32 bit with my new in 2006 CoreDuo build until I totally reinstalled to 64 bit with 9.10. I just installed in a new partition 14.04, but still have 12.04 as my main working install.
When I did my upgrade I also added a new large (in 2009) 640GB drive and made both data partitions and multiple 25GB partitions for / (root). So I could have several test installs.

You should backup /home. And backup any settings in /etc that you may have manually changed, but you may or may not need those with a new install.
You may want to backup a list of installed applications, but from an older  install you may also want to edit it to not install applications that have changed. It is just a text file, but long as it also has the lower level files also. If it includes any kernels delete those as you do not want those old ones.

       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

    
This is not an installable list, but you can install aptitude and just export a list of top level apps. Much shorter list.
 Top level applications:
aptitude --disable-columns -F 'no_dependents %p' search '~i!~M!~R(~i)'
sudo aptitude --disable-columns -F '%p' search '~i!~M!~R(~i)' >toplevelonly

---

