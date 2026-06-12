---
title: "Upgrading 7.10 to 10.10"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by neepster on 2010-10-12
All,

I have a server that has been merrily running Gutsy 7.10 for about 2.5 or 3 years.  It runs a RAID 5 array and is my home backup server, etc.  Recently one of the drives died and I had to rebuild the array (which worked - thank you RAID!!!), but since it was the boot drive that died, I am currently running a slightly older kernel that I had on one of the other drives.  Long story short, I am thinking about upgrading to the latest and greatest 10.10, but it looks like to do that I will have to upgrade 7.10 to 8.04 then 8.04 to 8.10 then 8.10 to 9.04 and then 9.04 to 9.10 and then 9.10 to 10.04, etc., etc., etc....

Seems like a long way to go.  Any recommendation on what to do?  Should I do that or just try to completely reinstall a fresh 10.10?  My only concern there is that I am not sure what that will do to my RAID array.  Thoughts?

---

### Post by DougieFresh4U on 2010-10-12
Don't know how 'server' installs work.
That being said, can't it be done by going to 8.04 LTS and then  to 10.4 LTS?

---

### Post by neepster on 2010-10-13
After further looking, I think I can go from LTS to LTS, so from 7.10 to 8.04 to 9.04 to 10.04... but I don't think I can jump from 8.04 to 10.04 or 10.10 in one upgrade.

Maybe someone else can confirm this?

At this point I am leaning to just reinstalling or trying to 'upgrade' with the 10.10 Server LiveCD

---

### Post by DougieFresh4U on 2010-10-13
according to [this]("https://wiki.ubuntu.com/LTS"), 8.04 and 10.04 are the only recent LTS, so yes you can go from 8.04 to 10.04

---

### Post by hecatae on 2010-10-13
you are looking at:

```
sudo do-release-upgrade
```

to upgrade to 8.04

then

[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

> Ensure you're up to date with latest release:

```
sudo apt-get update
```
```
sudo apt-get upgrade
```
Install update-manager-core if it is not already installed:

[QUOTE]sudo apt-get install update-manager-core
edit /etc/update-manager/release-upgrades and set Prompt=lts

Launch the upgrade tool:

> sudo do-release-upgrade
Follow the on-screen instructions.
At the end of the upgrade process you will be required to restart the server in order to boot into the new kernel. If you do not have access to the console of the system you are upgrading, you may need to edit /boot/grub/menu.lst and change the default boot kernel to the newly installed 10.04 kernel. If this step is not performed your server may attempt to boot into the 8.04 LTS kernel and will hang.[/QUOTE]

should be simple

---

