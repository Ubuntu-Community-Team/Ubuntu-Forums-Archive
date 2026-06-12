---
title: "Install with preseed from CD: Software from non-cd does not install"
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by axeljaeger on 2006-10-22
Hello all,
I'm currently making my own dapper-cd that should install with no user interaction.

My plan is to install an ubuntu server with two additional packages: ssh and avahi-daemon. ssh installs fine, avahi-daemon does not.

Here is my preseed-file:
```

# Always install the server kernel.
d-i     base-installer/kernel/override-image    string linux-server
# Don't install usplash.
d-i     base-installer/kernel/linux/extra-packages-2.6  string
# Desktop system not installed; don't waste time and disk space copying it.
d-i     archive-copier/desktop-task     string ubuntu-standard
d-i     archive-copier/ship-task        string

# Only install the standard system and language packs.
d-i     pkgsel/install-pattern  string ~t^ubuntu-standard$|~n^ssh$|~n^avahi-daemon$
d-i     pkgsel/language-pack-patterns   string

d-i apt-setup/restricted boolean true
d-i apt-setup/universe boolean true
d-i apt-setup/backports boolean true

# No language support packages.
d-i     pkgsel/install-language-support boolean false

d-i     netcfg/get_hostname     string ubuntuserver
d-i     partman-auto/disk                  string /dev/discs/disc0/disc
d-i     partman/confirm                     boolean true
# base-config  tzconfig/gmt           boolean true
d-i clock-setup/utc boolean false
d-i prebaseconfig/reboot_in_progress note

d-i passwd/user-fullname string Axel Jaeger
d-i passwd/username string axeljaeger
d-i passwd/user-password password xxxxxx
d-i passwd/user-password-again password xxxxxx 

```

My guess is that the install fails because avahi is not on the cd but only available on the servers. ssh is contained within the packages on the cd.

My question is: Is there a way to say the installer that it should download avahi-daemon plus all dependencies either during the setup or close afterwards? I know there is preseed/late_command but this seems to be an unclear way for me because I can only execute one command and package installing should be handled by pkgsel/install-pattern (I think).

Thanks for suggestions and ideas.

---

