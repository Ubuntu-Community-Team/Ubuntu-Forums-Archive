---
title: "Botched Program Installation - Need Help to remove/reinstall"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by Lucidmez on 2010-11-30
Hi,

My apologies in advance if this has been answered; I couldn't find it though.  I botched an installation of a program and now I can't completely remove or (re)install it.  I've tried the purge command with no luck.  Tried reinstalling through synaptic, nothing.  I'm quite sure the issue came up because I tried installing stopwatch while the update manger was running.  Stupid! Anyway, here is what I'm getting.  Any help would be much appreciated.

  [B]:sudo apt-get install stopwatch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  stopwatch
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/12.4kB of archives.
After this operation, 123kB of additional disk space will be used.
Selecting previously deselected package stopwatch.
(Reading database ... 
dpkg: warning: files list file for package `apport' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `time' missing, assuming package has no files currently installed.[/B] [B]

dpkg: warning: files list file for package `ufw' missing, assuming package has no files currently installed.[/B] [B]

dpkg: warning: files list file for package `uuid-runtime' missing, assuming package has no files currently installed.[/B] [B]

dpkg: warning: files list file for package `ppp' missing, assuming package has no files currently installed.[/B] [B]

dpkg: warning: files list file for package `tcl8.4' missing, assuming package has no files currently installed.[/B] [B]
(Reading database ... 265774 files and directories currently installed.)
Unpacking stopwatch (from .../stopwatch_3.5-2_all.deb) ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Setting up tcl (8.4.16-2) ...
update-alternatives: error: alternative path /usr/bin/tclsh-default doesn't exist.
dpkg: error processing tcl (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of tk:
 tk depends on tcl (= 8.4.16-2); however:
  Package tcl is not configured yet.
dpkg: error processing tk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of stopwatch:
 stopwatch depends on tk; however:
  Package tk is not configured yet.
dpkg: error processing stopwatch (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                       Errors were encountered while processing:
 tcl
 tk
 stopwatch
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]


Thank you

---

### Post by zvacet on 2010-12-03
```
sudo dpkg --configure -a
```

---

### Post by sikander3786 on 2010-12-03
And if that doesn't help,

```
sudo apt-get install -f
```

Keep posting the outputs ;-)

---

### Post by Lucidmez on 2010-12-03
Hmm, neither of those seemed to work.

mark@Paoli-1:~$ sudo dpkg --configure -a
Setting up tcl (8.4.16-2) ...
update-alternatives: error: alternative path /usr/bin/tclsh-default doesn't exist.
dpkg: error processing tcl (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of tk:
 tk depends on tcl (= 8.4.16-2); however:
  Package tcl is not configured yet.
dpkg: error processing tk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of stopwatch:
 stopwatch depends on tk; however:
  Package tk is not configured yet.
dpkg: error processing stopwatch (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tcl
 tk
 stopwatch
mark@Paoli-1:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up tcl (8.4.16-2) ...
update-alternatives: error: alternative path /usr/bin/tclsh-default doesn't exist.
dpkg: error processing tcl (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of tk:
 tk depends on tcl (= 8.4.16-2); however:
  Package tcl is not configured yet.
dpkg: error processing tk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of stopwatch:
 stopwatch depends on tk; however:
  Package tk is not configured yet.
dpkg: error processing stopwatch (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 tcl
 tk
 stopwatch
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by sikander3786 on 2010-12-03
What if you try to re-install those offensive packages?

```
sudo apt-get install --reinstall tcl tk stopwatch
```

Or try to remove them?

```
sudo apt-get remove --purge tcl tk stopwatch
```

```
sudo apt-get install tcl tk stopwatch
```

---

### Post by Lucidmez on 2010-12-06
I thought after purging all 3 I might have luck but I didn't.  I appreciate all the help but I'm inclined to just forget this program.  It really isn't that important to me.  If you just like solving problems I will keep trying, though.  Thanks again.  Here is the latest:

mark@Paoli-1:~$ sudo apt-get remove --purge tcl tk stopwatch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  stopwatch* tcl* tk*
0 upgraded, 0 newly installed, 3 to remove and 3 not upgraded.
3 not fully installed or removed.
After this operation, 262kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: warning: files list file for package `apport' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `time' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ufw' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `uuid-runtime' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ppp' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tcl8.4' missing, assuming package has no files currently installed.
(Reading database ... 265786 files and directories currently installed.)
Removing stopwatch ...
Purging configuration files for stopwatch ...
Removing tk ...
Removing tcl ...
update-alternatives: warning: /etc/alternatives/tclsh is dangling, it will be updated with best choice.
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 removed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for python-support ...
mark@Paoli-1:~$ sudo apt-get install tcl tk stopwatch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  stopwatch tcl tk
0 upgraded, 3 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/20.8kB of archives.
After this operation, 262kB of additional disk space will be used.
Selecting previously deselected package tcl.
(Reading database ... 
dpkg: warning: files list file for package `apport' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `time' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ufw' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `uuid-runtime' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ppp' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tcl8.4' missing, assuming package has no files currently installed.
(Reading database ... 265760 files and directories currently installed.)
Unpacking tcl (from .../archives/tcl_8.4.16-2_all.deb) ...
Selecting previously deselected package tk.
Unpacking tk (from .../archives/tk_8.4.16-2_all.deb) ...
Selecting previously deselected package stopwatch.
Unpacking stopwatch (from .../stopwatch_3.5-2_all.deb) ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for menu ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Setting up tcl (8.4.16-2) ...
update-alternatives: error: alternative path /usr/bin/tclsh-default doesn't exist.
dpkg: error processing tcl (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of tk:
 tk depends on tcl (= 8.4.16-2); however:
  Package tcl is not configured yet.
dpkg: error processing tk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of stopwatch:
 stopwatch depends on tk; however:
  Package tk is not configured yet.
dpkg: error processing stopwatch (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 tcl
 tk
 stopwatch
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by sikander3786 on 2010-12-06
If no one comes up with a better solution, I would suggest to manually remove the information regarding offensive packages here. See this one.

[http://ubuntuforums.org/showpost.php?p=10048487&postcount=6](http://ubuntuforums.org/showpost.php?p=10048487&postcount=6)

Replace **firmware-b43-installer** in that post to **tcl, tk** and **stopwatch** as these are the offensive packages on your system. Remove all references to these 3 packages and again try apt-get update.

Good Luck!

---

