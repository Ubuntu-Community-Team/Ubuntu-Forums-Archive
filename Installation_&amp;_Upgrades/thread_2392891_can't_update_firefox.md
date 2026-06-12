---
title: "can't update firefox"
date: 2018-05-26
forum: Installation &amp; Upgrades
---

### Post by jaxom98 on 2018-05-26
I am updating firefox via terminal  and get this message" E: the update command takes no arguments"
the command was "sudo apt-get update firefox
Can somebody translate this message please?

Note, by changing "update" to "upgrade" firefox is now current.

---

### Post by ajgreeny on 2018-05-26
Running commands ```
sudo apt update
sudo apt upgrade
``` will first check the repos for updates to all applications you have installed in your system and then upgrade any that have updated versions available.
You can not ask to update just a single application (eg firefox) as you requested as the update command does not actually update any apps; it just checks if any newer versions are available.

See **man apt** in terminal for more and better information.
> update (apt-get(8))
           update is used to download package information from all configured sources. Other commands operate on this data to e.g.
           perform package upgrades or search in and display details about all packages available for installation.

upgrade (apt-get(8))
           upgrade is used to install available upgrades of all packages currently installed on the system from the sources configured
           via sources.list(5). New packages will be installed if required to satisfy dependencies, but existing packages will never be
           removed. If an upgrade for a package requires the remove of an installed package the upgrade for this package isn't
           performed.

---

### Post by jaxom98 on 2018-05-28
Hello ajgreeny, thank you for your reply.  If I read it correctly, I am using a general command and telling it to do a specific action that is a part and only that 1 part of the general command , and this is causing a conflict?

---

### Post by PaulW2U on 2018-05-28
This correct way to upgrade a single package is by using the following command:
```
sudo apt-get install --only-upgrade <packagename>
```
See [https://ubuntuforums.org/showthread.php?t=2274216](https://ubuntuforums.org/showthread.php?t=2274216) 
and [https://askubuntu.com/questions/44122/how-to-upgrade-a-single-package-using-apt-get](https://askubuntu.com/questions/44122/how-to-upgrade-a-single-package-using-apt-get)

but obviously that will only upgrade a package if an update is available.

If the upgrade requires either new packages to be installed or other packages to be upgraded then I understand you remove the --only-upgrade switch from that command.

---

### Post by SeijiSensei on 2018-05-28
I use "install" to upgrade packages without bothering with the --only-upgrade.  Works fine.

The "upgrade" directive to apt applies to whole installations, not individual packages.

---

### Post by ajgreeny on 2018-05-28
Just curious, but surely in almost all circumstances it makes a lot more sense to simply run the **sudo apt update** and then **sudo apt upgrade** commands to upgrade everything at once.

Why just update a single package if there are several packages with candidate upgrades available?  For me this is one of the many delights of using Linux in any distro I've tried; there is no need to look at each application and update it separately from others as all are updated at the same time.

---

