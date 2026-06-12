---
title: "can't access certain admin functions since gutsy upgrade"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by timczer on 2007-12-15
I recently upgraded to gutsy and now can't access some admin functions.

I cannot get into restricted drivers manager, software sources, and gdebi will not open a deb file.  Other admin functions I can get to, network manager for example, and I can install packages through synaptic.

When I open the  functions that don't work, it takes my password, but then doesn't do anymore.  

Any ideas on what I can do to get full access would be appreciated.

---

### Post by src2206 on 2007-12-16
Did you try to change options in your USER accounts through the menu?

---

### Post by timczer on 2007-12-16
I haven't changed anything since the upgrade.  

A couple of strange things though.  When I look at users and groups, under group settings, all of the groups are listed like 4 times.  Root, my user, admin all are listed several times.  

Also, I have my normal home folder, but under media, there is now a folder called /_home that has some of the settings you would see in your Home folder (.bashrc, .ICEauthority, etc).  These files also show up in my actual home folder.  

What's more, if I go to my Places menu, and select home it takes me to my actual home folder.  If I click on Computer, it lists as a mounted volume /home.  Clicking on this takes me to the /_home folder in /media.  

I think maybe this additional home folder is perhaps causing or symptomatic of the problem. It seems that many of the programs that need admin privileges (restricted driver manager) will not run (although they ask for the password, and then don't run afterwards).  I am not sure why synaptic runs fine though.

---

### Post by #!/bin/bash on 2007-12-16
Make sure you own all your files. Open xterm and su root, then:
cd /home
chown -R user.user user
Where user is your username

---

### Post by timczer on 2007-12-16
I tried running the chown command as suggested, but that didn't help.

The problem appears to be related to the GTK issue I reference in this post: [http://ubuntuforums.org/showthread.php?t=641919]("http://ubuntuforums.org/showthread.php?t=641919")

So between the extra /_home folder, and the error messages referring to GTK issues, I am not sure what is going on. 

Any other suggestions?

---

