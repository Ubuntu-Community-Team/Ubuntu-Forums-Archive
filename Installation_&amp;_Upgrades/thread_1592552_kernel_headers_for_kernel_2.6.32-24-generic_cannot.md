---
title: "kernel headers for kernel 2.6.32-24-generic cannot be found"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by sibyphilips on 2010-10-10
hi,

I upgraded from Lucid to 10.10 today,

I had installed Kubuntu desktop from the synaptic in Lucid (earlier) and then upgraded from within KUBUNTU,

after the upgrade my grub menu (I use a dual boot with Vista) shows that I am using
kernel 2.6.32-24

but actually all the headers were removed during the upgrade

when I tried to "dpkg --configure -a" after the upgrade it shows:


warning, in file '/var/lib/dpkg/status' near line 52092 package 'virtualbox-3.1':
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/status' near line 52093 package 'virtualbox-3.1':
 error in Config-Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
warning, in file '/var/lib/dpkg/available' near line 66890 package 'virtualbox-3.1':
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number

and when I try this...(since my graphics was broken)[COLOR=#000000]sudo apt-get install build-essential linux-headers-$(uname -r) [/COLOR]I get this following error..

 Error! Your kernel headers for kernel 2.6.32-24-generic cannot be found at
/lib/modules/2.6.32-24-generic/build or /lib/modules/2.6.32-24-generic/source.

also I cannot open any folders because once I click them it directs me to the archive manager and says that this type of archive is not supported 

can anyone help....

I am not sure if I am posting in the correct place, and without help I think I will be lost...

thanks,
siby.

Hi 
sorry for being impatient and posting in a rush, 


I later found out the problem, my Grub "menu.lst" was not showing the new kernel 2.6.35- so I did a "update-grub" following this thread
[http://ubuntuforums.org/showthread.php?t=1527492](http://ubuntuforums.org/showthread.php?t=1527492)

and later edited the updated grub menu.lst to automatically show up at the begining following

[http://www.easy-ubuntu-linux.com/grub-menu-visible.html](http://www.easy-ubuntu-linux.com/grub-menu-visible.html)

now the system is working fine, although the KDE graphics are broken, hope to solve it by an update.
thanks,
siby.

---

