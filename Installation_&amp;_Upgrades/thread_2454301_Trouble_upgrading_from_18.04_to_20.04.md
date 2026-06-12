---
title: "Trouble upgrading from 18.04 to 20.04"
date: 2020-11-26
forum: Installation &amp; Upgrades
---

### Post by astronomertom on 2020-11-26
I'm another person having the 18.04->20.04 upgrade blues...
Been wanting to do this for a few months so I've been following all manner of threads on this topic.

I recently installed the GRUB2 update which seem to clear the block on this upgrade.

So I've turned off the 3rd-party PPAs, unchecking in 'Software & Updates' as suggested in this thread (hadn't seen that in other threads)..

Then went through the usual:

[B]sudo apt-get update
sudo apt-get upgrade --yes
sudo apt autoremove
sudo apt-get dist-upgrade --yes[/B]

It updated a few web-related things (webkit, javascript stuff)

**sudo do-release-upgrade**
[I]Checking for a new Ubuntu release
Failed to connect to [https://changelogs.ubuntu.com/meta-release-lts](https://changelogs.ubuntu.com/meta-release-lts). Check your Internet connection or proxy settings
There is no development version of an LTS available.
To upgrade to the latest non-LTS develoment release 
set Prompt=normal in /etc/update-manager/release-upgrades.
[/I]
Yet I can access the link: [https://changelogs.ubuntu.com/meta-release-lts](https://changelogs.ubuntu.com/meta-release-lts)
 fine through a browser and it does show 20.04.1 available.

[B]sudo update-manager -c
[/B] 
similarly reports inability to access changelogs.

Why is it failing to make the connection??
Other suggestions?
Thanks.

---

### Post by Bashing-om on 2020-11-26
astronomertom; Hello -

As the package manager suggest; did you check what is set in the /etc/update-manager/release-upgrade file ?

What shows:
```

grep -i ^prompt /etc/update-manager/release-upgrades

```

[INDENT]any thought better than no thought
[/INDENT]

---

### Post by astronomertom on 2020-11-27
It's set to 'lts' of course.

I just realized do-release-upgrade is Python code...  
How does m.new_dist get set?
What's happening in MetaReleaseCore?

I have anaconda python 3 installed in /opt.  Could that be conflicting with the python3 in /usr/bin?  All show up with
whereis python
but only anaconda appears for
which python

Where is the UpdateManager module?

/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py

There's a few python items in this which I'm not that familiar with, but there's some complex decision trees in this...

---

### Post by astronomertom on 2020-11-28
I've been trying to debug MetaRelease.py with no real success. 
The log files in /var/log/dist-upgrade/ show nothing related to these update attempts.
Oddly the log files are timestamped nearly a year ago.  Checking this date in my notes, I apparently received messages about 'Partial Update' from Software Updater and I ran as a partial update.
My guess is that there's some bad data element saved from some earlier update attempt that is not permitting UpdateManager to continue forward.

I'd like to do an upgrade on this machine, but I'm using it in a 'work-from-home' configuration and would like to avoid the time it would require to do a fresh install of the OS and all the additional software I need.

---

