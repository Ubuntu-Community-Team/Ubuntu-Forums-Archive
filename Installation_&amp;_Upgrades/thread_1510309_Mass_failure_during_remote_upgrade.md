---
title: "Mass failure during remote upgrade"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by slperwan on 2010-06-15
I went to do a much needed upgrade of my production box (hosted in the US, I'm based in Australia) via SSH from gutsy to hardy, and it failed after getting most of the way through, by suddenly saying that the file system had become read only.

This caused a massive fit by the updater, which then caused it to cancel and attempt to roll back changes. This failed due to the above mentioned read only file system problem.

Due to not having access to the actual console, I've had to raise a ticket to the hosting provider to attempt to run an fsck as it has been suggested on my mass googling within the first 30 seconds of me going "What the hell!?!?"

The complete PuTTY session is attached, but below is a manual attempt to run the "dpkg --configure -a" as it recommended to back the upgrade out.

```
root@mars:/etc/dovecot# dpkg --configure -a
dpkg: unable to access dpkg status area: Read-only file system
```I then checked the upgrade command again to see what errors it would bring up, and it returned the following

```
root@mars:/etc/dovecot# do-release-upgrade
Checking for a new ubuntu release
Traceback (most recent call last):
  File "/usr/bin/do-release-upgrade", line 31, in <module>
    m = MetaReleaseCore(useDevelopmentRelease=options.devel_release)
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/MetaRelease.py", line 55, in __init__
    self._buildMetaReleaseFile()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/MetaRelease.py", line 76, in _buildMetaReleaseFile
    os.mkdir(path)
OSError: [Errno 30] Read-only file system: '/root/.update-manager-core/'
```I then went to check the folder it mentioned as being read only in the Errno, and was informed that the file or folder did not exist (???)

I'm hoping that the hosting guys can get it sorted out for me, but at this point in time, I'm not overly optimistic due to the server currently responding to ping, but not doing anything else.

Anyone able to shed some light as to what might have gone wrong, and was it something I did or failed to not do at the time of doing the upgrade?

---

### Post by dino99 on 2010-06-15
****
File "/usr/bin/do-release-upgrade", line 31, in <module>
    m = MetaReleaseCore(useDevelopmentRelease=options.devel_release)
*****

thats a too big jump i think :lolflag:

gutsy --> lucid: cant do that man

[http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)

a workaround: follow this example to chroot the broken system (better to update the sources.list IMO)

[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

---

### Post by slperwan on 2010-06-15
Yeah.. I double checked before I started the upgrade that I was only stepping from 7.10 to 8.04..

The next step up would be to go from 8.04 LTS to 10.04 LTS

I raised a ticket with the hosting provider, and the resolution to the issue was to run a manaul fsck on the system to check and clear errors.

After the server was up from that, I then had to do a manual dpkg --configure -a, which then fixed a number of broken packages and applications. Since then I havn't found any further issues (so far, so good).

I'm now considering whether it would be a good idea to then push from 8.04 LTS to 10.04 LTS, considering that the system had as big a fit as it had with the relatively simple 7.10 to 8.04 step up.

Any pointers?

---

