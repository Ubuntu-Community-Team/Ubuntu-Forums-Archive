---
title: "Installing KDE4.1 on Ubuntu from alt CD?"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by xenomorph99 on 2008-09-01
Hi

I have downloaded the latest Kubuntu alternative install CD and wonder if I can install KDE4.1 to my existing Ubuntu installation via this CD?

Or is it only possible via the internet?

If it is possible to do it via the CD, could someone please post the relevant steps or point me to some resource that already exists? I had a search around but couldn't find anything relevant.

TIA
X

---

### Post by arch0njw on 2008-09-02
You need to add a repository and point to the CD.

Put the CD in the drive, and try going into your add-software program.  See if the CD is listed as a repository.  Use the tips here to add a repository:  [https://help.ubuntu.com/community/Repositories/Ubuntu#Editing%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Editing%20Repositories)

If it is not, you can try a couple of things:
1. at the command line:  "sudo apt-cdrom add" <-- that should add the CD as a source
-OR-
2. directly edit the /etc/apt/sources.list file.  PLEASE make a backup first.  As long as all you do is add things, you can always comment those lines out.  Add a line that looks like

[LIST]
[*]"deb file:/media/[your cd drive]/ hardy main restricted" (e.g., deb file:/media/cdrom0/ hardy main restricted)
[*]deb cdrom:[description of cd]/ hardy main restricted (e.g.,"deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted")
[/LIST]
 
I am not 100% sure of the exact syntax to manually add the line for a file or a CD.  I got my ideas from here:
[https://help.ubuntu.com/community/Repositories/Ubuntu#Editing%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Editing%20Repositories)
[http://ubuntuforums.org/archive/index.php/t-290636.html](http://ubuntuforums.org/archive/index.php/t-290636.html)
[http://odzangba.wordpress.com/2007/01/10/how-to-use-ubuntu-cd-images-as-additional-software-repositories/](http://odzangba.wordpress.com/2007/01/10/how-to-use-ubuntu-cd-images-as-additional-software-repositories/)

Hope that helps.

---

