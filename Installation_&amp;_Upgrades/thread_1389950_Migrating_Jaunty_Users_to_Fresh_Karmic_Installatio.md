---
title: "Migrating Jaunty Users to Fresh Karmic Installation"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by rationalisst on 2010-01-25
I have a working system running Jaunty. For various reasons I want to move to Karmic, but I don't want to use the "upgrade" feature in the software update manager. I need to swap some hard drives around, so I want to do a fresh installation. My question is, what is the easiest way to "migrate" a user to a fresh installation? On a Mac you can simply run the migration tool and it moves everything into place with relative ease, whether from a backup drive or from one computer to another. Is there any analogous program in Ubuntu? Or is it just so simple that such a program is unnecessary?

---

### Post by presence1960 on 2010-01-25
You can do a clean install and have your packages and their settings just the way they were in the old ubuntu install:

Back up all data you don't want to lose.

Back up /home

Boot into the existing ubuntu installation and use this [guide]("http://ubuntuforums.org/showpost.php?p=7157175&postcount=5") to create a file of your installed packages. Move that file with your backups above, you will need it after the clean install to restore your packages for you. After you do the clean install move that file back to /home and follow the directions to have your packages reinstalled on the clean installation. The only packages that won't be installed are packages installed manually from third parties & packages that you compiled. Restore the /home backup which will have most of the settings for your installed packages just as it was in the old installation.

---

