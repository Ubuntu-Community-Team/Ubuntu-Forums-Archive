---
title: "Ubunto 12.04 LTS - No Space Left on Device"
date: 2015-01-25
forum: Installation &amp; Upgrades
---

### Post by kbellx on 2015-01-25
```
$ uname -a
Linux izanagi-MS-7756 3.5.0-48-generic #72~precise1-Ubuntu SMP Tue Mar 11 20:08:23 UTC 2014 i686 i686 i386 GNU/Linux
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise
```
Okay, I'm new to using linux, and like every other OS I've ever used,  troubleshooting is how I learn best.  However in this case, I have my  hands tied in some of my efforts.  For one thing, in terminal, I have  the scrollback set to 'unlimited' (or even 512), but it still only  allows me to go back 30 lines, which is rather limiting.  That aside, I  cannot install any software/updates, as I came across this issue "Error  Broken count > 0" as it has unmet dependencies... because it ran out  of space.  Sometimes I cannot even open some programs nor mount my  second hard drive (Error creating mount point: No space left on device) unless I close other running operations first.   As I understand, it's not disk space it's out of, but rather to space  specifically allocated for the system.

When I first start ubuntu, I go to the error notification and it always  gives me the error above.  When I try to do a partial upgrade to satisfy  it, I get the message "Failed to run /usr/bin/update-manager  '--dist-upgrade' as user root.  Unable to copy the user's Xauthorization  file." with no details.  So I go into terminal and run the following  command: /usr/bin$ update-manager '--dist-upgrade'

```
Original exception was:
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 112, in <module>
    controller = DistUpgradeController(view, datadir=data_dir)
  File "/usr/lib/python2.7/dist-packages/DistUpgrade/DistUpgradeController.py", line 123, in __init__
    aufsOptionsAndEnvironmentSetup(self.options, self.config)
  File "/usr/lib/python2.7/dist-packages/DistUpgrade/DistUpgradeAufs.py", line 23, in aufsOptionsAndEnvironmentSetup
    tmprw = tempfile.mkdtemp(prefix="upgrade-rw-")
  File "/usr/lib/python2.7/tempfile.py", line 317, in mkdtemp
    dir = gettempdir()
  File "/usr/lib/python2.7/tempfile.py", line 261, in gettempdir
    tempdir = _get_default_tempdir()
  File "/usr/lib/python2.7/tempfile.py", line 208, in _get_default_tempdir
    ("No usable temporary directory found in %s" % dirlist))
IOError: [Errno 2] No usable temporary directory found in ['/tmp', '/var/tmp', '/usr/tmp', '/usr/bin']
```

Again, I believe everything is 'unusable' because there is no space in  which to write.

Perhaps the partition I created was too small?  How do I go about finding/removing the unnecessary bits?

Thanks

---

### Post by oldos2er on 2015-01-25
Please post the output of ```
df -h
```

---

