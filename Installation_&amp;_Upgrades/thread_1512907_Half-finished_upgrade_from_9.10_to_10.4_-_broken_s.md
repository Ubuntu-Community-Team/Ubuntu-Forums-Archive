---
title: "Half-finished upgrade from 9.10 to 10.4 - broken system"
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by hymerman on 2010-06-18
I tried doing an upgrade of my server from 9.10 to 10.4 using the given instructions (do-release upgrade). It went well up until it found a config file I had modified and asked me which version to keep. I tried to do a diff, it asked me for the root password which I gave but it seemed to ignore. It also said I could press ctrl+D to skip this, so I did that and it gave me a shell indented a bit from the rest of the upgrade output. I assumed that wasn't right and hit ctrl+D again, which immediately powered off my system, and now when it boots it leaves me with a load of error messages and a blinking cursor, unable to type anything. The messages go:

```
mount: mounting none on /dev failed: No such device

(screen clears)

fsck from util-linux-ng 2.17.2
udevd[2932]: BUS= will be removed in a future udev version, please use SUBSYSTEM= to match the event device, or SUBSYSTEMS= to match a parent device, in /lib/udev/rules.d/52-nut-usbups.rules:6

(That last line is repeated with slightly different errors about 30 times. I think it's to do with the network UPS software I had set up which presumably has now got outdated config files.)

/dev/sda1: clean, 140888/30154752 files, 3040580/120614004 blocks (check in 4 months)
```

I just have a blinking cursor that doesn't allow me to type anything. Hitting escape makes the above messages (from the fsck line) scroll by again. I can ctrl+alt+F1 etc to get to other 'shells' but I can't type anything in those. Hitting ctrl+alt+del makes a few things scroll by and then the system restarts. The messages start with 'checking for unattended-upgrades' then a few things shutting down then "the system will now restart".

I can choose either 2.6.31-22-server or 2.6.31-14-server. The above is what happens if I choose 22, if I choose 14 I get almost the same but with a really big font so I can't quite tell, and I get left on a screen with just this on it:

```
init: plymouth main process (451) killed by SEGV signal
```

ctrl+alt+del still restarts it, and I still can't type anything.

Choosing recovery mode of either kernel does the exact same as choosing the normal kernel but with a bigger font to start with.

Before grub starts, I see something flicker on the screen and it looks like it says something like "no hard disk detected" which is odd. Grub reports that it's version 1.97~beta4.

I hope that's enough information for someone to be able to help me! Is there anything I can do to get this upgrade back on track? I've got full backups of everything but I'd rather not have to go through setting up all the various software I'd painstakingly set up.

---

### Post by hymerman on 2010-06-18
I'm sure you'll all be delighted to know I've sorted it all out, more or less. Looks like I ran into 4 or 5 other bugs, and all but the last one I cracked were red herrings. Since there were a lot of steps I took that solved problems that were only slightly related, it's hard to say exactly what I did that made it work, but it went roughly like this:

Burn a 10.4 64 bit server CD (must match the system you're repairing - I tried 32 bit desktop for an easier time but ran into many, many odd problems)

Start up a recovery shell and chroot into your old system (there are guides all over the place for that - just a few mounts and a chroot is all)

Do these about a hundred times each:
apt-get update
apt-get upgrade
dpkg --configure -a
apt-get dist-upgrade

Mix the order up a bit, it seems sometimes things get forgotten.

Eventually it'll come down to just a few packages that can't be installed due to a bug that prevents them being run from inside a chroot (which will give you errors about not connecting to upstart). Once you're there, you can restart and choose the newest kernel from grub, and you should be greeted with a login prompt finally. After that you'll want to 'apt-get upgrade' one more time to finish the job. Done!

Ignore any errors about being unable to mount 'none' and about ureadahead-other returning error status 4. Make sure you choose the recovery console from the live cd and don't do anything clever with advanced mode, or you'll get some other weird errors about fsck not existing, /bin/bash not existing, and lots of others. Ignore the errors dpkg spews out about locales, that's a dead-end and will be magically sorted out after you've done all this.

Ubuntu makes my head hurt sometimes :(

---

