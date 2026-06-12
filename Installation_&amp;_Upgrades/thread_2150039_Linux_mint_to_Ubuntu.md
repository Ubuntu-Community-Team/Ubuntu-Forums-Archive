---
title: "Linux mint to Ubuntu?"
date: 2013-05-30
forum: Installation &amp; Upgrades
---

### Post by frap129 on 2013-05-30
Hello, I'm currently running Linux mint 14 and i want to switch to Ubuntu 13.04, but i don't want to loose all my programs and data. is there a backup tool that could be used cross-distro? i know that mint is Ubuntu based, so it should work. What backup tools do you recommend?

---

### Post by presence1960 on 2013-05-30
your individual software must be reinstalled after installing Ubuntu.

---

### Post by rewyllys on 2013-05-31
> **frap129 said:**
> Hello, I'm currently running Linux mint 14 and i want to switch to Ubuntu 13.04, but i don't want to lose all my programs and data. is there a backup tool that could be used cross-distro? i know that mint is Ubuntu based, so it should work. What backup tools do you recommend?
For backing up, I've found LuckyBackup reliable and easy to use; it's available via the Synaptic Package Manager or the Software Center.  Once you've installed LuckyBackup, use it to back up your home directory onto whatever storage means you want to use (other than the partition on which your current LinuxMint system is installed). 

As Presence1960 has noted, your software programs will need to be reinstalled after you install Ubuntu.  However, your personal data files for each program you use should be picked up by that program as it's reinstalled under Ubuntu.

Since you're making a major change anyway, I strongly recommend that you set up a separate partition to hold your /home directory.  After you've installed Ubuntu, install LuckyBackup, and tell it to re-install, on that new separate partition, the /home directory that you had saved elsewhere prior to replacing LinuxMint by Ubuntu.

---

### Post by fantab on 2013-05-31
> **frap129 said:**
> Hello, I'm currently running Linux mint 14 and i want to switch to Ubuntu 13.04, but i don't want to loose all my programs and data. is there a backup tool that could be used cross-distro? i know that mint is Ubuntu based, so it should work. What backup tools do you recommend?

Programs have to be reinstalled. You can back up your data though. There are several back up tools for linux. CLI is also an easy way to backup: [http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup). 

Another solution is to NOT use your /home when installing Ubuntu, I mean install Ubuntu to '/' partition only. Do not use or Format /home partition. Later you can reuse the previous /home as DATA partition, remove all the dotfiles and dotfolders and you are good to go.

---

### Post by frap129 on 2013-05-31
So im confused. Do i have to reinstall my programs because im switching disros or because there is not a backup tool that supports it?

---

### Post by tgalati4 on 2013-05-31
Both.  Each software package has custom configuration files stored in your home directory.  There are enough differences between Mint and Ubuntu to make reusing the configuration files problematic.  Besides Mint 14 is based on 12.10 and you want to move to 13.04.  That alone will cause breakage.  So you can wait for Mint 15 to come out and try an in-place upgrade (and expect some breakage), or backup your personal data and do a fresh install of Ubuntu 13.04.  You can make a list of packages installed currently:

Open a terminal:

```
dpkg --list
dkpg --list > listofcurrentlyinstalledpackagesonmysystem.txt
```

---

### Post by rewyllys on 2013-06-01
> **tgalati4 said:**
> . . . . So you can wait for Mint 15 to come out and try an in-place upgrade (and expect some breakage), or backup your personal data and do a fresh install of Ubuntu 13.04. . . . ]
Linux Mint 15 was released on May 29.

---

