---
title: "update to 11.10 and now unmet adobe-flashplugin dependency"
date: 2012-05-30
forum: Installation &amp; Upgrades
---

### Post by geckopelli on 2012-05-30
I have a similar problem to a previous poster re. a 12.4 upgrade followed with adobe-flashplugin problem...
My situation is after auto updates to 11.10 i have unmet dependencies with flash-plugin that prevent further updates or upgrades to 12.04.

anyone have a clue?

~$ uname -a
Linux dell-laptop 3.0.0-20-generic #34-Ubuntu SMP Tue May 1 17:28:21 UTC 2012 i686 i686 i386 GNU/Linux

~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 firefox : Breaks: adobe-flashplugin (<= 11.1.102.63-0oneiric1) but 10.0.12.36-1hardy1 is installed
E: Unmet dependencies. Try using -f.

grm@dell-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  adobe-flashplugin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 10.1 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 551094 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)

:~$  sudo apt-get remove adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  adobe-flashplugin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 10.1 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 551094 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Sularco on 2012-06-01
I can remember that we had similar problems a while back:

[http://ubuntuforums.org/archive/index.php/t-1075776.html]("http://ubuntuforums.org/archive/index.php/t-1075776.html")

Perhaps the same solutions applied back then will help in your case?

---

### Post by geckopelli on 2012-06-02
Thanks for the suggestion, but it did not work.  I am in a bad place... cannot update or upgrade because of the !#%* flashplugin...

Submitted bug #1007885....

> **Sularco said:**
> I can remember that we had similar problems a while back:

[http://ubuntuforums.org/archive/index.php/t-1075776.html]("http://ubuntuforums.org/archive/index.php/t-1075776.html")

Perhaps the same solutions applied back then will help in your case?

---

