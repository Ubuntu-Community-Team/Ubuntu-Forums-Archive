---
title: "install Flashplayer and close sofware management"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by fchartier on 2009-12-06
Hi all, 

I am trying to install the plugin for flashplayer on ubuntu for firefox.

during the package installation i get an error message :

only one software update manager can run at the same time   
please close other application Update manager, aptget, synaptic

the thing is i have just started my computer = haven't started them
therefore they start by default at start up, how do u turn them off ?

Thanks for ur help
cheers;)

---

### Post by gabo.cr on 2009-12-06
Ubuntu was probably getting ready for an update.
If you still have the problem you can run this command in terminal:

sudo apt-get update

Then try to install flashplayer again.

---

### Post by GregFuess on 2009-12-06
I have the same problem, and tried your recommendation.  The command was copied and pasted into the terminal command line, and executed nicely.  Then the package installer was opened, and responded with the statement that
"To install the following changes are required: To be removed: pdvdlinux"

Any help appreciated

Greg

---

### Post by gabo.cr on 2009-12-06
I can see you have this same problem in another post, I saw the commands you already tried.
You may get this problem when trying to install a Debian package into Ubuntu.
Try this:

> sudo dpkg -r --force-remove-reinstreq pdvdlinux

This command will force the removal of that file.

---

### Post by GregFuess on 2009-12-06
I appreciate your help, and am not sure what is happening, but this is the message that continues to return.  I used the command you recommend above, and this is the message that continues to return.  Somehow the install for flashplayer doesn't work, and this seems to be the problem.  Any help appreciated.

rm: cannot remove `/usr/share/app-install/desktop/pdvdlinux.desktop': No such file or directory
rm: cannot remove `/usr/share/app-install/icons/pdvdlinux.xpm': No such file or directory
/var/lib/dpkg/info/pdvdlinux.postrm: 27: update-app-install: not found
dpkg: error processing pdvdlinux (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 pdvdlinux
greg@dell-desktop:~$

---

### Post by GregFuess on 2009-12-06
This seems to be the issue, from what I can tell:

dpkg: error processing pdvdlinux (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 pdvdlinux
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by gabo.cr on 2009-12-06
You can edit the status file.
Just be careful to not delete anything you shouldn't.
Make a backup of the status file before making any changes.
Open the status file like this:

> sudo gedit /var/lib/dpkg/status

Gedit will open the file, it has a big list of packages, search for the pdvdlinux package information.
Once you find it, delete that whole section of the package, it should start like this:

> Package: pdvdlinux
Status...

Just be careful not to delete anything else from the other packages on the list.
This is an example of one package.


> Package: python-twisted-web
Status: install ok installed
Priority: optional
Section: python
Installed-Size: 1764
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: twisted-web
Version: 8.2.0-2ubuntu1
Replaces: python-twisted (<< 2.1), python2.3-twisted-web, python2.4-twisted-web
Depends: python, python-central (>= 0.6.11), python-twisted-core (>= 8.2.0-2)
Conflicts: python-twisted (<< 2.1), python2.3-twisted-web, python2.4-twisted-web
Description: An HTTP protocol implementation together with clients and servers
 Twisted web is a web server, and also provides basic HTTP client
 support. You may want to check out Nevow, a templating toolkit
 designed for twisted.web, and Twisted Web2, the next generation
 Twisted web server.
Original-Maintainer: Matthias Klose <doko@debian.org>
Python-Version: all


Once you deleted that section of pdvdlinux save the Gedit file and try one more time.

You should also run the update after doing that:

> sudo aptitude update


Hope that helps

---

### Post by GregFuess on 2009-12-07
Thanks, the Terminal says that the flashplayer is installed now.  Yet youtube does not play.  It says"Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player"

I appreciate your help, this is really getting better, maybe you could help me with javascript?

Thanks!

Greg

---

### Post by GregFuess on 2009-12-07
Thanks, the Terminal says that the flashplayer is installed now. Yet youtube does not play. It says"Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player"

I appreciate your help, this is really getting better, maybe you could help me with javascript?

Thanks!

Greg

---

### Post by gabo.cr on 2009-12-07
In Firefox go to: Edit > Preferences > Content.

Make sure Java and JavaScript are enabled.

---

### Post by GregFuess on 2009-12-07
Just checked and they are enabled...  any suggestions?

Thanks

Greg

---

### Post by mikewhatever on 2009-12-07
You need to relaunch Firefox to make it aware of what you have installed. By the way, your error was not at all like the OP's.;)

---

### Post by GregFuess on 2009-12-14
Thanks, there are still some plugins required, but You Tube is working.  The Dell PowerDVD is not, though, and neither is Movie Player .  Best Regards

Greg

---

