---
title: "Need to trim installation size... recommendations?"
date: 2010-08-14
forum: Installation &amp; Upgrades
---

### Post by redvenomweb on 2010-08-14
I recently used remastersys to create a custom 10.04 installation, and it works great.  However, the custom installation ISO is slightly over 1GB (about 50 MB too large).  I'd really like to trim it down to 1GB, as I have a bunch of unused 1GB USB flash drives that I could use as installation media, and it would be a lot cheaper than going out and buying new 2GB flash drives.

Right now, I have the plain desktop default installation.  What are some potentially good candidates for packages (preferably big ones) that I can remove?  I'm also open to replacing some heavy-duty packages with some more streamlined, lighter-footprint packages.

P.S. I've already run apt-get autoremove, but that didn't produce the space I needed.

---

### Post by clrg on 2010-08-15
Mono

---

### Post by kerry_s on 2010-08-15
1gb flash will be less, you'll need to get under 1gb.

---

### Post by oldfred on 2010-08-15
Flash drives are down to about $2 per GB. You may not be happy without everything.

Installed app size, but does not sum dependancies.
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes dependencies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependencies

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

I think Autoclean just cleans up files you don't need, while autoremove deletes unneded files..
Autoclean cleans up the downloaded archives (.gz or .tar) files used to install things. Autoremove cleans libraries that are no longer needed.
you can run any "apt-get" command predeccesed by the "-s" (simulate) switch

 How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

Openoffice & firefox are two larger apps. Did you add in any k apps. I like k3b but then that pulls in lots of kubuntu.

---

### Post by redvenomweb on 2010-08-16
OK, thanks for your responses.  I'll see what I can do with the information given.

---

