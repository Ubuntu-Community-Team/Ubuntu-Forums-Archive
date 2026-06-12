---
title: "Upgrade to 13.04 stopped midway!"
date: 2013-04-27
forum: Installation &amp; Upgrades
---

### Post by Stonecold1995 on 2013-04-27
I was updating Kubuntu 12.10 to 13.04, but the updater stopped midway saying that some error has occurred and that it would run "dpkg -a --configure" after I press cancel.  I forget exactly how far the update was in but it was probably between 40 and 70% (of configuring and installing packages, they had already downloaded).  Anyway, I cannot finish the upgrade because do-release-upgrade thinks I am already at 13.04!

Running "sudo dpkg -a --configure" outputs nothing, and "sudo apt-get -f install" doesn't find anything to fix.  When I try running "sudo apt-get dist-upgrade", it tries to install a single package but fails:
```
alex@kubuntu:~$ sudo apt-get dist-upgrade
Reading package lists...Building dependency tree...
Reading state information...
The following packages will be upgraded:
  live-tools
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/25.8 kB of archives.
After this operation, 52.2 kB of additional disk space will be used.
Do you want to continue [Y/n]?
(Reading database ... 436153 files and directories currently installed.)
Preparing to replace live-tools 3.0.8-1 (using .../live-tools_3.0.17-1_all.deb) ...
dpkg-divert: error: `diversion of /usr/sbin/update-initramfs to /usr/sbin/update-initramfs.orig.initramfs-tools by live-tools' clashes with `diversion of /usr/sbin/update-initramfs to /usr/sbin/update-initramfs.initramfs-tools by live-tools'
dpkg: error processing /var/cache/apt/archives/live-tools_3.0.17-1_all.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/live-tools_3.0.17-1_all.deb
```

Please help!  I'm afraid to shut down my computer because I'm not sure if it'll boot again (I have never had an update fail like this, and I've upgraded from 11.04 to 11.10 to 12.04 to 12.10 without ever encountering this problem).

Is there a way I can force the upgrade to continue so I'm not stuck with a potentially broken half-upgraded system?

---

### Post by ibjsb4 on 2013-04-27
Have you tried removing live-tools and then dist-upgrade?

---

### Post by Stonecold1995 on 2013-04-27
I was thinking of that but live-tools looks like it contains vital programs for booting up (initramfs stuff).

I'm worried I'll remove it, and then it won't re-install and then god forbid my computer crashes and I need to reboot...  I'm using full disk encryption so live ramfs stuff is vital.

Is it safe to remove?  Are there any files in /sbin or /bin or wherever that I should manually back up?

---

### Post by ibjsb4 on 2013-04-27
I can only say that its not installed on my Classic only system.

---

### Post by Stonecold1995 on 2013-04-27
I looked in the .deb package that was giving me trouble.  When I opened it with Ark I found the part that specifies the files it creates.  Do you have any of these files?
```
f60015875f042750bad14fc8897ddb50  bin/live-persistence90c9792fa9a83d73fc9e0af9a4120ed9  bin/live-system
9e22cf000533246697435e4db1781920  bin/live-toram
8a411c7fb6eadc805b711105f36852de  bin/live-update-initramfs
0e87b6472e55c6fa95ef6c3b786d7078  bin/live-update-initramfs-uuid
6da6a289482d7cb4a6ba35f42fba0cbb  bin/live-uptime
b24b4a8516d7548a91e1ba26b61a1a8d  usr/share/bug/live-tools/presubj
73eff1e8736b127452679f96e683a00b  usr/share/doc/live-tools/changelog.Debian.gz
b8e5dea12157459a22d5d26531ead938  usr/share/doc/live-tools/copyright
63858460eee689940700a0fb3c9ba827  usr/share/man/ca/man1/live-uptime.1.gz
56d05bb601dded7f3ace87d5f9c6a343  usr/share/man/ca/man7/live-tools.7.gz
0d87763ab862192b8318455ac5cca08d  usr/share/man/ca/man8/live-update-initramfs.8.gz
ae3abac5c45c8e7fc374cdd4bb9edb33  usr/share/man/de/man1/live-uptime.1.gz
f8f964f41e7fcc4c256a896bfeed969f  usr/share/man/de/man7/live-tools.7.gz
4987188241f490fad367d63298a8dd8a  usr/share/man/de/man8/live-update-initramfs.8.gz
83d195df8d9008f3cc97124e5902ee37  usr/share/man/es/man1/live-uptime.1.gz
eb2884c1a12e88537c7c40c4f1b72913  usr/share/man/es/man7/live-tools.7.gz
935f0d664132cd08b700d7d992ef09d4  usr/share/man/es/man8/live-update-initramfs.8.gz
68f89f24ad69ddaef195dfee6fa7d1dc  usr/share/man/fr/man1/live-uptime.1.gz
cd70b4bf7655dcf90910c7e1354da5b5  usr/share/man/fr/man7/live-tools.7.gz
dd5f2f1cf625a5fd98f3dc766bebcede  usr/share/man/fr/man8/live-update-initramfs.8.gz
85b109dd405c010bbe98cf10582d37cc  usr/share/man/man1/live-uptime.1.gz
60b87fde9c89154c9c0209e2fb61e824  usr/share/man/man7/live-tools.7.gz
c6b2f7977e7125d2b985217d5c74351d  usr/share/man/man8/live-update-initramfs.8.gz
```

Also, if I do manage to get live-tools upgraded correctly, how do I get the release upgrade to FINISH the process?  I really don't want to have to format my drive and re-install just because the upgrade stopped midway...  That's my primary problem, getting the upgrade to resume from where it left off.

It looks like my computer is now having misc problems.  Like for example, if I try to change the priority of a process using ksysguard nothing happens.

---

### Post by darkod on 2013-04-27
I'm not sure if the command works in reverse too (it might), but shouldn't it be:
```
sudo dpkg --configure -a
```

The option --configure comes first, and the -a means all. Although, it's linux so the order might not mean much.

Also, even if you reboot and it doesn't boot, it should boot the recovery mode where you should be able to do the dpkg --configure -a and apt-get install -f. Don't forget that the recovery mode root shell is read only, you have to remount root as RW:
```
mount -o remount,rw /
```

The commands might have better effect after the reboot, but I can't really guarantee it.

---

### Post by ibjsb4 on 2013-04-27
> Do you have any of these files?

Nope

---

### Post by Stonecold1995 on 2013-04-27
> **darkod said:**
> I'm not sure if the command works in reverse too (it might), but shouldn't it be:
```
sudo dpkg --configure -a
```

The option --configure comes first, and the -a means all. Although, it's linux so the order might not mean much.

Also, even if you reboot and it doesn't boot, it should boot the recovery mode where you should be able to do the dpkg --configure -a and apt-get install -f. Don't forget that the recovery mode root shell is read only, you have to remount root as RW:
```
mount -o remount,rw /
```

The commands might have better effect after the reboot, but I can't really guarantee it.
Well, "sudo dpkg --configure -a" seemed to do something.  More packages were upgraded.  I'm still having some instability issues in general though.

Also, I removed live-tools and it DID manage to install afterwards.  Yay!  Now I'm about to reboot.  Hopefully the upgrade will be fully active.

---

### Post by Stonecold1995 on 2013-04-27
Well, I rebooted and it seemed to work.  Now I have one other, more minor but very annoying problem.  My mouse acceleration seems to have changed!  Now when I move the cursor via my touchpad up or down, the speed is too high!  I can go from top to bottom in about a half stroke, but it takes me two strokes to go from left to right.  How do I decrease the vertical speed?

---

