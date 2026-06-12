---
title: "Upgrade Karmic to Lucid ending up having Maverick in update Manager"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by ypestis on 2010-07-02
Hello I did an manual terminal command upgrade from Ubuntu Karmic 9.10 installed as WUBI next to main Windows XP to Ubuntu Lucid 10.04 and now when I look in the Update Manager Ubuntu Maverick is added...

When I run bootinfo script it also detects my operating system as Ubuntu Maverick Development Branch but my System -> About Ubuntu says you are using Ubuntu Lucid..

Before upgrading I remember wanting to get Ktorrent 4.0 to run so I googled it and I checked my shell what I did and I came up with these commands having to do with my repository:
sudo apt-add-repository ppa:blca/published
sudo add-apt-repository ppa:user/kubuntu-ppa/ppa

This didn't work and I removed the kubuntu ppa's but can't remember doing something with blca/publised

Now the way I have upgraded is following:

sudo aptitude update
sudo aptitude safe-upgrade
sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade

After this I was already in Lucid but the tutorial I checked on the internet to do the update said I had to do these commands as well (and I suspect this is what caused the maverick trouble)

sudo aptitude install update-manager-core
sudo do-release-upgrade -d

Now apart from having Maverick in the update manager I also cannot boot my system normally from Grub anymore wich may have to do with this problem so I would like to revert this back if possible..

Any help more then welcome!

---

### Post by bcbc on 2010-07-02
Unless you backed up your root.disk file you cannot revert back to 9.10.

If you installed wubi from Karmic 9.10, note you have to replace your wubildr file as the one with the release has a bug. [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

This might get you booting again. However you'll still be in Maverick which has just gone to alpha2. But if you refrain from running any more updates, or keep backing up the root.disk (under c:\ubuntu\disks folder - assuming installed to c: ) then you have a way to recover your system.

Finally, you could just backup the root.disk outside of the c:\ubuntu folder, and reinstall. Then you can mount and copy over data from the backed up root.disk.

---

### Post by ypestis on 2010-07-02
yeah I ended up doing that cause I can't boot anymore cause of corrupted root.disk I think...
Back to Karmic 9.10 now...
Thanks for the information!

---

