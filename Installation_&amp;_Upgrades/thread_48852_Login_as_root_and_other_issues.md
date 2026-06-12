---
title: "Login as root and other issues"
date: 2005-07-14
forum: Installation &amp; Upgrades
---

### Post by ubuntunewb75 on 2005-07-14
Hello!

Im sorry if this has been covered elsewhere but all the documentation I have read on this isn't clarifying it.   :?  ](*,)   I Installed Ubuntu under expert mode and created a root password.  The login screen won't allow me to login as root.  Furthermore, when I try to run admin tools under my user account it asks for my root password-when I give it it tells me the session failed.  Any help advice or chiding replies would be greatly appreciated!  :)

---

### Post by shrikantubuntu on 2005-07-14
[QUOTE=ubuntunewb75]Hello!

Im sorry if this has been covered elsewhere but all the documentation I have read on this isn't clarifying it.   :?  ](*,)   I Installed Ubuntu under expert mode and created a root password.  The login screen won't allow me to login as root.  Furthermore, when I try to run admin tools under my user account it asks for my root password-when I give it it tells me the session failed.  Any help advice or chiding replies would be greatly appreciated!  :)[/QUOTE]
 Me too having the same problem :( . HELP

---

### Post by Umbra on 2005-07-14
use sudo commands, but if you need to setup few things in graphical mode you could try this. In hte logon screen, the icons below, choose Console login

login: root
pass: yourpass

then use the command startx

and you're done, dont use this as your everday user account, just when you really need to do something as root with the graphical mode.

---

### Post by ubuntunewb75 on 2005-07-14
That did help  I also went into visudo and added my user account which allowed me to finaly get into the admin tools.  Now I'm having issues autodetecting my modem... :-)  thanks for your reply!

---

### Post by codejunkie on 2005-07-14
[QUOTE=ubuntunewb75]Hello!

I'm sorry if this has been covered elsewhere but all the documentation I have read on this isn't clarifying it.   :?  ](*,)   I Installed Ubuntu under expert mode and created a root password.  The login screen won't allow me to login as root.  Furthermore, when I try to run admin tools under my user account it asks for my root password-when I give it it tells me the session failed.  Any help advice or chiding replies would be greatly appreciated!  :)[/QUOTE]

it's because you did an expert install, and you enabled the root account and by doing this it doesn't add your username to the /etc/sudoers file and ubuntu/kubuntu uses sudo by default the reason the administrator tools in the System menu don't work is because the commands to launch them are like this I'm going to use synaptic as an example ```
gksudo /usr/sbin/synaptic
``` so in order to make them work you have to manually add your username to the /etc/sudoers file this link will help you do that [http://ubuntuguide.org/#allowmoresudoers](http://ubuntuguide.org/#allowmoresudoers) or manually edit all the .desktop files for the administrator tools by changing the command to launch them from ```
gksudo
``` to ```
gksu
``` the easiest way to do this is to just drag them all to the desktop right click on them choose properties and then click on the Launcher tab where it says gksudo /nameofcommand change it to gksu /nameofcommand now it will ask for the root password instead of yours hope this helps.

---

