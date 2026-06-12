---
title: "I hate the Ubuntu 12.04 upgrade"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by xxwikkixx on 2012-04-27
Hey everyone

I just upgraded my ubuntu from version 11.10 to 12.04 even though i love ubuntu and use it everyday this thing is giving me all sorts of errors and stuff. its annoying me while i am doing work. i cant even run the update manage anymore this is the error i get :
```
'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
```

my ubuntu software center opens up for a second then crashes and closes. 

i try ti run sudo apt-get update in terminal and it goes but in the end it gives me couple of errors that it cant open this and that....:confused::confused::confused:

please help me out here cause this is annoying :(

---

### Post by jadtech on 2012-04-27
> **xxwikkixx said:**
> Hey everyone

I just upgraded my ubuntu from version 11.10 to 12.04 even though i love ubuntu and use it everyday this thing is giving me all sorts of errors and stuff. its annoying me while i am doing work. i cant even run the update manage anymore this is the error i get :
```
'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
```

my ubuntu software center opens up for a second then crashes and closes. 

i try ti run sudo apt-get update in terminal and it goes but in the end it gives me couple of errors that it cant open this and that....:confused::confused::confused:

please help me out here cause this is annoying :(

try this code in a terminal looks like you are another who has an incomplete install hope it helps  ..

```
  sudo apt-get dist-updgrade -f 
```

---

### Post by xxwikkixx on 2012-04-27
i just tried it and this is the error i got :S
```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```

---

### Post by xxwikkixx on 2012-04-27
Bump can someone please help me out

---

### Post by nd456 on 2012-04-27
I've had this issue in 11.10 and fixed it by deleting the additional reposity lists, sarting it up (sucsessfully), then re-adding the sources... This is assuming you added outside sources to the software center... the list should be in 
/etc/apt/sources.list Sorry if this dosn't apply.

---

### Post by Murphy1138 on 2012-04-27
If you can copy your data (docs/downloads etc) to another hard drive or external drive - then I would wipe and start again.

Ive had an upgrade go smooth and upgrades go bad, some times the old "format C: and reinstall" is quicker and less frustrating that trying to fix a linux mess.

---

### Post by jdeca57 on 2012-04-27
The easiest way? Download the installation CD and go from there. Of course, make a backup and make a note of what special software you might use. If your /home has a separate partition this could also be the quickest way. Upgrading the system is all right - I did it that way - but never 100% certain.

---

### Post by kansasnoob on 2012-04-27
I know this was written for 11.04 but the principle should be the same:

[http://ubuntuforums.org/showpost.php?p=10780434&postcount=7](http://ubuntuforums.org/showpost.php?p=10780434&postcount=7)

---

### Post by xxwikkixx on 2012-04-27
Alright i got it fixed even though none of ur options worked but thanks for the help :). 

now to fix it all i did was run this 
```
gksu update-manager
``` 
from there i let it do the partial upgrade. then i went in the properties and changed some options from USA server to main server and ran this same command line again. now everything is working in right order. 

there are couple of things that crash once in a while such as the docky, or clementine but it works right now :D

so if u have the same situation as i do try this it might help cheers :popcorn:

P.S and what kansasnoob said could also work but i didnt try that :P. I love ubuntu 12.04

---

### Post by QIII on 2012-04-27
Murphy1138 and jdeca57 --

In my opinion, the "Blast off and nuke 'em from orbit!" method of solution by reinstalling is a last resort.  (Both in Linux and Windows.)

That should not be the first thing we suggest.  It does not solve a problem, it avoids it.

As it is, it seems that the OP has demonstrated that point by finding a solution to most of the issue.  He has also provided other users with a potential answer to their problems, which has served the entire community well.

---

### Post by techsupport on 2012-04-27
> **Murphy1138 said:**
> If you can copy your data (docs/downloads etc) to another hard drive or external drive - then I would wipe and start again.

Ive had an upgrade go smooth and upgrades go bad, some times the old "format C: and reinstall" is quicker and less frustrating that trying to fix a linux mess.

Sometimes it is just faster and less frustrating to do a fresh install after an unsuccessful upgrade to the next release. That is also from my own experience with release upgrades, and it is compounded by the fact that some of these Ubuntu users who are upgrading to the next release, don't really know how to fix their problems when they occur.  Sometimes the only way is to do a fresh install.  It may be the last option for technically knowledgeable users, and for users who don't know how to fix their own installs, it is the only option.  Just sayin'

---

### Post by DaveDixon on 2012-07-08
It's well and good to say that the nuclear option should be last resort, but apparently the only way to get OpenVPN to work is to downgrade :(

---

