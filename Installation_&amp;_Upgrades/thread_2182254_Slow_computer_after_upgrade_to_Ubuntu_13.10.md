---
title: "Slow computer after upgrade to Ubuntu 13.10"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by sisde on 2013-10-20
Hi, 

I started upgrading my ubuntu (because of the software updater). But I stopped it because of the storm. Then I restarted my computer and clicked "yes" to continue the upgrade.

But every time, now, I've got a message : 
[ATTACH=CONFIG]247097[/ATTACH]
I sent the message and clicked "Continue".

I restarted my computer but it is still slow (slow to display windows) and Date&time in  the upper-right side of the desktop aren't displayed.

I had a look on a few ubuntu user documentations and i tried this in the terminal : 
**sudo dpkg-reconfigure -phigh -a**

and i just got : 

[B]acpid stop/waiting
acpid start/running, process 7313
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
apport stop/waiting
apport start/running
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
avahi-daemon stop/waiting
avahi-daemon start/running, process 7924
Rebuilding /usr/share/applications/bamf-2.index...
update-alternatives: using /usr/share/man/man7/bash-builtins.7.gz to provide /usr/share/man/man7/builtins.7.gz (builtins.7.gz) in auto mode
bluetooth stop/waiting
bluetooth start/running, process 9106
update-initramfs: deferring update (trigger activated)
/var/lib/dpkg/info/compiz.config: 1: /var/lib/dpkg/info/compiz.config: [general]: not found
/var/lib/dpkg/info/compiz.config: 2: /var/lib/dpkg/info/compiz.config: backend: not found
/var/lib/dpkg/info/compiz.config: 3: /var/lib/dpkg/info/compiz.config: plugin_list_autosort: not found
/var/lib/dpkg/info/compiz.config: 5: /var/lib/dpkg/info/compiz.config: [gnome_session]: not found
/var/lib/dpkg/info/compiz.config: 6: /var/lib/dpkg/info/compiz.config: backend: not found
/var/lib/dpkg/info/compiz.config: 7: /var/lib/dpkg/info/compiz.config: integration: not found
/var/lib/dpkg/info/compiz.config: 8: /var/lib/dpkg/info/compiz.config: plugin_list_autosort: not found
/var/lib/dpkg/info/compiz.config: 9: /var/lib/dpkg/info/compiz.config: profile: not found
/var/lib/dpkg/info/compiz.config: 11: /var/lib/dpkg/info/compiz.config: [general_ubuntu]: not found
/var/lib/dpkg/info/compiz.config: 12: /var/lib/dpkg/info/compiz.config: backend: not found
/var/lib/dpkg/info/compiz.config: 13: /var/lib/dpkg/info/compiz.config: integration: not found
/var/lib/dpkg/info/compiz.config: 14: /var/lib/dpkg/info/compiz.config: plugin_list_autosort: not found
/var/lib/dpkg/info/compiz.config: 15: /var/lib/dpkg/info/compiz.config: profile: not found[/B]

I guess files are missing.

What can I do? 

Thanks!

---

### Post by whitesmith on 2013-10-20
You might examine this thread: [http://ubuntuforums.org/showthread.php?t=2139521](http://ubuntuforums.org/showthread.php?t=2139521)

---

### Post by Tropicalbound on 2013-10-22
This worked for me:

[http://linuxg.net/fix-slow-graphics-performance-on-ubuntu-13-04-intel-gpu/](http://linuxg.net/fix-slow-graphics-performance-on-ubuntu-13-04-intel-gpu/)

TB

---

### Post by Albert_Levin on 2013-10-22
You should restart it or just reinstall Ubuntu 13.10 and make sure you have the right one (steps are below)
1. Go here to get 13.10 if needed: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop).
2. Select 32-bit or 64-bit from the list and hit the orange button.
3. A donation page would popup, scroll down and hit [COLOR=#ff0000]"Not now, take me to the download"[/COLOR]
4. The download should begin!

---

