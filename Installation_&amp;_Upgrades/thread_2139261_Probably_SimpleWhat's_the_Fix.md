---
title: "Probably Simple/What's the Fix?"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by vcell on 2013-04-26
Working from 12.10, I've tried upgrading to 13.04 from the command line and from the Ubuntu Software Updater.

From the command line I entered **sudo apt-get update && sudo apt-get dist-upgrade**. After it completed I typed **sudo update-manager -d**. The latter of course just opens the Ubuntu Software Updater, which I could just as easily do from Dash, which I also did. 

Nonetheless, after the updater looked up the updates, I get the following message:[INDENT][I]Failed to download repository information

Check your Internet connection.[/I]

[/INDENT]
In the details it says:[INDENT][I]W:Failed to fetch [http://ppa.launchpad.net/cooperjona/stormcloud/ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/cooperjona/stormcloud/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.[/I]
[/INDENT]

Is there something more I need to download and install. I've never had this issue upgrading before?

--VCell

---

### Post by grahammechanical on 2013-04-26
Remove that PPA. That Personal Package Archive has not been updated to the Raring repositories.

We should remember that the upgrade process is designed to work on upgrading one default Ubuntu installation to another default Ubuntu installation. It cannot account for all the variations that users make to their systems. It is always base to revert to a default installation.

Regards.

---

### Post by JRV on 2013-04-26
You need to disable the PPA before doing the upgrade.

Open (Install if neccessary) synaptic.

Click Settings=>Software Sources=Other Software

Uncheck the offending PPA.

Aftre installaion you can try to activate the PPA again, the maintainer may or may not have updated for 13.04 yet.

---

### Post by vcell on 2013-04-26
Thanks everyone. You were correct, it was a PPA that as far as I know I don't need. I opened the Synaptic Package Manager. Then went to Settings > Repositories > Other Software (Tab). From there I just unchecked the culprit. Running the upgrade to 13.04 went flawlessly after that.

I appreciate the fast responses and all the help. Excellent.

---

