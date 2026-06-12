---
title: "Installed on my Razr Maxx but wont download SSH?"
date: 2012-03-24
forum: Installation &amp; Upgrades
---

### Post by grandkodiak on 2012-03-24
Ive installed ubuntu on my Droid Razr Maxx and while trying to install openssh-server I get this:
 
root@localhost:/# apt-get install openssh-server
apt-get install openssh-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
libbeagle1 python-dev python-nautilus python2.6-dev
Use 'apt-get autoremove' to remove them.
Suggested packages:
rssh molly-guard openssh-blacklist openssh-blacklist-extra ufw
The following NEW packages will be installed:
openssh-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 284kB of archives.
After this operation, 733kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
openssh-server
Install these packages without verification [y/N]? y
y
Err [http://ports.ubuntu.com](http://ports.ubuntu.com) karmic/main openssh-server 1:5.1p1-6ubuntu2
404 Not Found
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/o/openssh/openssh](http://ports.ubuntu.com/ubuntu-ports/pool/main/o/openssh/openssh)
-server_5.1p1-6ubuntu2_armel.deb 404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-mis
sing?
root@localhost:/#
 
 
Without that running, there is no way to access the GUI from the androidVNC app etc). I've tried "apt-get update" but the problem remains. How do I use the "--fix" it mentions?
 
Thanks all!

---

### Post by ajgreeny on 2012-03-24
That is because karmic is no longer supported.  You will need to install a newer version of ubuntu.

---

### Post by grandkodiak on 2012-03-24
Don't know how to do that unfortunatly, the image and .sh are supplied in the instructions. I've only installed on PC before, its far more stright forward in my book...I think the image is taylored to work on the droid phone, it mentions running on a loop and on the ARM platform and has a .sh that does it all for you basically once you have the image on a memory card. I wouldn't know where to even begin without a click here type this step by step otherwise, making roms, building kernels...however its done its all beyond me. I'm a click setup.exe and let the OS do the work for you kinda guy :)
 
 
I did find this though
 
[http://aacable.wordpress.com/2011/12/02/howto-solve-ubuntu-9-10-karmic-koala-apt-get-not-updating-error/](http://aacable.wordpress.com/2011/12/02/howto-solve-ubuntu-9-10-karmic-koala-apt-get-not-updating-error/)
 
But gedit doesn't work since there is no GUI and I can't install nano for the same reason I can't install openssh-server since the repository whatevers are out of date or no longer supported.
 
is there any other way of editing the sources.list via the command line or some other method, or any way to download an installation file for openssh-server, put it on the memory card and install it from there?
 
thank you!

---

### Post by ajgreeny on 2012-03-25
You can try using the info on [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) to allow you to change your software sources and install packages from the end of life repos for karmic, though they will be those that were current at the time of the distros loss of support, and will not be updated any more after you have got to that point.  It should, however, allow you to install openssh-server and/or client and then it's over to you.

I didn't even realise that the hardware you are talking of was a mobile phone, at least I think it is?

---

### Post by grandkodiak on 2012-03-25
Success! I know have it all up and running! Yup, its running gnome on karmic on my Droid Razr Maxx phone!
 
I ended up deleting the image from the phone card, and starting from scratch again. Before doign an apt-update, I deleted the etc/apt/sources.list and used "vi" to type in what was listed on the link for old sources (deb [http://old-resources.ubuntu.com/ubuntu/](http://old-resources.ubuntu.com/ubuntu/) karmic main restricted" universe, multiverse, security etc. etc.) then ran apt-update, then apt-get install for openssh-server and tightvncserver, ran that and used a droid vnc program to connect in to the gui! even firefox works!!
 
awesomeness, thanks all!

---

### Post by pacman377 on 2012-05-28
Ive been attemping to install Ubuntu on my Razr as well. What rom are you using. Im running Eclipse 1.3 and when I type sh ubuntu.sh it will say something  about no more than 255 apps blah blah blah. Then it says chmod shuting down? I tried on Axiom and it went through but when it got to the part where it said this may take a while I stayed there for nearly 30 min. Sorry for being so vauge on some things, but Im at work not at my house so Im just tring to remember what everything said.

---

