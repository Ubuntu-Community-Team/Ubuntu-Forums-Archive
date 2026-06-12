---
title: "Update on jaunty broke X"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by xkaliburx on 2009-04-09
Need I say more!  Well running Jaunty did an update last night and this morning turned on and got my login screen (nice and clean).  After submitting un/pw, screen turned black and now it's just hanging there.  I can move the mouse around, ctrl-alt-f1 does get me to a shell, tried updating again, but  nothing new.  Also tried the older kernel and recovery with the same results.

This is a Dell XPS M1330, nvidia gforce, anything else I need to provide or suggestions, let me know.

** update **
Still playing, on the login tried optins/gnome failsafe.  This time I got the orange wallpaper and the login sound, but just stopped there.  No menu, icons, etc.

Other update, on my latest apt-get upgrade I am actually stuck on the following;
Preparing to replace update-manager-core 1:0.111.2 (using ../update-manager-core_1%3a0.111.4_amd64.deb)

Hope that sheds some light!

Thanks

---

### Post by askreet on 2009-04-09
Try:
# apt-get -f install

If it stills fails to install that package try clearing the apt cache:
# apt-get clean

Then:
# apt-get update
# apt-get -f install

Let us know how that goes.

---

### Post by xkaliburx on 2009-04-09
Thanks, same error.  Piped the whole -f install and it's identical before and after the clean.  Here's the error;

Reading package lists...
Building dependency tree...
Reading state information...
Correcting dependencies... Done
The following extra packages will be installed:
  libopal3.6.1 libpt2.6.1-plugins-alsa libpt2.6.1-plugins-v4l2
  update-manager-core
The following packages will be REMOVED:
  libopal3.4.2 libpt2.4.2-plugins-alsa libpt2.4.2-plugins-v4l2
The following NEW packages will be installed:
  libopal3.6.1 libpt2.6.1-plugins-alsa libpt2.6.1-plugins-v4l2
The following packages will be upgraded:
  update-manager-core
1 upgraded, 3 newly installed, 3 to remove and 8 not upgraded.
71 not fully installed or removed.
Need to get 0B/3564kB of archives.
After this operation, 1167kB of additional disk space will be used.
(Reading database ... 130151 files and directories currently installed.)
Preparing to replace update-manager-core 1:0.111.2 (using .../update-manager-core_1%3a0.111.4_amd64.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: Exec format error
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2186, in <module>
    main()
  File "/usr/bin/pycentral", line 2180, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1639, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 377, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 408, in read_pyfiles
    self.pkgconfig.set('pycentral', 'include-links', '0')
  File "/usr/lib/python2.6/ConfigParser.py", line 669, in set
    ConfigParser.set(self, section, option, value)
  File "/usr/lib/python2.6/ConfigParser.py", line 377, in set
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'pycentral'
dpkg: error processing /var/cache/apt/archives/update-manager-core_1%3a0.111.4_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/update-manager-core_1%3a0.111.4_amd64.deb


I've been reading around, tried removing the sources file and rebuilt but still running into the same problem.

Thanks for the reply

---

