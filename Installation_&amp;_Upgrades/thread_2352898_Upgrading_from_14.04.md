---
title: "Upgrading from 14.04"
date: 2017-02-16
forum: Installation &amp; Upgrades
---

### Post by Jason_Hunter on 2017-02-16
I'm trying to upgrade from 14.04 and I'm not able to. 

First of all, I'm trying to log the output I'm getting using this command:

sudo do-release-upgrade -d 2>&1|tee upgrade.log

This doesn't work; it logs just a few lines of basically nothing. 

I want to show you the error I'm getting, but I can't log it. 

I only have command line login to this box. 

Any pointers as to how I can proceed?

Thanks.

---

### Post by Impavidus on 2017-02-17
What's in your /etc/update-manager/release-upgrades file? Mine shows:```
# Default behavior for the release upgrader.

[DEFAULT]
# Default prompting behavior, valid options:
#
#  never  - Never check for a new release.
#  normal - Check to see if a new release is available.  If more than one new
#           release is found, the release upgrader will attempt to upgrade to
#           the release that immediately succeeds the currently-running
#           release.
#  lts    - Check to see if a new LTS release is available.  The upgrader
#           will attempt to upgrade to the first LTS release available after
#           the currently-running one.  Note that this option should not be
#           used if the currently-running release is not itself an LTS
#           release, since in that case the upgrader won't be able to
#           determine if a newer release is available.
Prompt=normal
```Make sure it's set to **Prompt=lts**

What are the lines of basically nothing? Maybe they contain anything useful.

The -d option of do-release-upgrade is to upgrade to the development release, which is 17.04. You want to upgrade to the next LTS release, 16.04.

---

### Post by RobGoss on 2017-02-17
I recommend making a complete backup and do a clean installation, in most case trying to upgrade within the system can cause problems 

I'm sure other people would agreed

---

### Post by Bucky Ball on 2017-02-17
Please use code tags and copy/paste commands when possible. It keeps the formatting and avoids confusion. Did you mean this?

```
sudo do-release-upgrade -d 2>&1|tee upgrade.log
```

Try this:

```
sudo do-release-upgrade -d 2>&1 | tee upgrade.log
```

And be aware of this excellent point:

[QUOTE=Impavidus]The -d option of do-release-upgrade is to upgrade to the development release, which is 17.04. You want to upgrade to the next LTS release, 16.04. [/QUOTE]

Good luck.

---

### Post by Jason_Hunter on 2017-02-17
It already says: [B]Prompt=lts

Also, I tried without -d and still the same issue. There are lots of 404 messages; it's not finding what it's looking for. 

How can I capture this output?[/B]

I've tried to clean out the /etc/apt/sources.list

I've also downloaded new apt and dpkg as it was complaining about that aswell, but still the same issue. It's pages of pages of 404 stuff.

do-release-upgrade starts a new shell, so that's probably why I can't capture the output the normal way, but I'm sure there is a way to do it.

---

### Post by Jason_Hunter on 2017-02-18
The method I used to clean up the sources.list file was this: 
[http://www.tuxgarage.com/2011/01/restore-your-sources-list-to-defaults.html](http://www.tuxgarage.com/2011/01/restore-your-sources-list-to-defaults.html)

---

