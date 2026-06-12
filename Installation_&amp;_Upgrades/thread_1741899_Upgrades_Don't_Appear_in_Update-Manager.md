---
title: "Upgrades Don't Appear in Update-Manager"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by lelantus on 2011-04-28
I know 11.04 is available for download at the moment, but it isn't showing up in Update-Manager.

I would just put it on a disk and install it that way, but I'm running 10.04 in Wubi.

Update-Manager is currently set to receive all 'normal' releases.

Help?

---

### Post by plucky on 2011-04-28
> **lelantus said:**
> I know 11.04 is available for download at the moment, but it isn't showing up in Update-Manager.

I would just put it on a disk and install it that way, but I'm running 10.04 in Wubi.

Update-Manager is currently set to receive all 'normal' releases.

Help?

You do realise that to upgrade to 11.04 you would have to also upgrade to 10.10 first?

It also depends on when your local server gets updated to the latest release before update-manager offers the distribution upgrade.

Good Luck

---

### Post by lelantus on 2011-04-28
Yes, but the fact remains that Update-Manager is showing *no *upgrades available, including 10.10.

---

### Post by StrayEddy on 2011-04-28
You can use the command:
 
sudo do-release-upgrade
 
It will open the upgrade manager

---

### Post by lelantus on 2011-04-28
Fantastic! That seems to have done it.

Thanks for the tip!

---

### Post by bcbc on 2011-04-28
You'd better check the wubi megathread: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

The upgrade to 11.04 will be fine, but upgrading 10.04 to 10.10 on Wubi has problems.

If you install a LTS release (which 10.04 is) then it is set by default to only prompt for upgrades to another LTS (next one will be 12.04). So you have to open Update manager, click Settings, and change it to prompt for all new releases.

---

### Post by lelantus on 2011-04-29
Updated from 10.04 to 10.10 and 10.10 to 11.04 seamlessly using the terminal command suggested by StrayEddy.

Thanks for the help!

---

