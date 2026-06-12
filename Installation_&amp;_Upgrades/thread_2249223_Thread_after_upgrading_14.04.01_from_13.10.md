---
title: "Thread after upgrading 14.04.01 from 13.10"
date: 2014-10-20
forum: Installation &amp; Upgrades
---

### Post by cchaverri on 2014-10-20
After upgrading online my laptop I got the following message before finishing the complete upgrade:

Could not install /var/cache/apt/archives/python-numpy_1%3z1.8.2-0ubuntu0.1_amd64.deb
unable to read link './usr/lib/python2.7/dist-packages/numpy/distutils/fcompiler/hpux.py':Input/ouput error

and upgrade process closed. I rebooted and could not access with my password the GUI. The GUI shows some " I could access CLI and found that Ubuntu 14.04 was installed and that dpkg was interrupted, so I tried to do run 'sudo dpkg --configure -a' to correct the problem and then 'sudo apt-get install -f'

After running 'sudo apt-get install -f' I got the following message:

Removing python-numpy (1:1.7.1-1ubuntu1) ...
dpkg: error processing package python-numpy (--remove):
unable to securely remove '/usr/lib/python2.7/dist-packages/numpy/distutils/command/build.py': Read-only file system
Processing triggers for man-db (2.6.5-2) ...
dpkg: unrecoverable fatal error, aborting:
unable to flush updated status of `man-db': Read-only file system
touch: cannot touch ‘/var/lib/update-notifier/dpkg-run-stamp’: Read-only file system
sh: 1: cannot create /var/lib/update-notifier/updates-available: Read-only file system
E: Sub-process /usr/bin/dpkg returned an error code (2)
E: Problem executing scripts DPkg::Post-Invoke 'if [ -d /var/lib/update-notifier ]; then touch /var/lib/update-notifier/dpkg-run-stamp; fi; if [ -e /var/lib/update-notifier/updates-available ]; then echo > /var/lib/update-notifier/updates-available; fi '
E: Sub-process returned an error code

What means "read-only file system" ? I am the only user of my laptop.  How can I fix this issue?
I tried to reinstall 14.04 from a DVD but there is no option for not touching /home partition and mantaining same program loaded configs.

Thanks in advance for any help.

---

### Post by grahammechanical on 2014-10-20
> [COLOR=#000000]What means "read-only file system" ?[/COLOR]

It means that you have access to the file or folder to read it but not to write to the file or even delete it. Why that should be I do not know. Perhaps you should try un-installing package python-numpy as a separate action. Or you could run these commands from the Recovery mode. First run Network. That will establish an internet connection and put the file system into read/write mode and then run Root. When finished type exit to get back to the recovery menu and run Resume to get to a desktop.

Applications like NumPy which are not in the software centre and so not in the Ubuntu repositories should be un-installed before upgrading and then re-installed to avoid problems like this.

Regards.

---

### Post by TheFu on 2014-10-20
Backup your /home.  Do this first before anything else.

Read-only partition means nothing can be written to that storage/partition.

I suspect the file system was full - but cannot be positive from the data above. It could be something else.
What is the output from **df -h**?
If the file system is full - some stuff needs to be removed - data, not programs, not packages, not other stuff - data stuff.  Then we can work on the other stuff.

---

