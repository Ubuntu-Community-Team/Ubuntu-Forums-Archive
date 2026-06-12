---
title: "add &amp; remove programs error"
date: 2005-05-18
forum: Installation &amp; Upgrades
---

### Post by n21roadie on 2005-05-18
when i opened ad & remove programs i got this error message =

W: Couldn't stat source package list [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by Xian on 2005-05-18
You generally just need to click on the "Reload" icon in Synaptic.
If this doesn't work then post back with what happens.

---

### Post by slow learner on 2005-06-29
I can't see the list of programs ---> Applications->System Tools->Add/remove Programs

The window is blank and the cursor has the waiting/busy clock icon.

If i click on the advanced tab the synaptic will open.

Is there away for the program list to be shown?


thanks

---

### Post by Tad030 on 2005-07-10
[QUOTE=slow learner]I can't see the list of programs ---> Applications->System Tools->Add/remove Programs

The window is blank and the cursor has the waiting/busy clock icon.

If i click on the advanced tab the synaptic will open.

Is there away for the program list to be shown?


thanks[/QUOTE]

I'm also having this problem.

---

### Post by Tad030 on 2005-07-10
[QUOTE=Tad030]I'm also having this problem.[/QUOTE]
 Anyone? Anyone?  Beuller?  :)

---

### Post by Raos on 2005-07-10
I get something similar, when I try to install just about anything using synaptic or apt-get in terminal, I get [ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz:](ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz:) MD5Sum mismatch

and

W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)

when I'm running apt-get in terminal,depending on what I'm doing, it always tells me to run either apt-get update or apt-get upgrade, but I have the exact same problems when running update or upgrade.  I get both messages from update, and the second from upgrade.

---

### Post by Tad030 on 2005-07-11
This problem didn't start occuring until after I edited the code to add more repositories.  I did this to install java, and some other programs.  I followed the instructions in the unofficial ubunto guide, so if anyone else knows if there is a relationship between the two, that would be great.

---

### Post by tenn on 2005-07-14
I just thought I would add I also have that problem with the add/remove programs, refresh in the synaptic does not fix it.

---

### Post by varunus on 2005-07-14
The problem with the gnome add and remove programs is a known bug.  There was a patch floating around somewhere on the wiki that fixed it.  It involved a new version of Python (I think having SMEG caused it) that caused problems with gnome-app-install.

I remember getting it from these forums or the wiki, and installing it, and it fixed my problem.  Do a search for it.

---

### Post by Ubunted on 2005-07-21
I've been having the problem with Add Remove Programs not displaying anything as well. This isn't the first time I've installed Ubuntu but it is the first time this has happened.

I tried serching the forum and wiki but came up blank. Anyone have a link to this fix?

---

### Post by racecat on 2005-07-21
Maybe I'm missing something, but in my limited playing around with removing packages, if you click on the filled in check box beside the package (in Synaptic) you want to remove, a drop down box apears with "Mark for removal" and "Mark for complete removal". This seemed to work fine.

If this is the wrong approach, somebody please correct me.

B

---

### Post by Xian on 2005-07-21
[QUOTE=racecat]If this is the wrong approach, somebody please correct me.[/QUOTE]
They are discussing a different package management GUI called "Add & Remove Progams". It works on top of the apt environment just like Synaptic but the front end has a different interface. It is generally accessed in Gnome from the main panel and appears in the notification area when there are system updates.

---

### Post by racecat on 2005-07-21
Coming from the Microsoft world, my first instinct was to use add and remove programs. It didn't work for me, either.

I'm still feeling my way around. This forum is a wealth of information, thanks to you and other contributors.

Thanks,
B

---

### Post by Yoshimitsu8 on 2005-07-23
I'm having the same problem as well. I checked out the wiki, no dice. It stopped working for me after I updated the repository as well, and after I installed the newest verison of Firefox.

---

### Post by saltydog on 2005-07-23
Here it is the patch:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=11871](https://bugzilla.ubuntu.com/show_bug.cgi?id=11871)

---

### Post by Ubunted on 2005-07-23
Beautiful! Thank you.

---

### Post by installer on 2005-07-24
Please ignore post

---

### Post by Fummie on 2005-07-30
[QUOTE=saltydog]Here it is the patch:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=11871](https://bugzilla.ubuntu.com/show_bug.cgi?id=11871)[/QUOTE]
OK, i've downloaded the patch but now what do I do with it?
I'm very lost here.  :confused:

---

### Post by ellingtn on 2005-07-31
Now that you've downloaded the file, gnome-app-install-v3.tar.gz. Extract the contents. You should see a file titled, install.txt, in a new folder 'gai'. Read the install instructions. You can either run 'make install' or use install-gai.sh. You will have to do the install as root or sudo....

---

### Post by Fummie on 2005-07-31
[QUOTE=ellingtn]Now that you've downloaded the file, gnome-app-install-v3.tar.gz. Extract the contents. You should see a file titled, install.txt, in a new folder 'gai'. Read the install instructions. You can either run 'make install' or use install-gai.sh. You will have to do the install as root or sudo....[/QUOTE]
Thanks for your help, heirno just beat you.  ;-) 
[http://www.ubuntuforums.org/showpost.php?p=279761&postcount=29](http://www.ubuntuforums.org/showpost.php?p=279761&postcount=29)

---

### Post by ozmont on 2005-08-15
OK, you get these errors when either the repo is down (marillat is quite often down, or just too busy) or you don't have the GPG key (google ubuntu gpg key for info).
I strongly suggest you look up the unofficial ubuntu install guide and CD. It is a great CD to have, with tips and trickes and a whole lot of help with installing everything from Java to enabling repositories. 
for some weird reason, I'm logged in as ozmont, but i am roxville!
 :smile:

---

