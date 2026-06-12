---
title: "Cannot update Ubuntu 22.04 Error: 503 OUT OF DISK SPACE"
date: 2024-10-29
forum: Installation &amp; Upgrades
---

### Post by gdundee on 2024-10-29
[COLOR=#0C0D0E][FONT=-apple-system]When I run 'sudo apt-get update' I receive the following output: 503 OUT OF DISK SPACE

Output:
[/FONT][/COLOR]
Ign:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease
Hit:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy InRelease
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InRelease
Ign:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease
Ign:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease
Ign:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease
Ign:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-security InRelease
Ign:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease
Ign:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease
Ign:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease
Ign:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease
Ign:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-security InRelease
Ign:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease
Ign:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease
Ign:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease
Ign:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease
Ign:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-security InRelease
Err:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease
  503  OUT OF DISK SPACE [IP: 69.65.176.22 3142]
Err:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease
  503  OUT OF DISK SPACE [IP: 69.65.176.22 3142]
Err:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease
  503  OUT OF DISK SPACE [IP: 69.65.176.22 3142]
Err:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease
  503  OUT OF DISK SPACE [IP: 69.65.176.22 3142]
Err:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-security InRelease
  503  OUT OF DISK SPACE [IP: 69.65.176.22 3142]
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease)  503  OUT OF DISK SPACE [IP: 69.65.176.22 3142]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease)  503  OUT OF DISK SPACE [IP: 69.65.176.22 3142]
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jammy-security/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/jammy-security/InRelease)  503  OUT OF DISK SPACE [IP: 69.65.176.22 3142]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease)  503  OUT OF DISK SPACE [IP: 69.65.176.22 3142]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease](http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease)  503  OUT OF DISK SPACE [IP: 69.65.176.22 3142]
W: Some index files failed to download. They have been ignored, or old ones used instead.


[COLOR=#0C0D0E][FONT=-apple-system]I have ran:[/FONT][/COLOR]
[HTML]sudo snap set system proxy.http="http://aptcacher.atu.edu:3142"
sudo snap set system proxy.https="http://aptcacher.atu.edu:3142"
[/HTML][COLOR=#0C0D0E][FONT=-apple-system]I have tried: sudo apt-get clean[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]I also added more drive space to the machine, and I have about 15GB available on the disk sda2.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]I have tried rebooting the server as well.[/FONT][/COLOR]

---

### Post by 1fallen on 2024-10-29
You did not say if ever ran:
```
sudo apt autoremove
### also this one
sudo apt autoremove --purge
```
show us this as well please:
```
[FONT=monospace][COLOR=#000000]inxi -p|grep /boot[/COLOR]

```
That might get us started

[/FONT]

---

### Post by yancek on 2024-10-29
What is /dev/sda2?  Is that your / filesystem partition?  What does df -h command show as far as disk space and space used?

---

### Post by gdundee on 2024-10-29
I was able to diagnose my issue.  My server was pointing to a proxy server for updates, and the proxy server (apt-cacher-ng) was in fact out of disk space.  We cleared up some of the space, and now I am good to go!

---

