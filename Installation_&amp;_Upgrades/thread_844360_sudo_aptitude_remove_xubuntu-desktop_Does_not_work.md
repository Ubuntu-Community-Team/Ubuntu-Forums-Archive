---
title: "sudo aptitude remove xubuntu-desktop Does not work"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by eniel on 2008-06-29
Hello,

I have installed ubuntu Hardy
Then I installed the xubuntu dektop with:
	sudo aptitude install xubuntu-desktop
This worked, then I tried to uninstall it with:
	sudo aptitude purge xubuntu-desktop
and with
	sudo aptitude remove xubuntu-desktop

This simply did not work. xubuntu is still there
When trying to remove I get the the following messages:

 sudo aptitude remove xubuntu-desktop (purge giving the same result)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      

I always thought that when you install a desktop with aptitude it was easy to remove.
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
[http://ubuntuforums.org/showthread.php?t=129517](http://ubuntuforums.org/showthread.php?t=129517)
[http://ubuntulinuxhowto.blogspot.com/2006/06/how-to-install-other-desktop.html](http://ubuntulinuxhowto.blogspot.com/2006/06/how-to-install-other-desktop.html)

Can someone explain to me if I misunderstood something, Thanks.
(Since I have a backup of the system before installing xubuntu I'm mainly interested in understanding what is happening)

---

### Post by dexter.deepak on 2008-06-29
have you checked whether you are "really having" xubuntu...meaning , it might be the case that you have the session option as "xubuntu", but you cant actually log in.

---

### Post by eniel on 2008-06-29
I've actually logged in into xubuntu to check this. 
I also have removed xubuntu by purging all packages I had installed
sudo aptitude purge <list of all installed packages>
After this ubuntu was restored.
I'm sure I really installed xubuntu since this was not the first try. The first time I installed xubuntu I've been playing around with it.
Furthermore I did the same thing with kubuntu (aptitude install and aptitude remove) and there the removal failed too.
It looks to me as if aptitude purge or aptitude remove does not work for the metapackages xubuntu-desktop or kubuntu-desktop

---

