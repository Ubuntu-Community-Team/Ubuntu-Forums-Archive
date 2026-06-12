---
title: "Can't install or update software in VirtualBox Ubuntu"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by biosol on 2011-05-01
I have installed both 32 and 64 bit versions of Ubuntu 11.04 in VirtualBox 4.0.6 and have installed the VBox Additions.  When I try to add new software or update software I get a package operation failed error.

installArchives() failed: Setting up tzdata (2011g-0ubuntu0.11.04) ... 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109. 
dpkg: error processing tzdata (--configure): 
 subprocess installed post-installation script returned error exit status 128 
Errors were encountered while processing: 
 tzdata 
Setting up tzdata (2011g-0ubuntu0.11.04) ... 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109. 
dpkg: error processing tzdata (--configure): 
 subprocess installed post-installation script returned error exit status 128 

How can I fix this?  I have used the same install media to install Ubuntu on a stand alone system and it works fine.

Thanks.

---

### Post by afs97209 on 2011-05-02
Same issue for me. Won't install from Win 7 x64 on what's now Oracle Virtualbox

Downloaded one desktop x64 CD from the Ubuntu main site, downloaded another desktop x64 by torrent that had 500+ previous downloads indicated. Both failed.

How about no more alpha software releases from Ubuntu, huh? Delay releases that aren't ready and tested.

---

### Post by axcairns on 2011-06-06
Found this in another thread - 

```
sudo dpkg --configure -a && sudo apt-get install -f
```

Fixed it for me.

Not too impressed. Vanilla install of 11.10 and this happens almost immediately. QC pls.

---

### Post by sealev on 2011-06-10
what do you do with this code line? where do you put it? How?

---

### Post by Argentina on 2011-08-16
[SIZE=3]I had the same problem with my own install of Ubuntu 11.04. What worked for me was to re-install the tzdata package. The problem is it won't let you uninstall it because libc6 and other important packages depend on it. You can't uninstall it neither with synaptic nor with the terminal. So you have to [manually download the package from here]("http://packages.ubuntu.com/natty/all/tzdata/download")[/SIZE] [SIZE=3](tzdata for natty [11.04] amd64). However, when you try to install it it won't allow you either; it says you already have a newer version installed. So you'll have to open up a terminal and run

[FONT=Courier New]sudo dpkg -i <location_of_.deb_file>[/FONT]

Remember you have to type the full address of the file (or cd to the folder you downloaded it to) and of course you need to consent this with your password.

That should get you working... I hope.
[/SIZE]

---

