---
title: "Upgrade to Gutsy failed"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by jimtb on 2007-10-29
During the upgrade to Gutsy there was an error about the package "torrentflux" which could not be upgraded. 
As a result the upgrade process could not continue and the update-manager informed me that my system could be unusable. I run dpkg --configure -a but nothing happened and now the OS things it is upgraded, as neither update-manager nor apt-get dist-upgrade find any new distro version.

(update-manager --dist-upgrade) ***Your system is up to date:*** [I]There are no upgrades available for your system. The upgrade will now be canceled.
[/I]
```
jimakos@jimakos-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Any ideas on what I can do to solve this?

Thanks for your help.

:-)

---

### Post by mlind on 2007-10-29
Did you run 'dpkg --configure -a' as root?
```

sudo dpkg --configure -a

```

---

### Post by jimtb on 2007-10-29
> **mlind said:**
> Did you run 'dpkg --configure -a' as root?
```

sudo dpkg --configure -a

```

Yes and still nothing happened.
Is there any way to find out if my system is fully upgraded or not?

---

### Post by mlind on 2007-10-29
> **jimtb said:**
> Yes and still nothing happened.

It sounds that your system is up-to-date and okay then. Otherwise dpkg would be very noisy about unmet/unconfigured dependencies. Do you have any logs left from the upgrade process in /var/log/ ?

---

### Post by jimtb on 2007-10-29
> **mlind said:**
> It sounds that your system is up-to-date and okay then. Otherwise dpkg would be very noisy about unmet/unconfigured dependencies. Do you have any logs left from the upgrade process in /var/log/ ?

Yes, the file is huge(about 25000 lines). Here are the last lines:
**dpkg.log:**
```
2007-10-29 19:07:53 status installed kdepim 4:3.5.7enterprise20070926-0ubuntu2
2007-10-29 19:07:53 status unpacked kitchensync 4:3.5.7enterprise20070926-0ubuntu2
2007-10-29 19:07:54 status half-configured kitchensync 4:3.5.7enterprise20070926-0ubuntu2
2007-10-29 19:07:55 status installed kitchensync 4:3.5.7enterprise20070926-0ubuntu2
2007-10-29 19:07:56 status half-configured libc6 2.6.1-1ubuntu9
2007-10-29 19:08:41 status installed libc6 2.6.1-1ubuntu9
2007-10-29 19:08:41 status half-configured initramfs-tools 0.85eubuntu20
2007-10-29 19:09:05 status installed initramfs-tools 0.85eubuntu20
2007-10-29 19:09:48 status half-configured torrentflux 2.3-2ubuntu1
2007-10-29 19:10:35 startup packages remove
2007-10-29 19:10:35 status half-configured torrentflux 2.3-2ubuntu1
2007-10-29 19:11:12 remove torrentflux 2.3-2ubuntu1 2.3-2ubuntu1
2007-10-29 19:11:12 status half-configured torrentflux 2.3-2ubuntu1
2007-10-29 19:11:55 status installed torrentflux 2.3-2ubuntu1
2007-10-29 19:12:06 startup packages purge
2007-10-29 19:12:06 status installed torrentflux 2.3-2ubuntu1
2007-10-29 19:12:09 remove torrentflux 2.3-2ubuntu1 2.3-2ubuntu1
2007-10-29 19:12:09 status half-configured torrentflux 2.3-2ubuntu1
2007-10-29 19:12:15 status half-installed torrentflux 2.3-2ubuntu1
2007-10-29 19:12:16 status config-files torrentflux 2.3-2ubuntu1
2007-10-29 19:12:16 purge torrentflux 2.3-2ubuntu1 2.3-2ubuntu1
2007-10-29 19:12:16 status config-files torrentflux 2.3-2ubuntu1
2007-10-29 19:12:16 status config-files torrentflux 2.3-2ubuntu1
2007-10-29 19:12:16 status config-files torrentflux 2.3-2ubuntu1
2007-10-29 19:12:18 status config-files torrentflux 2.3-2ubuntu1
2007-10-29 19:12:18 status config-files torrentflux 2.3-2ubuntu1
2007-10-29 19:12:18 status not-installed torrentflux <none>
2007-10-29 19:16:40 startup packages configure
2007-10-29 19:27:53 startup packages configure
2007-10-29 20:02:43 startup packages configure
```

---

### Post by mlind on 2007-10-29
Could gzip contents of /var/log/dist-upgrade/ and attach the file ?

---

### Post by jimtb on 2007-10-29
Well I've been working on my PC for about two hours and I didn't notice anything strange indicating that something went wrong(except fglrx not working grrr). 

Anyway, I attached the logs just in case. 

Thanks for helping. :-)

---

### Post by mlind on 2007-10-29
To me it seems that distribution upgrade went fine. torrentflux failed to upgrade its database, but that didn't interfere the dist-upgrade. maybe mysql database wansn't running when it tried to dump the backup, dunno.

Did you manage to solve the torrentflux install/upgrade yet? Try to upgrade packages using your preferred package manager. If torrentflux still fails to upgrade, then purge it and reinstall.

---

### Post by jimtb on 2007-10-29
> **mlind said:**
> To me it seems that distribution upgrade went fine. torrentflux failed to upgrade its database, but that didn't interfere the dist-upgrade. maybe mysql database wansn't running when it tried to dump the backup, dunno.

Did you manage to solve the torrentflux install/upgrade yet? Try to upgrade packages using your preferred package manager. If torrentflux still fails to upgrade, then purge it and reinstall.

It seems that there is no problem after all. As for torrentflux, I haven't used it for a long time so I don't really mind not upgrading it at the moment.

Again, thanks for all your help.

:-)

---

