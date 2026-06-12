---
title: "How to stop APT from automatically downloading packages?"
date: 2018-10-12
forum: Installation &amp; Upgrades
---

### Post by doctordruidphd on 2018-10-12
The problem: After automatically doing an apt update, the system downloads all upgradeable packages. This ties up network resources at an inappropriate time.

What I want it to do:  DO automatically check for updates, i.e. apt-get update, and notify me (this works). DO NOT download upgradeable packages; I will do this manually when network resources are not otherwise needed.

I have noticed this behavior on Debian, and so far I have not been able to stop it. It just appeared on kubuntu with the upgrade to 18.10, so something has changed.

My /etc/apt/apt.conf.d/10periodic file is:

```
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::Download-Upgradeable-Packages-Debdelta "0";
APT::Periodic::Unattended-Upgrade "0";
APT::Periodic::AutocleanInterval "0";
```

Since everything connected with APT is turned off, I suspect the problem is really somewhere in the systemd stuff, but so far I have not been able to find it. It is a real irritation because I have to go in and manually kill a bunch of apt-methods processes when it starts, in order to just read my email.

---

### Post by ajgreeny on 2018-10-12
I always uninstall the unattended-upgrades package as I do not want the system doing the job for me, and prefer to maintain my own manual control.

This does, of course, depend upon me ensuring that I manually upgrade often; I do so daily, except when I am away from the computer and it is the turned off so not a problem.
I also set the update preferences as shown in the screenshot below so nothing is downloaded until I manually ask for upgrades.

NB: This screenshot is from xenial but it's the same in bionic.

---

### Post by doctordruidphd on 2018-10-12
This is what is so mysterious.  Unattended-upgrades is NOT installed. Software-properties-kde is set just as yours is -- to check for updates and notify only, not to download anything.

For these reasons, I'm pretty sure this problem has its source somewhere in systemd. I notice that what is actually running after boot is:

```
root      1984  0.0  0.0   2560   820 ?        Ss   14:00   0:00 /bin/sh /usr/lib/apt/apt.systemd.daily update
```

and I also see: 

```
root      2135  0.3  0.6  69792 54876 ?        R    14:01   0:01 apt-get -qq -y update
```

which the man page for apt-get warns against:

```
-q, --quiet
           Quiet; produces output suitable for logging, omitting progress indicators. More q's will
           produce more quiet up to a maximum of 2. You can also use -q=# to set the quiet level,
           overriding the configuration file. Note that quiet level 2 implies -y; [B]you should never
           use -qq without a no-action modifier such as -d, --print-uris or -s as APT may decide to
           do something you did not expect.[/B] Configuration Item: quiet.
```

as it is indeed doing.

I checked /usr/lib/apt/apt-systemd-daily, and there is actually stuff in there about doing automatic downloads, though it is SUPPOSED to be reading /etc/apt/apt.conf.d/10periodic for instructions, which apparently it is ignoring. apt-systemd-daily is a bit too much of a rube-goldberg script for me to untangle why it isn't following instructions.

---

### Post by doctordruidphd on 2018-10-18
Further information on this:

What I have discovered is that multiple programs are running updates on the system.

1. systemd is running /lib/systemd/system/apt-daily.service and apt-daily-upgrade.service.

2. systemd is running packagekit.service  (packagekit is still here?)

3. cron is running /etc/cron.d/apticron

And who knows what else I haven't found yet. The net result of all this garbage is that every time I turn on the computer, one thing or another starts running an apt update and/or downloading packages. This is ridiculous. this should only be run once a day, if not done manually. I guess what I need to do is every time one of these things starts, just delete whatever is running it from the disk, and do the update/upgrades manually from now on.

---

