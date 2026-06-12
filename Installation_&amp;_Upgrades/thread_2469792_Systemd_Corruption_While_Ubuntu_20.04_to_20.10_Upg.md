---
title: "Systemd Corruption While Ubuntu 20.04 to 20.10 Upgrade!"
date: 2021-12-09
forum: Installation &amp; Upgrades
---

### Post by uygardemirkoc on 2021-12-09
Yesterday I did the Ubuntu 20.04 - 20.10 update. A few bugs occurred during the update and I guess the systemd package got corrupted during this time. Currently I can't use any of the package managers like apt, dpkg. I can't update or uninstall any packages. When I run "dpkg --audit" a long list of unconfigured packages comes up. All of these packages cannot be configured as they are systemd dependent. First I tried configuring the systemd package with the command "dpkg --configure systemd". An error as below occurred:
```

Ayarlan&#305;yor: systemd (248.3-1ubuntu8) ...
systemd-machine-id-setup: error while loading shared libraries: libsystemd-shared-247.so: cannot open shared object file: No such file or directory
dpkg: systemd paketi i&#351;lenirken sorun ya&#351;and&#305; (--configure):
systemd paketi post-installation beti&#287;i kuruldu alt süreci 127 hatal&#305; ç&#305;k&#305;&#351; kodu ile sona erdi
&#304;&#351;leme s&#305;ras&#305;nda hatalarla kar&#351;&#305;la&#351;&#305;ld&#305;:[[ystemd[
```
 then tried to solve this by creating symlinks. It was only effective for this problem. These are the commands I used when creating the links:

```
udo ln -s /lib/systemd/libsystem-shared-248.so /lib/systemd/libsystemd-shared-247.so[[udo ln -s /lib/systemd/libsystem-shared-248.so /usr/lib/systemd/libsystemd-shared-247.so[
[ow the output of the command "dpkg --configure systemd" has changed to:[[[yarlan&#305;yor: systemd (248.3-1ubuntu8) ...[[ystemd-machine-id-setup: symbol lookup error: systemd-machine-id-setup: undefined symbol: log_assert_failed_unreachable_realm, version SD_SHARED[[pkg: systemd paketi i&#351;lenirken sorun ya&#351;and&#305; (--configure):[[ystemd paketi post-installation beti&#287;i kuruldu alt süreci [27[hatal&#305; ç&#305;k&#305;&#351; kodu ile sona erdi[[&#351;leme s&#305;ras&#305;nda hatalarla kar&#351;&#305;la&#351;&#305;ld&#305;:[[ystemd[
```
['ve heard that others who have done the update are having this issue as well ([https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1948904](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1948904). What can I do, please help. As you know, 127 errors mean "not found". Is it possible to make the package systems work by manually adding the missing parts of the systemd package? Thanks in advance...

---

### Post by tea for one on 2021-12-09
Systemd is inextricably linked to the OS and the launchpad bug has seen little action since it was originally reported on October 27 2021.
My instinct tells me that you would be wise to consider a fresh installation.

Have you backed up your data today?

---

### Post by Dennis N on 2021-12-09
How did you manage to get directed to Ubuntu 20.10 which is now end-of-life (unsupported)? Software Updater would direct you to the next supported release, which is 21.04.

---

### Post by tea for one on 2021-12-09
> **Dennis N said:**
> How did you manage to get directed to [COLOR="#0000FF"]Ubuntu 20.10[/COLOR] which is now end-of-life (unsupported)? Software Updater would direct you to the next supported release, which is 21.04.

Good spot - I missed that.
Even more reason to back up and start from scratch.

---

### Post by uygardemirkoc on 2021-12-09
> **tea for one said:**
> Systemd is inextricably linked to the OS and the launchpad bug has seen little action since it was originally reported on October 27 2021.
My instinct tells me that you would be wise to consider a fresh installation.

Have you backed up your data today?

That's exactly what I was afraid of. I placed an order for a disk that I can backup. :(

---

### Post by uygardemirkoc on 2021-12-09
> **Dennis N said:**
> How did you manage to get directed to Ubuntu 20.10 which is now end-of-life (unsupported)? Software Updater would direct you to the next supported release, which is 21.04.

I don't know, a window popped up stating a new version was available and I pressed the install button. I think that was one of the biggest mistakes I've ever made. Maybe this update came to me because updates other than LTS versions are turned on in the settings. It can be concluded that versions ending in x.10 have less stability than versions ending in x.04.

---

### Post by Impavidus on 2021-12-09
With 20.10 dead already, an upgrade from 20.04 to 20.10 doesn't make sense. It should have been offered when 20.10 was still alive (if you configured to system to notify you of every release upgrade), but not after that. Maybe the file with release information was outdated? Should only happen if you use a faulty mirror or restored this file from an old backup.

It may be possible to fix this issue, but the standard approach after a release upgrade has gone wrong is a fresh install. systemd is so deeply integrated into the OS that fixing this may be very hard. And when fresh installing, take the opportunity to jump directly to 21.10. Just skip 20.10 and 21.04.

Before release upgrading, I always create backups of my important files and a live disk of the next release.

---

### Post by uygardemirkoc on 2021-12-09
Thanks... So I will back up everything and re-install Ubuntu (last version). And I'll always get backups before dist upgrades... As you said fixing broken systemd is not an easy task and it is not very logical too. Fresh install will be best...

---

### Post by grahammechanical on 2021-12-09
Ubuntu versions xx.10 are stable. They are only supported for nine months. This is also true of some versions xx.04, such as Ubuntu 21.04. Every two years we get an Long Term Support version (LTS) it will have 5 years standard support with an option to extend security support for another five years - Extended Security Maintenance (ESM). Ubuntu 20.04 is LTS and we can do an online upgrade directly to Ubuntu 22.04 LTS about 6 months after it is released next year.

So, the difference between LTS releases and the 6 monthly releases is not stability but length of support life.

Regards

---

### Post by uygardemirkoc on 2021-12-10
Thanks for replay I understand the difference now.

---

### Post by lucasalastuey on 2022-01-08
I used

```
sudo cp /usr/lib/systemd/libsystemd-shared-247.so /usr/lib/
sudo apt --fix-broken install systemd-sysv
sudo apt-get --reinstall install systemd
```

and if you have de usrmerge problem

```
sudo dpkg-reconfigure usrmerge
```

---

