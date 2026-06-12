---
title: "Ubuntu Server 6.10 (Edgy Eft) to 7.04 (Feisty Fawn): &quot;do-release-upgrade&quot; problem."
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by aznach on 2007-11-14
Hi,

While attempting to upgrade (a VMware) Ubuntu Server 6.10 (Edgy Eft) to 7.04 (Feisty Fawn) using "do-release-upgrade", the script terminated unexpectedly.

stdout:

""

Starting tor daemon: tor...
Nov 14 19:25:45.496 [notice] Tor v0.1.1.26. This is experimental software. Do not rely on it for strong anonymity.
Nov 14 19:25:45.505 [notice] Initialized libevent version 1.1a using method epoll. Good.
Nov 14 19:25:45.509 [notice] connection_create_listener(): Opening Socks listener on 127.0.0.1:9050
Nov 14 19:25:45.512 [notice] connection_create_listener(): Opening Socks listener on 10.0.0.152:9050
Nov 14 19:25:45.513 [warn] connection_create_listener(): Could not bind to 10.0.0.152:9050: Cannot assign requested address
Nov 14 19:25:45.515 [notice] options_act_reversible(): Closing Socks listener on 127.0.0.1:9050
Nov 14 19:25:45.517 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
Nov 14 19:25:45.517 [err] tor_init(): Reading config failed--see warnings above. For usage, try -h.
invoke-rc.d: initscript tor, action "start" failed.
dpkg: error processing tor (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 tor

Could not install the upgrades
The upgrade aborts now. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a).

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
installArchives() failed
Setting up tor (0.1.1.26-1) ...
debian-tor uid check: ok
debian-tor homedir check: ok
Raising maximum number of filedescriptors (ulimit -n) to 8192.
Starting tor daemon: tor...
Nov 14 19:25:46.377 [notice] Tor v0.1.1.26. This is experimental software. Do not rely on it for strong anonymity.
Nov 14 19:25:46.393 [notice] Initialized libevent version 1.1a using method epoll. Good.
Nov 14 19:25:46.400 [notice] connection_create_listener(): Opening Socks listener on 127.0.0.1:9050
Nov 14 19:25:46.409 [notice] connection_create_listener(): Opening Socks listener on 10.0.0.152:9050
Nov 14 19:25:46.419 [warn] connection_create_listener(): Could not bind to 10.0.0.152:9050: Cannot assign requested address
Nov 14 19:25:46.425 [notice] options_act_reversible(): Closing Socks listener on 127.0.0.1:9050
Nov 14 19:25:46.430 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
Nov 14 19:25:46.432 [err] tor_init(): Reading config failed--see warnings above. For usage, try -h.
invoke-rc.d: initscript tor, action "start" failed.
dpkg: error processing tor (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 tor

""

**For more information, see attachments:**

/var/log/dist-upgrade/main.log
/var/log/dist-upgrade/apt.log


**My questions are:**

- What would be a sensible thing to do next?

- Which commands should I use (to somehow resume the upgrade, or fix issues)?

- Should I resolve the "tor" issue and reissue the "do-release-upgrade" command?

- Should I try?:

""
apt-get update
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
""
- Or use aptitude?

- What if I reboot?


[B]
Any clues or help would be very much appreciated!
Thanks in advance.[/B]


Best regards,
Az

---

