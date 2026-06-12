---
title: "Edgy won't install on Asrock 939Dual-SATA2"
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by futz on 2006-11-17
I've run Ubuntu Breezy and Dapper and also PCLinuxOS on this Asrock mainboard with no major problems. Last night I decided to wipe the partition with Dapper on it and install Edgy, using the Alternate CD.

Everything goes fine until it starts copying files. Then it errors out at somewhere around 85%. I tried everything I could think of, but no go. 

Tried the OEM install. Errors out same as standard alternate.

Downloaded the live disk. It boots up fine. Installed with the graphical installer. That goes to 94% and the installer crashes.

WTF!?!?

Maybe I'll put Dapper back on it...

------------

What is up with the sloppy, buggy installers lately? I've had a lot of grief with the Edgy installer on various machines. The new Fedora Core 6 installer is a bug filled, crashing piece of crap too. Took me like 4 tries to get it installed, and even then it installed the wrong kernel because of a bug. 

The Fedora 4 and 5 installers were fine and Ubuntu installers previous to the Edgy one worked much better.


EDIT: Here's the 94% crash report for the graphical install:
```
We're sorry; the installer crashed. Please file a new bug report at https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug (do not attach your details to any existing bug) and a developer will attend to the problem as soon as possible. To help the developers understand what went wrong, include the following detail in your bug report, and attach the files /var/log/syslog and /var/log/partman:

Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 166, in ?
    main()
  File "/usr/bin/ubiquity", line 161, in main
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 57, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 305, in run
    self.process_step()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 856, in process_step
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 628, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s\n%s" %
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 1404, in ?
    install.run()
  File "/usr/share/ubiquity/install.py", line 390, in run
    self.remove_extras()
  File "/usr/share/ubiquity/install.py", line 1341, in remove_extras
    self.do_remove(difference)
  File "/usr/share/ubiquity/install.py", line 1258, in do_remove
    if not cache.commit(fetchprogress, installprogress):
  File "/usr/lib/python2.4/site-packages/apt/cache.py", line 204, in commit
    res = self.installArchives(pm, installProgress)
  File "/usr/lib/python2.4/site-packages/apt/cache.py", line 179, in installArchives
    res = installProgress.run(pm)
  File "/usr/share/ubiquity/install.py", line 200, in run
    res = pm.DoInstall(self.writefd)
SystemError: E:Sub-process /usr/bin/dpkg received a segmentation fault.

```

---

### Post by futz on 2006-11-20
After many many hours of tinkering I got Edgy installed. 

What I finally figured out is that the installer must use a kernel that doesn't work quite right with the Uli chipset on this mainboard. 

I remembered that the previous installs that had worked were when I was using an IDE drive as my main boot drive and a 320GB SATA as an archive drive. The failures were all after I removed that old IDE drive and made the SATA the main drive.

So I grabbed a 250GB IDE drive that wasn't yet being used much in another box and bolted that in. Then I disabled the SATA controller in the BIOS.

Tried again and it installed without a hitch. Now I can reenable the SATA controller and have my 320GB back.

---

