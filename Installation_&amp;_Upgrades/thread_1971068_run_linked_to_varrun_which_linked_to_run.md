---
title: "/run linked to /var/run which linked to /run"
date: 2012-05-02
forum: Installation &amp; Upgrades
---

### Post by climberjc on 2012-05-02
Hi,

For a little background, I upgraded from 11.10 to 12.04 on a 64-bit desktop and have had a series of problems recovering the system. It's hard for me to include log files since the system is down to a command line. I'm just transcribing things.

I got the glibc error after upgrading described in 
[http://askubuntu.com/questions/125649/reboot-during-update-glibc-error](http://askubuntu.com/questions/125649/reboot-during-update-glibc-error)
and followed their directions to correct the problem with a modification of installing mdadm and mounting my raid filesystem. I used the directions in [http://www.jeffsplace.net/node/14](http://www.jeffsplace.net/node/14) and [http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount) for that. 

After restart, I got an error "run: Too many levels of symbolic links" that prevented startup from moving forward.

Sure enough, somehow /run was now linked to /var/run, and /var/run was linked to /run. I found that the developers made /run the new place for temporary files to be stored during boot. [http://askubuntu.com/questions/57297/why-has-var-run-been-migrated-to-run](http://askubuntu.com/questions/57297/why-has-var-run-been-migrated-to-run)

I figured I could just rm or rmdir or unlink the directories and then mkdir new versions that weren't linked. Unfortunately, everything I tried, including rm -rf /run, gives me an error:
"cannot remove 'run': Read-only file system.

I cannot figure out what to do from here. I'd appreciate any help!

Thanks,
Jere

---

### Post by climberjc on 2012-05-13
If anyone can tell me how to fix this symbolic link loop from the command line, I'd really appreciate it. I have not found any solution, so my machine is not usable after the upgrade.

---

