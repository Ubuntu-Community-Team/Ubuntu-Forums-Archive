---
title: "I think xubuntu is taking up too much hdd space"
date: 2011-07-21
forum: Installation &amp; Upgrades
---

### Post by highnitro on 2011-07-21
hello all,

i just installed xubuntu 11.04 on my laptop and it works great and i really like, but.... just the install took up about 6GB which is alot more than i anticipated and more than what the site says it should take up. is there a way i can find out if i can remove some files to make more room, this doesnt seem right.

Thanks,
Matt

btw im a linux newb, but i do understand windows well, and have a bit of programming experiance.

---

### Post by oldfred on 2011-07-22
You can do the standard housekeeping. My install is a little over 7GB but I install lots of programs. That also does not count the data that you may have in /home.

# housekeeping.txt
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependancies

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

# also computer janitor in system-admin
# see grub cleanup to remove old linux versions or use synaptic
# empty trash
# remove log files only if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

# check sizes of 
cd /
sudo du -hc --max-depth=1

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

---

