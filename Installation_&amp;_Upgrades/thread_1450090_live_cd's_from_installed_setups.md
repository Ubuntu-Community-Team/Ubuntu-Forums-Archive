---
title: "live cd's from installed setups"
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by munaf on 2010-04-08
Hi,

I'm trying to create a live cd - or at least an installation cd - from a 9.04 installation that already has the programs I need installed.
For instance; I have 9.04 installed, along with a postgres server, jdk1.6, and a certain java app that only works in 9.04. I perform the same installation procedure on several pc's weekly. And I'd like to cut the work down to installing a "custom" ubuntu with all software already installed.

I'd sincerely appreciate any tips here.
Thanks in advance,

M

---

### Post by oldfred on 2010-04-08
I have seen recommendations for both of these, but have not used either:

[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)
[http://clonezilla.org/](http://clonezilla.org/)

After my last install, I tried to use the command line for just about everything and then saved history. I plan on converting history to a bash script so I can reinstall all my apps and reconfigure the default download easily.

List installed application - lovingliunux's post:
sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work.
generate new sources file

[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
from lovinglinux
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

---

