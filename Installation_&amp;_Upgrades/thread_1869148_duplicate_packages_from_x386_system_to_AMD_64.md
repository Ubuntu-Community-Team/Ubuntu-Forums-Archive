---
title: "duplicate packages from x386 system to AMD 64"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by nobody00 on 2011-10-25
I've been running an Xubuntu x386 system for years and finally decided to join the 21 century so I made a fresh install of an AMD 64 bit Xubuntu 11.10 on the same machine. I've also updated the x386 system to 11.10. Both are running fine.

So my question is:
Can I duplicate on the AMD 64 bit system all the packages I have manually downloaded onto the x386 system with a script? I have been using Synaptic Package Manager and have never deleted the history. The oldest history entries are from 11/2009.

Perhaps a script is perhaps asking too much so maybe pointing out the correct background files and associated flags on Synaptic that I could eyeball and edit would be enough.

---

### Post by dino99 on 2011-10-25
no you cant do that, 32 & 64 bits are way too different

---

### Post by nobody00 on 2011-10-26
Let me clarify my request further. I'm want to duplicate an existing system. I'd like a listing of the packages that are optional and that I selected and manually downloaded. I have no interest in the "standard system" packages and their dependencies.

---

### Post by oldfred on 2011-10-26
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings'

I run the dpkg when I install a new system. But found I was installing old packages. It will not reinstall obsolete packages as they do not exist. I found I was reinstalling python2.5 for example. Now you may not want OpenOffice as LibreOffice is now the standard.  It is just a text file, so you can manually edit and remove anything you do not want.


But do not just import all sources as that can lead to issues of versions:
[http://askubuntu.com/questions/2038/backup-software-sources](http://askubuntu.com/questions/2038/backup-software-sources)
sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, the tip will only reinstall Ubuntu files,

List is long, if you want a list of top level apps (but not for reinstall)
Top level applications:
aptitude --disable-columns -F 'no_dependents %p' search '~i!~M!~R(~i)'

---

### Post by Toz on 2011-10-26
I don't usually use the Software Center, but I had a look at it today and noticed an option under the File menu called "Sync Between Computers". A google search later:

- [http://stephen.rees-carter.net/2011/09/a-fantastic-new-feature-in-ubuntu-software-center-sync-between-computers/]("http://stephen.rees-carter.net/2011/09/a-fantastic-new-feature-in-ubuntu-software-center-sync-between-computers/") 
- [http://www.addictivetips.com/ubuntu-linux-tips/how-to-synchronize-applications-between-multiple-ubuntu-computers/]("http://www.addictivetips.com/ubuntu-linux-tips/how-to-synchronize-applications-between-multiple-ubuntu-computers/")

and it seems that this can be used to keep the installed applications on multiple computers in sync. Cool.

I'll have to give this a try when I have some free time.

---

### Post by nobody00 on 2011-11-01
I used the Sync Between Computer feature in the Ubuntu Software Center. It provided exactly what I needed. Since both of my computers were on the same box I had to change the hostname on one of them so the diff between systems would work. Toz thanks for the input.  OldFred - I appreciate the old school solution you provided being old school myself, but Ubuntu appears to have anticipated our needs. Much thanks for your effort.

---

