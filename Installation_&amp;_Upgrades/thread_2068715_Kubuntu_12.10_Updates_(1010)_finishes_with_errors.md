---
title: "Kubuntu 12.10 Updates (10/10) finishes with errors"
date: 2012-10-09
forum: Installation &amp; Upgrades
---

### Post by bra|10n on 2012-10-09
Applying today's system-updates via CLI, the process completes with errors that both *flashplugin-installer* and *update-notifier-common* failed to install. 
Re-running the recommended **dist-upgrade** command allows for these packages to finally install.
The benefit of applying updates via the CLI is obvious.

Posting here mainly for the benefit of early adopters of Kubuntu 12.10, but wise for users of regular Ubuntu users to keep a watchful eye also.

---

### Post by jeppebundsgaard on 2012-10-09
That didn't quite do it for me. But the following combination of what I had been trying and your suggestion did:
```

sudo apt-get remove flashplugin-installer
sudo apt-get remove update-notifier-common
sudo apt-get dist-upgrade
sudo apt-get install flashplugin-installer

```

---

### Post by bra|10n on 2012-10-09
@jeppebundsgaar,
Then respectfully , I suggest that you began the update process with an already broken installation of flash on your system. 
It might be helpful to others if you indicated whether or not you have Kubuntu installed, (or Ubuntu with Kubuntu-desktop).

If you haven't already, you might want to reinstall update-notifier-common also.

---

### Post by bra|10n on 2012-10-09
Update: It appears that *flashplugin-installer* is failing to correctly identify the flash version already installed and simply reinstalls flash again.

---

### Post by vasa1 on 2012-10-09
I saw a similar thing with Lubuntu 12.10 updates. I got a screen indicating that the flash bit didn't happen and prompting me to retry which I did and all is good now for now.
So I guess that error may not be Kubuntu-specific.

---

