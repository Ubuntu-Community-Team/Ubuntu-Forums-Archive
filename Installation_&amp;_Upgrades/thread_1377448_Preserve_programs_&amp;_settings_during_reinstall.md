---
title: "Preserve programs &amp; settings during reinstall"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by ternarybit on 2010-01-10
Howdy all,

Say I want to totally reinstall Ubuntu 9.04, but I want to preserve my environment (programs & settings). I have /home on its own partition. I notice that running
```
type <program name>
```
reveals that all my programs installed from apt reside in /usr/bin or /usr/sbin.

If I were to back up /usr, /opt and /etc, then reinstall Ubuntu from scratch, remount my /home partition and copy back those dirs, could I preserve my environment just the way it is?

P.S. I want to know because I'm considering migration to an md RAID1 mirror. AFAIK there is no way to do it without reinstalling from scratch.

Thank you!

---

### Post by TwoWordz on 2010-01-10
If you want to move to Raid 1, you don't need to reinstall, you can just add your drive and setup the Raid. 

There is good documentation on Linux raid setups [here ]("http://www.linuxfoundation.org/collaborate/workgroups/linux-raid/raid_setup") and documentation on how to make a Raid array from an existing drive [here]("http://wiki.archlinux.org/index.php/Convert_a_single_drive_system_to_RAID").

As for programs, if you were to reinstall, I would do:

```
dpkg --get-selections >~myprograms.txt #export program list
```

after you reinstall:

```
dpkg --set-selections <~myprograms.txt
apt-get -u dselect-upgrade
```

This will reinstall the list of your programs.

TW

---

