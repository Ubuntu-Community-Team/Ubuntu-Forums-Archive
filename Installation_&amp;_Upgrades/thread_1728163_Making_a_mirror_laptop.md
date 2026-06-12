---
title: "Making a mirror laptop"
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by Peter2009 on 2011-04-13
Dear Forum,

I need some help to updating my new laptop to the same level to the old one

I dont want to go by synaptic application one by one for update the whole thing!

Surely there should be a easier way!

I was thinking there must be a command which would list all the package installed on my old PC

and then take that list to synaptic some how to look for the newest package on the repository and install it!

Could you please help me here? I am not that expert on Linux!

Thanks for you help!

---

### Post by oldfred on 2011-04-13
This just lists a text file of the package names. You may want to houseclean in synaptic before hand or edit list to eliminate things you do not want. List is long. It will not reinstall anything already installed, but does download current versions for your new install. I used this after updating in place for several years & it found some packages that were totally obsolete and did not update them of course. But it reinstall all sorts of old packages. I still have python2.5 for example.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings'

But do not just import all sources as that can lead to issues of versions:
[http://askubuntu.com/questions/2038/backup-software-sources](http://askubuntu.com/questions/2038/backup-software-sources)
sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, the tip will only reinstall Ubuntu files,

---

### Post by Peter2009 on 2011-04-13
> **oldfred said:**
> This just lists a text file of the package names. You may want to houseclean in synaptic before hand or edit list to eliminate things you do not want. List is long. It will not reinstall anything already installed, but does download current versions for your new install. I used this after updating in place for several years & it found some packages that were totally obsolete and did not update them of course. But it reinstall all sorts of old packages. I still have python2.5 for example.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings'

But do not just import all sources as that can lead to issues of versions:
[http://askubuntu.com/questions/2038/backup-software-sources](http://askubuntu.com/questions/2038/backup-software-sources)
sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, the tip will only reinstall Ubuntu files,
Thanks for quick reply!

I did update the sources.list file!
By mistake a double click it and a application try to update the new sources!
[COLOR="Red"]**Is that a better way????**[/COLOR]

I just copy a pasted all the sources contented into the new machine file!

I have to used cp to move the files to the etc/apt/...... 
[COLOR="#ff0000"]its a good idea to make the user sudo so I could just past and copy in everywhere in the machine[/COLOR] (i did wast time looking for command and typing)

I did used the making files to update the other machine but one thing to mention when I did told it to update I wait for a while to see if something was going to happen but you must press APPLY button to carry on, otherwise look like nothing happen

Thanks one again! Let you know when all is downloaded, does not look that there will be any problem though!

---

### Post by Peter2009 on 2011-04-13
> **Peter2009 said:**
> Thanks for quick reply!

I did update the sources.list file!
By mistake a double click it and a application try to update the new sources!
[COLOR="Red"]**Is that a better way????**[/COLOR]

I just copy a pasted all the sources contented into the new machine file!

I have to used cp to move the files to the etc/apt/...... 
[COLOR="#ff0000"]its a good idea to make the user sudo so I could just past and copy in everywhere in the machine[/COLOR] (i did wast time looking for command and typing)

I did used the making files to update the other machine but one thing to mention when I did told it to update I wait for a while to see if something was going to happen but you must press APPLY button to carry on, otherwise look like nothing happen

Thanks one again! Let you know when all is downloaded, does not look that there will be any problem though!
One thing to say here! if you save the makings to the Destop you can not find them with the file browser 
[COLOR="Red"][/COLOR]Why?

---

### Post by oldfred on 2011-04-13
Copying all of sources could be a problem if your new install is an upgrade as then the versions would not match.

You also need to be very careful using Nautilus as root or anytime you are at root. You then have total capability to cause lots of damage. 

I have never used the save as markings. I just did it and it saved the file, but it had root as owner and not much in the way of permissions.

---

