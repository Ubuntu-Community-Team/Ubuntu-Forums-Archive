---
title: "patition question"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by olympus112 on 2011-10-13
I want  bigger HD space how can I make mine larger? It says I have 209mb not the full 300 or so gigs i should.
Some is taken up by Windows and no idc to ever use it again. Haven't in months anyway.

---

### Post by oldfred on 2011-10-13
Is this a partition install or wubi file inside the windows NTFS partition.

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependancies

Folder sizes
sudo du -hc --max-depth=1

Partition sizes
df -Th | sort

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

# housekeeping.txt
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.

---

