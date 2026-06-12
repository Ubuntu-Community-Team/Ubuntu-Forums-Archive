---
title: "Upgrade to Precise hangs"
date: 2012-08-30
forum: Installation &amp; Upgrades
---

### Post by awacs on 2012-08-30
.. it just goes off to la-la land. End of /var/log/dist*/main.log:

2012-08-29 19:58:17,091 DEBUG check if patch _usr_bin_pycompile.b17cebfbf18d152
702278b15710d5095.97c07a02e5951cf68cb3f86534f6f917' needs to be applied
2012-08-29 19:58:17,092 DEBUG target for '_usr_bin_pycompile.b17cebfbf18d1527022
78b15710d5095.97c07a02e5951cf68cb3f86534f6f917' is '_usr_bin_pycompile' -> '/usr/bin/pycompile'
2012-08-29 19:58:17,135 WARNING unexpected target md5sum, skipping: '/usr/bin/pycompile'
2012-08-29 19:58:17,136 DEBUG skipping 'README' (no '.')
2012-08-29 19:58:17,192 DEBUG killing update-notifier
2012-08-29 19:58:17,228 DEBUG killing kblueplugd kbluetooth4
2012-08-29 19:58:17,257 DEBUG killing gnome-screensaver
2012-08-29 19:58:17,287 DEBUG apt btrfs snapshots supported: False
2012-08-29 19:58:17,288 INFO cache.commit()
2012-08-29 19:58:17,289 DEBUG failed to SystemUnLock() (E:Not locked)

Top indicates that 'precise' is doing *something*, but dunno what.

Been like this since last night. What do I do?

---

### Post by awacs on 2012-08-30
I quit the terminal session and started again. It hung again, with the last message on the screen talking about "memtest86+ parse error ..." (I can post a screenshot if desired). Top shows 'precise' occasionally running.

?

---

### Post by critin on 2012-08-30
Don't know if this will help, but 

[http://ubuntuforums.org/showthread.php?t=1983533&page=3](http://ubuntuforums.org/showthread.php?t=1983533&page=3)

[http://superuser.com/questions/420595/repair-ubuntu-after-unsuccesful-upgrading](http://superuser.com/questions/420595/repair-ubuntu-after-unsuccesful-upgrading)

---

### Post by awacs on 2012-08-30
> **critin said:**
> Don't know if this will help, but 

[http://ubuntuforums.org/showthread.php?t=1983533&page=3](http://ubuntuforums.org/showthread.php?t=1983533&page=3)

[http://superuser.com/questions/420595/repair-ubuntu-after-unsuccesful-upgrading](http://superuser.com/questions/420595/repair-ubuntu-after-unsuccesful-upgrading)

No, but thanks for the suggestion.

I guess I should mention that I'm upgrading with do-release-upgrade (and not by booting a CD).

---

### Post by awacs on 2012-08-30
Tried it three times over a telnet window, and each time it broke in the same place.

Then, I tried it over a SSH connection from another machine and ... it works!

I guess that means something to somebody, but I'm stumped.

---

### Post by awacs on 2012-08-30
Uh-oh. I got further, but now I have:

_____________________________
Errors were encountered while processing:
 samba4
Error in function:
A fatal error occurred

Please report this as a bug and include the files
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in
your report. The upgrade has aborted.
/etc/apt/sources.list.distUpgrade.

SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)

Could not install the upgrades

Error during commit 'E:Couldn't configure pre-depend multiarch-support for libapt-pkg4.12, probably a dependency cycle.'
__________________________
What do I do now?

---

### Post by awacs on 2012-08-30
Some research I've done suggests that I should install apt (separately) from Precise.

How do I do that?

---

