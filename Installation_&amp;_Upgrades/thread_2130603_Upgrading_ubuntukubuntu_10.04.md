---
title: "Upgrading ubuntu/kubuntu 10.04"
date: 2013-03-29
forum: Installation &amp; Upgrades
---

### Post by jsvidyad on 2013-03-29
Hello,

    I have two systems that I need to upgrade to ubuntu/kubuntu12.04. I'm not sure whether to go in for a clean install or a network upgrade. I have had minor issues with network upgrades in the past(such as annoying messages upon logging into an user account). What are the pros and cons of each option? 

Of the two computers, one has just ubuntu 10.04 installed on it. On the second computer, I did the initial installation using a kubuntu 10.04 desktop installation disc. Then, on top of that I also installed ubuntu 10.04 by running the command "sudo apt-get install ubuntu-desktop". On the second computer, I always use Gnome and never KDE. So, how do I go about upgrading the systems to 12.04? Will there be any complications on the second computer as I have both ubuntu and kubuntu on the same system(in the same partition)?

---

### Post by oldfred on 2013-03-30
It really is just the DE that is different although if you did the full install you have all the standard apps also. I normally install k3b and KmyMoney in gnome, so I end up with a majority of the supporting files for KDE anyway.

I also have gnome-panel or fallback as I have not made the conversion to Unity. Have you tried Unity? Some like it, others are old fashioned and want menus.

I prefer clean installs. Forces a houseclean, but either way you have to have good backups. Do you have another 25GB  on hard drive? I might do a clean install to another partition and fully test new install. If you have separate /home that also works better.

But even if upgrading you need good backups. I plan a clean install when my hard drive fails, so my backup is to recover data and system settings, but not entire system.
       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

If you export the list of installed applications, you will find it very long as it includes all the depends. But you really do not want to reinstall old kernels, or OpenOffice as that has now been replaced with LibreOffice. It is just  a text list, so you can manually delete lines.
      
 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages


 Top level only - no depends (not for reinstall)
sudo apt-get install aptitude
aptitude --disable-columns -F '%p' search '~i!~M!~R(~i)' > toplevel 
or
aptitude search '?installed ?not(?reverse-depends(?installed))'

If you have any ppa's be sure to disable before hand. Many of the upgrade issues are related to ppas that may not have new versions.

---

