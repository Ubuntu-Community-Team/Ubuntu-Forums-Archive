---
title: "Customised Live CD installer crashes"
date: 2016-06-16
forum: Installation &amp; Upgrades
---

### Post by &amp;KyT$0P# on 2016-06-16
I'm trying to make a customised Xubuntu 16.04 ISO, starting from the official Xubuntu ISO, using [this instructions]("https://help.ubuntu.com/community/LiveCDCustomization"), mainly so that package installation/removal doesn't need to be repeated in installing to multiple machines.  The live CD boots fine, and the system seems to be working... except, when I try to run the installer, the installer crashes at "Configuring system locales" and wants to submit a bug report.
This does not happen with the official Xubuntu ISO.

What am I doing wrong in creating the custom ISO?

---

### Post by &amp;KyT$0P# on 2016-06-19
Not sure if this is getting somewhere or not?

If I only remove packages, but don't install anything new, it fails same as before.
If I follow the steps in that guide, but without actually customizing the CD at all, it works.

It seems the installer log messages go to /var/log/syslog, so here's a sample of the errors it's giving:
```
xubuntu /plugininstall.py: log-output -t ubiquity chroot /target python2.7 -m compileall /usr/share/python/
xubuntu ubiquity: dpkg: warning: failed to open configuration file '/root/.dpkg.cfg' for reading: Permission denied
xubuntu /plugininstall.py: log-output -t ubiquity chroot /target py3compile -p python3 /usr/share/python3/
xubuntu ubiquity: mount:
xubuntu ubiquity: only root can use "--types" option
xubuntu ubiquity: 
xubuntu /plugininstall.py: log-output -t ubiquity chroot /target mount -t proc proc /proc
xubuntu ubiquity: mount:
xubuntu ubiquity: only root can use "--types" option
xubuntu ubiquity: 
xubuntu /plugininstall.py: log-output -t ubiquity chroot /target mount -t sysfs sysfs /sys
xubuntu ubiquity: mount:
xubuntu ubiquity: only root can use "--bind" option
xubuntu ubiquity: 
xubuntu /plugininstall.py: log-output -t ubiquity mount --bind /dev /target/dev
xubuntu ubiquity: mount:
xubuntu ubiquity: only root can use "--bind" option
xubuntu ubiquity: 
xubuntu /plugininstall.py: log-output -t ubiquity mount --bind /run /target/run
xubuntu ubiquity: [Errno 13] Permission denied: '/usr/lib/python2.7/dist-packages/lsb_release.pyc.140707814690024'
xubuntu ubiquity: [Errno 13] Permission denied: '/usr/lib/python2.7/dist-packages/liblzma.pyc.140707814690112'

```
(There are lots more python permission denied messages for both python 2 and python 3.)

Seems like the issue is stuff not running as root that should be running as root... :confused:
I didn't set a root password or anything like that (as far as I know), and I can sudo in the live environment without password...

Why customizing the packages would cause this, and how can I avoid this problem?

---

### Post by &amp;KyT$0P# on 2016-06-20
> Why customizing the packages would cause this
Ok I take that back, actually it depends exactly what packages are being uninstalled, question is still which package(s) required while not marked as dependency of the installer... :-k

---

### Post by &amp;KyT$0P# on 2016-06-20
As odd as this sounds I think it might be the ubiquity-slideshow.  Removing only ubiquity-slideshow-xubuntu (which I had been doing to try to save space on the image) and the installer crashes as described.  The times it worked fine were the times I had left that package alone.

If it works all my other desired customizations, while making sure to have a ubiquity-slideshow package installed in the cd, I'll consider that part resolved.

Secondary question though: when installing extra packages in the live CD, is it needed to have them in cdrom/pool in order to do a fully offline install of the system, and if so how to populate cdrom/pool automatically (like after doing the dpkg-repack and/or copying .deb's from apt's cache)?  I'm not sure how to "guess" that directory structure where adding new .deb packages.

---

### Post by &amp;KyT$0P# on 2016-06-21
Solved! :D
(Well, mostly, anyway...)

I fixed the problem with slideshow by replacing ubiquity-slideshow-xubuntu (which kept causing severe lagging in my test environment) with the **ubiquity-slideshow-ubuntu** (which works smoothly).

And apparently the install process doesn't care that "extra" packages are not present in the pool directory.  I did get all kinds of weird error messages during install but none of it looked related...
The resulting system seems to work fine as far as I can tell..

Last question before I mark this solved: if I perform a dist-upgrade while customizing the CD, do I need to also update the corresponding .deb packages in the CD's pool directory?

EDIT
Ok actually my question is what even is the purpose of the pool directory in terms of this use case?  Do I care about it at all, since this CD will be used only for clean install & system recovery, and I use the network for all my package-installing needs?  (Is it a bad idea to just see what happens if I delete pool outright? :shock: )

As for how to populate pool directory, some *extensive* searching shows the process somehow involves a utility [FONT=Courier New]apt-move[/FONT], but I didn't find any clear explanations...

EDIT2 OK so I did try deleting pool, and it still installed fine.  I think that answers all my questions about live CD customizing.
I hope this thread is useful to someone else saves a lot of time.

---

