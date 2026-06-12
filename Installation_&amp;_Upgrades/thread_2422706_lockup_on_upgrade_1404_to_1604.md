---
title: "lockup on upgrade 1404 to 1604"
date: 2019-07-11
forum: Installation &amp; Upgrades
---

### Post by bdubawoop on 2019-07-11
I had 1404lts on my laptop & desktop.
The laptop offered to upgrade to 1604 & it went successfully.
the desktop did not offer so I googled & found 'sudo do-release-upgrade' which seemed to work. It d/l & installed stuff for ~1/2 hour, then it locked up installing fonts. Had to do hard reboot & it came up to 1604 command line & errored out whe I tried 'startx'.
I'm now back to (restored) 1404lts.
any other options for upgrading without doing a clean install?
By the way, in the middle of the upgrade the window popped up offering to upgrade to 1804lts. I told it to ask again later.
-------------------------
I got the updater to prompt for 1604. 
Tried it again twice, once with bu from 2 weeks ago & again with bu from sep 2018. It always freezes in the same spot, about 1/2 way thru installing.
I see frirefox-flashplugin-a bunch of fonts then a hard freeze.

---

### Post by mastablasta on 2019-07-12
backup and clean install.

separate home from root if you still can and if it is feasible.

---

### Post by Impavidus on 2019-07-12
It should have offered that upgrade about 3 years ago. Best to upgrade before the old version reaches end of life. So, yes, backup and fresh install. And when you're at it, consider jumping directly to 18.04.

---

### Post by rsteinmetz70112 on 2019-07-12
Most likely when the release upgrade failed to complete you were left with a partially upgraded system. If you can still boot to 16.04 you might try running a few commands to fix the failed upgrade.

```
# sudo dpkg --configure -a
# sudo apt install -f
# sudo apt update 
# sudo apt upgrade
```

If this works it is still likely some packages will need repair.

---

### Post by bdubawoop on 2019-07-12
well, i'm amazed. It appears I actually managed to get to 1604 with all my settings intact.
I was left with only a terminal & startx produced errors, partial install as rsteinmetz suggested, so rebooted to another system & googled & found basically what rsteinmetz70112 suggested (are you a columbo fan?), dpkg..., etc. This ran 20 min (with a lot of error messeges). Then did apt-get update-reboot-again to terminal,no desktop. ran startx & came up with bare desktop, no apps. back to terminal-reboot-this time came up in desktop & offered updates-did that-rebooted & it came up normally! There may have been a few more reboots in there, I don't recall, my head is spinning.
What a hassle.
I also have debian jessie on another partition & recently ran the debian upgrade process to go to stretch & it went smooth as silk.
I dread going from 1604 yo 1804 but theres always backup/restore to fall back on.
I'd mark it as solved but given the goat---- I had to go thru, I don't think so. Not sure what happened.

---

### Post by rsteinmetz70112 on 2019-07-15
Glad I could help.

As you can see a lot of people recommend a clean install and for a pure desktop system that is probably best. However if you use a server, have much local configuration or non-standard software a clean install will wipe out the local configuration and you have to do it all over again, even finding some of the configuration files can be challenging. Upgrades work best if you do it to the next release, but then you have to do it often. Upgrades between LTS versions usually have some minor issues, particularly related to desktop and video drivers.

All of that said, I suggest you immediately upgrade to 18.04 LTS. 16.04 LTS will be EOL relatively soon but 18.04 still has a long time to go. You probably don't want to wait until 16.04 is unavailable to upgrade. I've just recently completed upgrading all of my systems (except one) to 18.04 LTS.

---

### Post by mastablasta on 2019-07-16
> **bdubawoop said:**
> 
What a hassle.


due to an unresolved bug in Kubuntu i didn't even get that far. not even overwriting the current install with new version worked. i had to reformat the partition. it was in the end faster to just reinstall (and upgrade to 64bit while at it). had i used a separate home the reinstall would go fast (30-40 min), the settings would be preserved.

the stupid part - i didn't make a separate home on the new install... ](*,)

---

