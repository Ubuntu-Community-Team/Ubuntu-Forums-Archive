---
title: "No unity launcher or window manager after upgrade to 16.04"
date: 2016-04-22
forum: Installation &amp; Upgrades
---

### Post by koma77 on 2016-04-22
I just upgraded my 15.10 installation to 16.04.
Towards the end of the upgrade there was an error related to mysql-server, however I managed to fix that by re-installing mysql-server.

Now, when I start 16.04, after I log in I get only the desktop background with icons. No launcher and there is no window manager. I've tried to start unity by myself but that did not work.

The guest account looks great so there is something wrong with 16.04 and my account.

Any ideas on where to look for this error?

---

### Post by DuckHook on 2016-04-22
My concern would be that if mysql-server did not upgrade properly, other files may also have been corrupted. Network distro upgrades are a bit of a black art and don't always go well. It may be necessary to reinstall from scratch.

Did you back up all important data first? If so, you won't have to face catastrophic results. If not, then that is the first thing that you absolutely *must* do.

Can you <Alt>+<Ctrl>+<F1> into a TTY? You should be able to backup using the CLI if necessary.

---

### Post by grahammechanical on 2016-04-22
There is a comment in the release notes about MySQL 5.7

> MySQL has been updated to 5.7. Some configuration  directives have been changed or deprecated, so if you are upgrading from  a previously customised configuration then you will need to update your  customisation appropriately. See [bug 1571865]("https://bugs.launchpad.net/ubuntu/+source/mysql-5.7/+bug/1571865") for details. 


Password  behaviour when the MySQL root password is empty has changed. Packaging  now enables socket authentication when the MySQL root password is empty.  This means that a non-root user can't log in as the MySQL root user  with an empty password. For details, see the [NEWS]("https://anonscm.debian.org/cgit/pkg-mysql/mysql-5.7.git/tree/debian/NEWS?id=1025a9fa9c6c112913c59138db49dbc94891d20f") file. 

 


> Users with customised MySQL server configurations may hit a maintainer  script error on upgrade due to changed configuration directives in MySQL  5.7. This will need to be fixed up manually. See the [general MySQL update notes]("https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#MySQL_5.7") for details and instructions on fixing one common case of this.

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

As for the issue of a missing Unity try another video driver. That is the best that I can offer.

Regards

---

### Post by chainedgx on 2016-04-22
I had the same issue and fixed it with the following commands from TTY ([COLOR=#000000]<Alt>+<Ctrl>+<F1>[/COLOR])

sudo apt-get -f install
sudo apt-get install ubuntu-desktop
sudo apt-get update && sudo apt-get dist-upgrade

---

### Post by koma77 on 2016-04-23
I tried all of the above and I still have the same problem.

Some observations:
The problem still exists even if I switch from the proprietary NVidia driver to Noveau.
The guest account still works fine: The unity top bar and side launcher works fine there.

Is there any way to debug unity? Where does unity keep its log?
I did not spot anything obviously wrong in the kernel log or in the syslog but of course I might have missed something.

I really do not want to re-install or create a new user...

---

### Post by koma77 on 2016-04-23
Ok, I think I got it working alright. Funnily enough I'm quite sure I did try this several times yesterday, but this is what I did from a terminal windows inside the broken unity environment (right click, select terminal):

sudo apt-get install --reinstall ubuntu-desktop unity
dconf reset -f /org/compiz
dconf reset -f /org/compiz/

(Note that I did not use sudo in the last two commands)

---

### Post by chainedgx on 2016-04-23
Glad to hear you got it working. I never tweaked compiz, so I didn't need to reset it.

---

### Post by sziliv on 2016-06-02
thx a lot, improved :)

---

### Post by zachpreston on 2016-11-26
Thank you, [[COLOR=#000000]chainedgx[/COLOR]]("https://ubuntuforums.org/member.php?u=1952411")!  This solved my issue.  Prior to this, I tried all six approaches in [http://askubuntu.com/questions/449845/problems-after-upgrading-to-14-04-only-background-and-pointer-after-login/481620#481620](http://askubuntu.com/questions/449845/problems-after-upgrading-to-14-04-only-background-and-pointer-after-login/481620#481620) (which was referenced in a 16.04 question) and koma77's steps as a path of lesser change (though I only tried them once).  I don't know if some prior steps (including changing the video driver to nouveau) contributed to it working.  I wish I had tried them first in isolation just for a cleaner reference.  I got a warning in the process about _apt not having perms for something to do with a Flash plugin.  This reminded me that the last change to my system before Unity not launching was to Flash plugins per trying to get DRM streaming media to work in Firefox.  I ultimately ended up using Chrome for that.  Thanks, again!

---

