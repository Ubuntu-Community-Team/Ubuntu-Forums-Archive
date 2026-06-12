---
title: "sudo apt upset"
date: 2022-09-28
forum: Installation &amp; Upgrades
---

### Post by ipv2 on 2022-09-28
01

sudo apt update

gives me this:

14 packages can be upgraded. Run 'apt list --upgradable' to see them.

apt list --upgradable

give me this :

Listing... Done
libnss-systemd/jammy-updates 249.11-0ubuntu3.6 amd64 [upgradable from: 249.11-0ubuntu3.4]
libpam-systemd/jammy-updates 249.11-0ubuntu3.6 amd64 [upgradable from: 249.11-0ubuntu3.4]
libspeechd2/jammy-updates 0.11.1-1ubuntu2 amd64 [upgradable from: 0.11.1-1ubuntu1]
libsystemd0/jammy-updates 249.11-0ubuntu3.6 amd64 [upgradable from: 249.11-0ubuntu3.4]
libudev1/jammy-updates 249.11-0ubuntu3.6 amd64 [upgradable from: 249.11-0ubuntu3.4]
python3-speechd/jammy-updates,jammy-updates 0.11.1-1ubuntu2 all [upgradable from: 0.11.1-1ubuntu1]
speech-dispatcher-audio-plugins/jammy-updates 0.11.1-1ubuntu2 amd64 [upgradable from: 0.11.1-1ubuntu1]
speech-dispatcher-espeak-ng/jammy-updates 0.11.1-1ubuntu2 amd64 [upgradable from: 0.11.1-1ubuntu1]
speech-dispatcher/jammy-updates 0.11.1-1ubuntu2 amd64 [upgradable from: 0.11.1-1ubuntu1]
systemd-oomd/jammy-updates 249.11-0ubuntu3.6 amd64 [upgradable from: 249.11-0ubuntu3.4]
systemd-sysv/jammy-updates 249.11-0ubuntu3.6 amd64 [upgradable from: 249.11-0ubuntu3.4]
systemd-timesyncd/jammy-updates 249.11-0ubuntu3.6 amd64 [upgradable from: 249.11-0ubuntu3.4]
systemd/jammy-updates 249.11-0ubuntu3.6 amd64 [upgradable from: 249.11-0ubuntu3.4]
udev/jammy-updates 249.11-0ubuntu3.6 amd64 [upgradable from: 249.11-0ubuntu3.4]

what do i need to do to get the 14 missing upgrades?



02

sudo apt upgrade

gives me this :

The following package was automatically installed and is no longer required:
systemd-hwe-hwdb
Use 'sudo apt autoremove' to remove it.
The following packages have been kept back:
libnss-systemd libpam-systemd libspeechd2 libsystemd0 libudev1 python3-speechd speech-dispatcher speech-dispatcher-audio-plugins
speech-dispatcher-espeak-ng systemd systemd-oomd systemd-sysv systemd-timesyncd udev
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.

sudo apt autoremove

removes the no longer required systemd-hwe-hwdb

but the software updater brings it back & this cycle goes on in loop.

what is going on?

help me out please.

---

### Post by &amp;KyT$0P# on 2022-09-28
01) Those are phased updates that your system has not yet been phased into.  You'll get them eventually when the phasing in is re-enabled.

02) Not sure, but I just wrote about that [here]("https://ubuntuforums.org/showthread.php?t=2478639&p=14113797&viewfull=1#post14113797").

---

### Post by ipv2 on 2022-09-28
01. seems a bit of an overkill where i am being informed about probable future upgrades.

02. does it qualify to be filed as a bug?

---

### Post by &amp;KyT$0P# on 2022-09-28
> **ipv2 said:**
> 02. does it qualify to be filed as a bug?

In this case, I would say it does qualify if you think it's a bug (and if you post the link to your bug report, I would mark it as affecting me too).

---

### Post by ipv2 on 2022-09-28
> **halogen2 said:**
> In this case, I would say it does qualify if you think it's a bug (and if you post the link to your bug report, I would mark it as affecting me too).

done :

[https://bugs.launchpad.net/ubuntu/+bug/1991139](https://bugs.launchpad.net/ubuntu/+bug/1991139)

---

### Post by ipv2 on 2022-09-28
> **halogen2 said:**
> 01) Those are phased updates that your system has not yet been phased into. You'll get them eventually when the phasing in is re-enabled.

am assuming that on my front i have no choice but to ignore the >14 packages can be upgraded< notification right?

---

### Post by &amp;KyT$0P# on 2022-09-28
> **ipv2 said:**
> am assuming that on my front i have no choice but to ignore the >14 packages can be upgraded< notification right?

No, you do have a choice.  But I'd recommend not taking it unless you specifically need the fix(es) in those updates.

If you do need those updates, you have two options:

1) For just a one-off, you can tell apt to ignore phasing of updates for an individual command.  I have an [alias]("https://ubuntuforums.org/showthread.php?t=2477612&p=14106533&viewfull=1#post14106533") for that.

2) To have apt ALWAYS install all available updates ignoring phasing, like it did in Ubuntu 20.04 and prior, [you can configure apt to restore this old behavior]("https://ubuntuforums.org/showthread.php?t=2479483&p=14113643&viewfull=1#post14113643").

---

### Post by ipv2 on 2022-09-28
> **halogen2 said:**
> If you do need those updates

i have no clue if i need them or not but i sure want to get rid of that nag.

> **halogen2 said:**
> 2) To have apt ALWAYS install all available updates ignoring phasing, like it did in Ubuntu 20.04 and prior

i took option #2 & no more nag.

update :

after applying the fix in option #2 my other grievance regarding systemd-hwe-hwdb no more persists.

sudo apt autoremove no more asks me to remove systemd-hwe-hwdb & it does not show up in software updater as an update any more.

```
APT {
Get {
Always-Include-Phased-Updates true;
}
}
```

the brackets in the code above are supposed to be as they are right? am asking because they do seem to be at random since i have no knowledge of coding whatsoever.

---

### Post by &amp;KyT$0P# on 2022-09-28
> **ipv2 said:**
> after applying the fix in option #2 my other grievance regarding systemd-hwe-hwdb no more persists.

Right, it would *work around* that because now on your system, [FONT=Courier New]systemd-hwe-hwdb[/FONT] is a dependency of a package you **actually do** have installed, so it should have been installed during the update and now not be auto-removable.

> the brackets in the code above are supposed to be as they are right?

Correct.

---

### Post by ipv2 on 2022-09-28
am gonna mark this thread solved & update my bug report on launchpad too.

thank you loads halo.

---

### Post by donald187 on 2022-09-28
Happening to me as well.  I just upvoted the bug.

EDIT:  Sorry.  I guess I shouldn't add to a solved thread.

---

