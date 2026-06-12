---
title: "Update Manager/Settings/Updates - unable to check boxes"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by epp on 2010-06-01
I have 10.04 LTS installed on a system, in which 7.10 was originally installed, then upgraded to 8.04 LTS then to 10.04 LTS.

When opening the Update Manager, on the Updates tab, I noticed that none of the upper four boxes (Ubuntu updates) can be checked.  If the box is selected, the check mark does not appear.

I have been able to obtain updates manually by running the Update Manager each time, because the notification icon usually seen, does not appear.

At this point, since none of those boxes can be checked, I have no idea if any of the updates installed since the upgrade to 10.04 LTS, are or were security related.  Everything listed in the Update Manager are under "Recommended updates".

Is there any reason why none of the four boxes under Ubuntu updates on the Updates tab can be checked and is there a way to correct this?  I'm concerned that the system is not receiving all updates.

Thank you in advance for any help.

---

### Post by ajgreeny on 2010-06-01
The top two boxes should be selected by default, the two below that are not normally needed and may give you "cutting edge" apps that give some bugs.

I have no idea why your boxes are not selected.  Perhaps it's due to updating to 10.04 rather than a clean install.

---

### Post by epp on 2010-06-01
I looked at the information in Users and Groups and my account is set to administer the system, although the option is checked under "Custom".  As it was the first time I looked at that particular screen, I would presume anything checked came from the initial 7.10 installation.

I also reinstalled update-manager and update-manager-core, no change, none of those four boxes can be checked.

Also ran sudo apt-get update and the following appeared:

> 
~$ sudo apt-get update
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid Release.gpg
Ign [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) lucid/main Translation-en_US
Ign [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) lucid/universe Translation-en_US
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-updates Release.gpg
Ign [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://ubuntu.media.mit.edu/ubuntu/](http://ubuntu.media.mit.edu/ubuntu/) lucid-updates/restricted Translation-en_US
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid Release         
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-updates Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid/main Packages                  
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid/universe Packages              
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-updates/universe Packages
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-updates/main Packages
Hit [http://ubuntu.media.mit.edu](http://ubuntu.media.mit.edu) lucid-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Reading package lists... Done


In looking at the above, would it appear that I am receiving all updates on this, including security?

---

