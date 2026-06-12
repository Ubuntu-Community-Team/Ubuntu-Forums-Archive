---
title: "Upgraded edgy -&gt; fiesty:  Now can't login"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by j3ff on 2007-04-23
Hello,

Synaptic informed me that I could upgrade to 7.04 so I pressed the button and went ahead with the upgrade.

The upgrade proceeded, seemingly to completion, but it did report the following problems:-

   * It failed to install avahi-autoip
   * It failed to install ubuntu-desktop citing dependancy problems.  

When the upgrade appeared to have finished I rebooted and GDM came up presenting me with a GUI login screen.  I entered my username, then password but it reported "Authorization failed".

I've booted into recovery mode and issued the following:-
    dpkg --configure -a
    apt-get -f install
    apt-get dist-upgrade
    apt-get install ubuntu-desktop

Each command indicated that the system was up to date.  No easy fixes there.

I tried su to my username (jeff) and got:-
```
pam_winbind[4706]: request failed, but PAM error 0!
pam_winbind[4706]: internal module error (retval = 3, user = `jeff')
su: Error in service module
```

So I suspect something is up with my winbind or PAM install or config but i don't know what.  I've tried 

apt-get install winbind

but apt reports that it too is up to date.

I would greatly appreciate some help.

Thanks,

Jeff

---

### Post by avb on 2007-04-23
try to read changelog of winbind. I think the config format is changed or maybe your network is not configured, so u cant access auth server.

---

### Post by j3ff on 2007-04-23
> **avb said:**
> try to read changelog of winbind. I think the config format is changed or maybe your network is not configured, so u cant access auth server.

The install samba/winbind version is 3.0.24.  On the Samba site, release notes for 3.0.25 indicate changes to idmap option syntax in smb.conf.  That's no help to me though as I'm using 3.0.24

My network is configured.  I can resolve names and run apt-get to fetch things from the repositories on the internet.  I don't think I have a network config problem, but I won' t let that stop me from checking things out if anyone has any suggestions.

Thanks avb, but still no joy.

---

### Post by zvacet on 2007-04-24
> It failed to install ubuntu-desktop citing dependancy problems

```
sudo aptitude install ubuntu-desktop
```

```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by j3ff on 2007-04-24
I've finally found why I couldn't login, but not before I hosed my system and started again with the fiesty live CD.  My computer is a domain member in a windows network.  I use winbind to authenticate windows users browsing shares on my computer.  I got this working in edgy by following the advice in this forum post:
[http://ubuntuforums.org/showthread.php?t=5409](http://ubuntuforums.org/showthread.php?t=5409)

Anyway, after reinstalling fiesty I was getting my domain authentication to work again when I found I could no longer log in.  I backed out of the changes I'd made to /etc/pam.d and then I could log in again.  A little more searching and I uncovered the following little nugget:

[http://ubuntuforums.org/showthread.php?p=2200998&highlight=winbind+pam#post2200998](http://ubuntuforums.org/showthread.php?p=2200998&highlight=winbind+pam#post2200998)

/etc/pam.d/common-account should read:

```
account sufficient pam_winbind.so
account required pam_unix.so
```

instead of what is suggested in the original howto.

I hope this is helpful to someone else.

Cheers,
Jeff

---

