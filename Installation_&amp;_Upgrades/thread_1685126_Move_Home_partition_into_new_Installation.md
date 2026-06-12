---
title: "Move Home partition into new Installation"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by gurudev1000 on 2011-02-10
Yea, the title might look like the question has been asked a million times, but I have a little different problem which I couldn't find elsewhere.

I have a 500GB SATA in which 64GB is used as the main Ubuntu installation mounted at '/' with no separate home partition like how they recommend.

I just got a 1TB SATA in which I have an EXT4 formatter 66GB partition into which I want to have a proper clone of the 500GB installation. I followed the instructions on [http://askubuntu.com/questions/20460/move-installation-to-new-disk](http://askubuntu.com/questions/20460/move-installation-to-new-disk) that 'dv3500ea' gave and it didn't work. I spent hours trying multiple times and finally got frustrated.

1- So, now I am thinking, I can do a fresh normal install of Ubuntu into the 1TB partition, but perhaps there could be a way of moving the 'HOME' folder from the old partition into a second partition on the new HDD and mount it as the '/home' folder of the new installation? I hope I am not too confusing. I want to have a separate home folder because I realise after reading around that all my customisations are better kept safe in a separate home folder.

2- Also I want to know a way of keep the softwares from the old installation in the new installation without having to download all of them again. If a simple copy paste would work, I wonder how their shortcuts would appear in the 'Applications' menu like how they do when you do a proper install through the Software Centre.

On that note, I am curious - since Ubuntu 11.04 seems to have a totally different look with Unity, will the settings in a separate '/home' folder screw up what the fresh installation is supposed to look like?

Hoping for your help.
/thanks :P

---

### Post by zvacet on 2011-02-10
For making separate home read [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) .

To keep software you installed with apt,synaptic,deb packages you can use **aptoncd**.You can install it from synaptic and on [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) you can see how it works.

---

### Post by gurudev1000 on 2011-02-10
> **zvacet said:**
> For making separate home read [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) .

To keep software you installed with apt,synaptic,deb packages you can use **aptoncd**.You can install it from synaptic and on [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) you can see how it works.

Thanks for your help. I wil read about them.. but those with CD solutions, any way of simply making images or trying them on USB? I don't like CDs.

---

### Post by oldfred on 2011-02-10
If you install a different version of Ubuntu, you have to download the newer versions of the software. 

You can make a list of all installed apps:
But this will require new download:
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

Location of downloaded debs
/var/cache/apt/archives/

Since Ubuntu is designed to be upgraded, all the old settings will work in the new. Some just may be obsolete. But you may not be able to go back as new settings may confuse an old install. Backups are important.

Another thought. I prefer to install Ubuntu on every drive, but have different versions. I keep my old install, my current install and the beta of the new install rotating around on different drives. I let each keep their own /home in / and only copy some settings from the hidden files & folders. I then have all my data in a separate /data partition that I mount in each install so I can use any install, but have access to my data files. My /home then is only about 1GB which is mostly .wine (that I have not yet moved to /data).

---

### Post by grahammechanical on 2011-02-10
I first installed Ubuntu with a /home folder on a partition mounted as /. Then, when I was feeling clever, I created a second partition which I mounted as /home but then Ubuntu would not boot. The OS was expecting a /home folder on the same partition as the OS. It did not know that all the user files were in the /home folder on the /home partition.

Back up all the data that you want to keep. Copy the folders in the /home folder. You will need to set View Hidden files. You will need to re-install Ubuntu and tell it about the /home partition. And then repopulate the folders in the /home partition with your data. Best to try this when upgrading to 11.04

Regards.

---

### Post by zvacet on 2011-02-10
@ **grahammechanical**

> I first installed Ubuntu with a /home folder on a partition mounted as /. Then, when I was feeling clever, I created a second partition which I mounted as /home but then Ubuntu would not boot. The OS was expecting a /home folder on the same partition as the OS. It did not know that all the user files were in the /home folder on the /home partition.

There is easy way to deal with that.Boot your live CD and mark your root as root / **but do not format it**!After that make new partition mark it as home /home **and format it as ext4.** Ubuntu will recognize new partition!

---

