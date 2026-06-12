---
title: "Help! My 10.04 suddenly freezes"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by melvskups on 2011-05-23
Good Day Everyone...

I am encountering this problem and haven't solved this yet... I was upgrading from 10.04 to 10.10, however during the installation process, it was not finished because the plug of my laptop was suddenly pulled out causing it to turn off and as I restart my computer and tried to load Ubuntu, It loaded but freezes on the log-in screen. no keyboard and mouse functions, and the hard disk do not show any activities.

Any ideas on this one? 

Thanks

---

### Post by oldfred on 2011-05-23
Welcome to the forums.

It may be half upgraded, so it is not in a working order. Can you boot to a command line or repair via the recovery mode in the grub menu? That would be the easiest solution. 

Otherwise you need the current liveCD of 10.10 and will have to chroot into your system and finish the updates. And exactly what to do may depend on how far it updated.

---

### Post by melvskups on 2011-05-24
I tried to run the recovery mode but at some point the process stops. I am not really sure whether that part really stops or it really takes sometime to continue.

---

### Post by oldfred on 2011-05-24
If you can get to command line run these, there may be a few more commands also to finish an upgrade as it may depend on whether is sees it as the new version or still as the old version.

#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

Edit:
What does this show, new version or old version as versions of software to download:
less /etc/apt/sources.list

---

### Post by melvskups on 2011-05-30
Will this commands work for the command line loaded by the Grub? It's the only thing I can go into... By the way, are there any available recovery tools for such problems? Thanks

---

### Post by oldfred on 2011-05-31
If all you get is a grub command line, you are not booting to a Ubuntu command line which would give you a login. The commands have to be run from a Ubuntu command line or chroot.

If you can boot grub, you may be able to get to the recovery mode and update from that. Or run commands from there.

You can try manual boot from the grub commands or use a liveCD and chroot into your install to run the commands.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

Manual boot and rescue mode:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode)

Chroot to repair grub2, also run other update commands while chrooted.
[https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT](https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT)

---

