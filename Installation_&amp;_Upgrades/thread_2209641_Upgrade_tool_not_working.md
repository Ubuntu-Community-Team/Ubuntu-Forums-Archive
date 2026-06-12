---
title: "Upgrade tool not working"
date: 2014-03-06
forum: Installation &amp; Upgrades
---

### Post by sudo-server on 2014-03-06
First off, requisite system info:
Hardware is a Toshiba Satellite with two Pentiums at 2.0GHz each, 3GB ram, and a couple hundred gigs free storage currently.
Software is KDE SC 4.10.5 and Ubuntu 13.04. The system is up to date otherwise.

I'm trying to upgrade to the latest version because Raring is unsupported. When I ran the upgrade tool through the GUI, it mysteriously closed less than a second later. It was definitely closed and not hiding in the background somewhere because I opened system monitor and looked for it to be sure it wasn't just frozen. I tried again for good measure. I attempted to click "view in terminal," but it closed too quickly. I ran [FONT=courier new]do-release-upgrade -m desktop -f DistUpgradeViewKDE[/FONT] (the same command the GUI was trying to run) in the terminal instead. It gave me several puzzling errors. Tried again. Exact same errors. Rebooted my computer several times and everything. Nothing. Here it is, albeit with my username replaced with <username>:

```
<username>@phoenix:~$ do-release-upgrade -m desktop -f DistUpgradeViewKDE
Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife

Get:1 Upgrade tool signature [198 B]                                                                                        
Get:2 Upgrade tool [1,142 kB]                                                                                              
Fetched 1,142 kB in 0s (0 B/s)                                                                                              
authenticate 'saucy.tar.gz' against 'saucy.tar.gz.gpg'
extracting 'saucy.tar.gz'
[sudo] password for <username>:
**Error: "/var/tmp/kdecache-<username>B6tYEu" is owned by uid 1000 instead of uid 0.**
adept_manager: no process found
adept_updater: no process found
exitMainLoop
Error in sys.excepthook:
Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-l6pec5/DistUpgrade/DistUpgradeViewKDE.py", line 600, in _handleException
    self.translate_widget_children(self.dialog)
**AttributeError: 'DistUpgradeViewKDE' object has no attribute 'dialog'**

Original exception was:
Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-l6pec5/saucy", line 10, in <module>
    sys.exit(main())
  File "/tmp/ubuntu-release-upgrader-l6pec5/DistUpgrade/DistUpgradeMain.py", line 240, in main
    save_system_state(logdir)
  File "/tmp/ubuntu-release-upgrader-l6pec5/DistUpgrade/DistUpgradeMain.py", line 133, in save_system_state
    scrub_sources=True)
  File "/tmp/ubuntu-release-upgrader-l6pec5/DistUpgrade/apt_clone.py", line 149, in save_state
    self._write_state_sources_list(tar, scrub_sources)
  File "/tmp/ubuntu-release-upgrader-l6pec5/DistUpgrade/apt_clone.py", line 241, in _write_state_sources_list
    "./etc/apt/sources.list.d/"+source)
  File "/tmp/ubuntu-release-upgrader-l6pec5/DistUpgrade/apt_clone.py", line 246, in _add_file_to_tar_with_password_check
    for line in f.readlines():
  File "/usr/lib/python2.7/codecs.py", line 296, in decode
    (result, consumed) = self._buffer_decode(data, self.errors, final)
**UnicodeDecodeError: 'utf8' codec can't decode byte 0xb3 in position 16: invalid start byte**
```

I googled all three error messages, which are bolded in the above log ("[FONT=courier new]Error: "/var/tmp/kdecache-<username>B6tYEu" is owned by uid 1000 instead of uid 0.[/FONT]", "[FONT=courier new]AttributeError: 'DistUpgradeViewKDE' object has no attribute 'dialog'[/FONT]", and "[FONT=courier new]UnicodeDecodeError: 'utf8' codec can't decode byte 0xb3 in position 16: invalid start byte[/FONT]"), hoping for answers.

The first one turned up plenty of results; most of the answers said that the command [FONT=courier new]sudo chown root.root /var/tmp/kdecache-<username>B6tYEu[/FONT] would fix it, but I don't want to break something by accident so I didn't do it, mostly because I don't understand why it's not owned by root in the first place.

The second error message turned up [this bug report]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/92368"), but the bug is marked as fixed and it's from 2007 (which is well before I even owned this machine) so I don't think that's of much use.

the UnicodeDecodeError completely baffles me. 

Should I chown that directory or would it break something?

---

### Post by Bashing-om on 2014-03-06
sudo-server; Hello, Welcome to the forum.

The sad thing is that you waited too late to make an easy version upgrade. The 13.04 software repository no longer exist. And is the main reason for those errors.
This guide, though old, you will find still applicable to get you upgraded to release 13.10.
[https://help.ubuntu.com/community/EOLUpgradeshttps://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgradeshttps://help.ubuntu.com/community/EOLUpgrades)

Have a read, give it a try and let us know how it goes.

[INDENT][INDENT]it can be done
[/INDENT][/INDENT]

---

### Post by sudo-server on 2014-03-06
Thanks for replying so quickly. It took a bit of figuring out because I'm a bit of a novice when it comes to things like this but I changed sources.list to the repos it said to and did the commands, but all I get is a similar error in a slightly different format. This time it did actually sit and load something before crashing, and gave me some log files to upload. Here's the command line output. It's still saying something about the Unicode codec and I don't understand why. I still can't believe they would put Raring in EOL before Quantal; thought I had plenty of time to get upgraded. That's what I get for not keeping track of these things.

```
<username>@phoenix:~$ sudo do-release-upgrade
Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife

Get:1 Upgrade tool signature [198 B]                                                                                        
Get:2 Upgrade tool [1,142 kB]                                                                                               
Fetched 1,142 kB in 0s (0 B/s)                                                                                              
authenticate 'saucy.tar.gz' against 'saucy.tar.gz.gpg' 
extracting 'saucy.tar.gz'

Reading cache


**A fatal error occurred **

Please report this as a bug and include the files 
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in 
your report. The upgrade has aborted. 
Your original sources.list was saved in 
/etc/apt/sources.list.distUpgrade. 

Traceback (most recent call last): 

File "/tmp/ubuntu-release-upgrader-kzmzjq/saucy", line 10, in 
<module> 
sys.exit(main()) 

File 
"/tmp/ubuntu-release-upgrader-kzmzjq/DistUpgrade/DistUpgradeMain.py", 
line 240, in main 
save_system_state(logdir) 

File 
"/tmp/ubuntu-release-upgrader-kzmzjq/DistUpgrade/DistUpgradeMain.py", 
line 133, in save_system_state 
scrub_sources=True) 

File "/tmp/ubuntu-release-upgrader-kzmzjq/DistUpgrade/apt_clone.py", 
line 149, in save_state 
self._write_state_sources_list(tar, scrub_sources) 

File "/tmp/ubuntu-release-upgrader-kzmzjq/DistUpgrade/apt_clone.py", 
line 241, in _write_state_sources_list 
"./etc/apt/sources.list.d/"+source) 

File "/tmp/ubuntu-release-upgrader-kzmzjq/DistUpgrade/apt_clone.py", 
line 246, in _add_file_to_tar_with_password_check 
for line in f.readlines(): 

File "/usr/lib/python2.7/codecs.py", line 296, in decode 
(result, consumed) = self._buffer_decode(data, self.errors, final) 

[B]UnicodeDecodeError: 'utf8' codec can't decode byte 0xb3 in position 
16: invalid start byte[/B]
```

Here's /var/log/dist-upgrade/main.log:
```
2014-03-06 20:09:15,012 INFO Using config files '['./DistUpgrade.cfg']'
2014-03-06 20:09:15,012 INFO uname information: 'Linux phoenix 3.8.0-35-generic #50-Ubuntu SMP Tue Dec 3 01:24:59 UTC 2013 x86_64'
2014-03-06 20:09:15,012 INFO apt version: '0.9.7.7ubuntu4'
2014-03-06 20:09:15,012 INFO release-upgrader version '0.205.4' started
2014-03-06 20:09:15,036 INFO screen could not be run
2014-03-06 20:09:15,129 DEBUG Using 'DistUpgradeViewText' view
2014-03-06 20:09:15,188 DEBUG aufsOptionsAndEnvironmentSetup()
2014-03-06 20:09:15,189 DEBUG using '/tmp/upgrade-rw-3ifJ2R' as aufs_rw_dir
2014-03-06 20:09:15,189 DEBUG using '/tmp/upgrade-chroot-ve8fBu' as aufs chroot dir
2014-03-06 20:09:15,190 DEBUG enable dpkg --force-overwrite
2014-03-06 20:09:15,205 DEBUG creating statefile: '/var/log/dist-upgrade/apt-clone_system_state.tar.gz'
2014-03-06 20:09:15,353 ERROR not handled exception:
Traceback (most recent call last):

  File "/tmp/ubuntu-release-upgrader-kzmzjq/saucy", line 10, in <module>
    sys.exit(main())

  File "/tmp/ubuntu-release-upgrader-kzmzjq/DistUpgrade/DistUpgradeMain.py", line 240, in main
    save_system_state(logdir)

  File "/tmp/ubuntu-release-upgrader-kzmzjq/DistUpgrade/DistUpgradeMain.py", line 133, in save_system_state
    scrub_sources=True)

  File "/tmp/ubuntu-release-upgrader-kzmzjq/DistUpgrade/apt_clone.py", line 149, in save_state
    self._write_state_sources_list(tar, scrub_sources)

  File "/tmp/ubuntu-release-upgrader-kzmzjq/DistUpgrade/apt_clone.py", line 241, in _write_state_sources_list
    "./etc/apt/sources.list.d/"+source)

  File "/tmp/ubuntu-release-upgrader-kzmzjq/DistUpgrade/apt_clone.py", line 246, in _add_file_to_tar_with_password_check
    for line in f.readlines():

  File "/usr/lib/python2.7/codecs.py", line 296, in decode
    (result, consumed) = self._buffer_decode(data, self.errors, final)

UnicodeDecodeError: 'utf8' codec can't decode byte 0xb3 in position 16: invalid start byte

2014-03-06 20:09:15,354 DEBUG enabling apt cron job
```

The other document mentioned was empty. Is there something really obvious I'm missing? because I feel like an idiot. I really have no idea what most of this is and I'm in over my head, but it seems like it's checking some cache that has corrupted data in it. Am I completely wrong?

---

### Post by Bashing-om on 2014-03-06
sudo-server; Hummm,

Well, rather than blaming a corrupted cache just yet, let's look at some of the "sources" and make sure they are not what is corrupted.
Post back the outputs of terminal commands:
```

cat -n /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list
cat /etc/update-manager/release-upgrades

```
One step at a time, Will try and 
[INDENT][INDENT][INDENT]find out what is not going on
[/INDENT][/INDENT][/INDENT]

---

### Post by sudo-server on 2014-03-06
This is the result.
```
<username>@phoenix:~$ cat -n /etc/apt/sources.list
     1  ## EOL upgrade sources.list
     2  # Required
     3  deb http://old-releases.ubuntu.com/ubuntu/ raring main restricted universe multiverse
     4  deb http://old-releases.ubuntu.com/ubuntu/ raring-updates main restricted universe multiverse
     5  deb http://old-releases.ubuntu.com/ubuntu/ raring-security main restricted universe multiverse
     6
     7  # Optional
     8  deb http://old-releases.ubuntu.com/ubuntu/ raring-backports main restricted universe multivers
<username>@phoenix:~$ cat /etc/apt/sources.list.d/*.list
deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
<username>@phoenix:~$ cat /etc/update-manager/release-upgrades
# Default behavior for the release upgrader.

[DEFAULT]
# Default prompting behavior, valid options:
#
#  never  - Never check for a new release.
#  normal - Check to see if a new release is available.  If more than one new
#           release is found, the release upgrader will attempt to upgrade to
#           the release that immediately succeeds the currently-running
#           release.
#  lts    - Check to see if a new LTS release is available.  The upgrader
#           will attempt to upgrade to the first LTS release available after
#           the currently-running one.  Note that this option should not be
#           used if the currently-running release is not itself an LTS
#           release, since in that case the upgrader won't be able to
#           determine if a newer release is available.
Prompt=normal


```
Could Steam be causing it?

---

### Post by Bashing-om on 2014-03-07
sudo-server; Well, Yeah !

I bet it is steam. Let's disabale that source (gui: -> Software Center -> other sources) and see what results).
Then run terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo do-release-upgrade

```
Mind you steam is not a part of the ubuntu operating system, But an add-on, and to be dealt with as a separate issue.

Will see if we can get through this.
[INDENT][INDENT]nothing to it, but to do it
[/INDENT][/INDENT]

---

