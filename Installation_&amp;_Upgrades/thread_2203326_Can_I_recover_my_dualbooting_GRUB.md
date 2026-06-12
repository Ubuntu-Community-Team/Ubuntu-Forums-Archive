---
title: "Can I recover my dualbooting GRUB"
date: 2014-02-02
forum: Installation &amp; Upgrades
---

### Post by JohnBlood on 2014-02-02
I bought an old HP SlimDesktop to play with linux. I installed Pear OS 8, UbuntuGnome 13.10 and Fedora 20. I uninstalled Fedora and installed PCLinuxOS. Unfortuneately, I was not paying attention and told PCLinuxOS to install a graphicall GRUB. I restared after the install only to find PCLinuxOS the only option. I booted to a LiveUSB version of UbuntuGnome, installed Boot-Repair and ran the recommended repair. Now when it boots up, it only has Pear OS 8. When I load GParted to check to see if the UbuntuGnome partition still exists, I get this message: "Invalid argument during seek for read on /dev/sda". When I boot from the UbuntuGnome LiveUSB to reinstall UG it says that it does not detect any other OS. Do I need to reinstall both Pear OS and UbuntuGnome? Please help. Here is the information that Boot-Repair gave me: [http://paste.ubuntu.com/6864671/](http://paste.ubuntu.com/6864671/).

---

### Post by sudodus on 2014-02-03
Welcome to the Ubuntu Forums :-)

If you are still experimenting, and have no important data on the HDD (photos, documents etc), I think it will be much easier to reinstall everything instead of repairing it.

Otherwise you can choose between backing up your important data and reinstall or repair the system.

But if you want to climb the steep learning curve, you can choose to repair, even if reinstalling would be easier.

-o-

And when you reinstall, you should always install the least intelligent system first (systems that do not recognize other systems, overwrite or ignore them)
;-)

---

### Post by oldfred on 2014-02-03
You show this:

 Invalid MBR Signature found.
EBR refers to a location outside the hard drive.

I would try fixparts and see if that can fix MBR, then try Boot-Repair again.

      
 Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by JohnBlood on 2014-02-03
I'm going to take sudodus' advice an just reinstall. It will be quicker in the long run.

---

