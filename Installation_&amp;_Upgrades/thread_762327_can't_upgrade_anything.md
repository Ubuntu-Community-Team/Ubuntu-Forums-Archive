---
title: "can't upgrade anything"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by brenbren on 2008-04-22
When I go to package manager it starts to initialize and then an error message comes up and says:


Could not initialize the package information 

A unresolvable problem occurred while initializing the package information. 

Please report this bug against the 'update-manager' package and include the following error message: 

'W:Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages), E:Dynamic MMap ran out of room, E:Error occurred while processing xscreensaver (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


any suggestions?

---

### Post by fquist on 2008-04-28
There seem to be two of us with this problem and no one willing to help.  Have you had any luck fixing the problem?

---

### Post by fquist on 2008-04-28
I did get some response to my thread "Update Manager Problem" but, unfortunately, it didn't solve my problem.  It may be applicable to your situation though.

---

### Post by iaculallad on 2008-04-28
Try:

sudo apt-get install -f

maybe caused by broken/corrupt installation.

---

### Post by Sudo Sumo on 2008-04-28
Hey Guys,

Try running an "apt-get clean"; beyond that, I'd recommend increasing the size of your apt-cache (add 

APT::Cache-Limit "118388608";

to /etc/apt/apt.conf.d/70debconf and retry.

Good luck!

---

### Post by yodc on 2008-04-30
tried iaculallad's suggestion, no luck for me...
tried sumo's suggestions, no luck for me....

definatly an issue that has arrisen in a matter of hours.

put me down as an affected user for this bug.

---

### Post by Starhawk99 on 2008-05-09
I'm having the same problem and am trying to update tje 70debconf file but when I attempt to save changes and replace existing file with new one , it says i don't have the proper permissions to update.  How do i get the proper permission?

---

