---
title: "Fiesty upgrade blocked"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by dblbogey on 2007-05-29
I am running Edgy on machine coexisting with XP. When I recently tried to upgrade via the Upgrade Manger I received the following error message:

"Not enough free disk space.

The upgrade aborts now. Please free at least 412M of disk space on /var/cache/apt/archives. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean' "

I have done all the above, but I still get the same message. File browser says that I have 3G free space on hda1, but it also says that there is only approx. 260M of free space in the above-referenced '...../archive' subdirectory. There are currently 1 file and 1 folder in that subdirectory, but they are showing using 0 disk space.

I'm a relative newbie with Ubuntu, so please be specific about how to resolve this issue, and I'll really appreciate your patience.

---

### Post by aysiu on 2007-05-29
I'd install *filelight* and see exactly *where* all the space is being used.

If you're confident after that that you do have enough free space, file a bug report on the upgrade tool.

---

### Post by dblbogey on 2007-05-29
Thanks aysiu. I installed and ran Filelight. Near as I could tell from that there are 14 files in that subdirectory; it says the archive subdirectory is:  20.8 MiB (53%), Files: 14 (82%). Not quite sure what all that means.

BTW, the one file that File Browser shows in that subdirectory is "LOCK", but it shows no space being used, won't open to anything and can't be deleted/modified or unlocked. Don't know it that's relevant.

I'm still clueless as to how to resolve my problem, and I'll greatly appreciate any further ideas.

---

