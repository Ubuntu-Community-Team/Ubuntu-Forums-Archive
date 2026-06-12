---
title: "Problem with adding the cdrom to /etc/apt/source.list"
date: 2011-08-09
forum: Installation &amp; Upgrades
---

### Post by nandan.pc on 2011-08-09
Hi, 
I wanted my customised cd to be detected for installing the packages . 

so i used : 

sudo apt-cdrom add --auto-detect 

command so that the i can add the cd to /etc/apt/source.list file  
I referred [http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html)
for apt-cdrom command . 

But i am getting following error. 


> root@nandan:/media/apt# apt-cdrom add --auto-detect 
Using CD-ROM mount point /media/apt/
Identifying.. [aeb6648ae3fd5da22717eb5f409dd972-2]
Scanning disc for index files..
Found 1 package indexes, 0 source indexes, 0 translation indexes and 0 signatures
Found label 'Custom Live CD - Release i386'
This disc is called: 
'Custom Live CD - Release i386'
Copying package lists...E: Unable to stat the mount point /media/Custom\040Live\040CD/ - stat (2: No such file or directory)
E: Could not open file /media/apt/Packages.gz - open (2: No such file or directory)
E: Unable to stat the mount point /media/Custom\040Live\040CD/ - stat (2: No such file or directory)please can anybody help me :)

---

