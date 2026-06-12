---
title: "Error BrokenCount&gt;0 when tried installing Facebook for Firefox addon for pidgin"
date: 2012-10-13
forum: Installation &amp; Upgrades
---

### Post by Gabuds on 2012-10-13
I downloaded this add-on at this site after installing pidgin: [http://code.google.com/p/pidgin-facebookchat/downloads/detail?name=pidgin-facebookchat-1.69.deb&can=2&q=](http://code.google.com/p/pidgin-facebookchat/downloads/detail?name=pidgin-facebookchat-1.69.deb&can=2&q=)

I dont know what happened/what I did but I'm having errors. 
At my update manager, it says that error on the title and ask to update packages, but it wont update. 
Over the software center, the "applying changes" for the repair is stuck at the half. 
I tried doing those commands on the terminal and that what I got:

    sudo apt-get check
    [sudo] password for geo: 
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    You might want to run 'apt-get -f install' to correct these.
    The following packages have unmet dependencies:
     pidgin-data : Breaks: pidgin-facebookchat (< 1.69-2) but 1.69 is installed
    E: Unmet dependencies. Try using -f.
    geo@Geo-PC:~$ sudo apt-get -f install
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    Correcting dependencies... Done
    The following extra packages will be installed:
      pidgin-facebookchat
    The following packages will be upgraded:
      pidgin-facebookchat
    1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
    1 not fully installed or removed.
    Need to get 0 B/40.4 kB of archives.
    After this operation, 131 kB of additional disk space will be used.
    Do you want to continue [Y/n]? Y
    dpkg: warning: there's no installed package matching pidgin-facebookchat:i386

---

### Post by Gabuds on 2012-10-13
The notification error for update maneger disappeared when i did
    sudo apt-get remove pidgin-facebookchat

however the "repairing installed software - applying changes" is still stuck at half on software manager. how do i remove that?

---

