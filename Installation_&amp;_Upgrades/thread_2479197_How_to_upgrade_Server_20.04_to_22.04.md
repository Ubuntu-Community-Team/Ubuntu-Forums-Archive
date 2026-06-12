---
title: "How to upgrade Server 20.04 to 22.04"
date: 2022-09-17
forum: Installation &amp; Upgrades
---

### Post by mikolajkazmierczak on 2022-09-17
As in title. I'm a newbie.

---

### Post by aljames2 on 2022-09-17
Before doing anything you should verify that you have all your data backed up in a separate backup location, and that you know how to do a restore on a fresh installation if needed.  Backup doesn't mean a clone or mirror.  Know where all your configuration files are, and know how to access them if your system is down so that you can restore to a new installation if needed.  Once you are confident you can recover if something goes wrong, then look in to how to upgrade if you must.

Perhaps you have found this.  Read through it all & understand it before doing anything.
[https://ubuntu.com/server/docs/upgrade-introduction](https://ubuntu.com/server/docs/upgrade-introduction)

---

### Post by MAFoElffen on 2022-09-17
Once upgraded with the latest updates...
```

sudo apt update && sudo apt upgrade
[code]
Backup using your preferred method to a different drive.

Then upgrade the release
[code]
sudo do-release-upgrade

```

Though honestly, if doing a production server, I migrate to the newer release, instead of upgrade the release in place:
- Update to latest updates.
- Backup data and configs.
- I dump the manually installed packages. Process that list to just the applications that were installed.
- I check the storage for any potential problems and do any maintenance. Then wipe the disks, changing out any old disks.
- Install the new release.
- Install the applications. I do this from a post install script made from the processed list.
- Install the config files and data from my backups.
- Test the system.

---

### Post by TheFu on 2022-09-17
Regardless of what you do, server programs have been upgraded, so if you are running a DBMS or webapp or some other language specific program on the server, you'll still need to manually validate that program supports the 22.04 software stack. For example, if running wordpress, expect it to fail until the php is modified for the new php version in 22.04.  There are always little things that change with each release, so any custom stuff might break too.

As with all patching or upgrades, ensure you have know-you-can-recover backups BEFORE starting.  Bad things sometimes happen. Nobody can be certain that won't happen to you.  Also, some upgrades take a few hours. During this time, the system is unavailable.  OTOH, with a flexible backup solution, a fresh install is usually about 15 minutes and restoring the data and settings another 30 minutes, then just install the APT packages from a list you made on the old system, so that list can be provided to APT for manual installation on the new system.  If the settings, configs and data are all where expected, with the correct owner, group, permissions, ACLs, and xattrs, then APT will see the settings and data, use them as part of the package install ... this usually works fine, but for some things like samba, nfs, GPUs, all DBMS, webapps, expect config problems.  

And be certain to read the release notes for the new release - the general RN and the "Server" RN.  Better to know about issues that others have already seen.  With samba, every LTS release has changed defaults, which means that some clients are impacted, unless you happen to be running only Linux Samba clients (which should be avoided - use NFS!).

---

### Post by mikolajkazmierczak on 2022-09-18
But I have 20.04 and apt says that repos for this version don't have a Release file. What to do? This is on my small home server.

---

### Post by TheFu on 2022-09-18
> **mikolajkazmierczak said:**
> But I have 20.04 and apt says that repos for this version don't have a Release file. What to do? This is on my small home server.

You've lost me.  What's a release file?  I said "release notes."  Those are very specific for every distro of every OS. Use google. Details matter.

---

### Post by mikolajkazmierczak on 2022-09-18
I did it!

---

