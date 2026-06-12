---
title: "Problems Upgrading from 9.04 to 9.10"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by LzF on 2009-11-25
Hello there,

I know I'm not the first to post this issue, and I have read a couple of other threads but it didn't help. I'm running Jaunty Jackalope on a HP-Pavillion dv4-1225dx, and when trying to updrage from the Update Manager (or the alternate 64 .iso, for that matter), I got a bunch of errors regarding Unauthenticated Packages. I tried to change the server from which I download, two brazilian ones, the American one, and tthe main server, none worked. 

```
Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

acpi-support
acpid
adduser
aisleriot
alacarte
alien
alsa-base
alsa-utils
amsn
amsn-data
anacron
app-install-data
app-install-data-partner
apparmor
apparmor-utils
apport
apport-gtk
apport-symptoms
apt
apt-transport-https
apt-utils
apt-xapian-index
aptdaemon
aptitude
...
dia
dia-common
dia-libs
dictionaries-common
diff
```And the list goes on..

As you can see, it kind of thinks ALL packages are unauthenticated, not some. I then tried to run ```
sudo apt-get update
``` but got GPG errors, as follow:

```
W: GPG error: http://archive.ubuntu.com jaunty Release: The following signatures were invalid: NODATA 2
W: GPG error: http://archive.ubuntu.com jaunty-updates Release: The following signatures were invalid: NODATA 2
W: GPG error: http://archive.ubuntu.com jaunty-security Release: The following signatures were invalid: NODATA 2
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2  Error reading from server - read (104 Connection reset by peer) [IP:]

E: Some index files failed to download, they have been ignored, or old ones used instead.
```I actually found a solution for specific keys somewhere, saying I should run:

```
gpg --keyserver subkeys.pgp.net --recv DCF9F87B6DFBCBAE
gpg --export --armor DCF9F87B6DFBCBAE | sudo apt-key add -
```For the specific key, of course. But the thing is, I don't know much about keys, and NODATA 2 means nothing to me.

If there's a way for me to restore my sources.list for apt-get and do the update/dist-upgrade, or simply uninstall Jaunty and then use the CD to install Karmic without all the trouble of reinstalling my packages/preferences and personal files, please tell me!

Thank you all, and sorry for the long post!

---

