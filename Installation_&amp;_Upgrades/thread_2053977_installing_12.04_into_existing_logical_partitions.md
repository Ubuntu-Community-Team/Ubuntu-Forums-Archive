---
title: "installing 12.04 into existing logical partitions"
date: 2012-09-06
forum: Installation &amp; Upgrades
---

### Post by rawlins02 on 2012-09-06
I'm preparing to install Precise on a machine currently running 9.10 in a dual boot setup. /dev/sda1 has the Windoze install, and there are 4 logical partitions in the extended linux partition. I have swap, /home, /usr, and root, which has over 5GB of available space. 

```

>df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              11G  4.9G  5.7G  47% /
udev                 1007M  272K 1006M   1% /dev
none                 1007M  212K 1006M   1% /dev/shm
none                 1007M  120K 1007M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/dev/sda6              97G   65G   28G  71% /home
/dev/sda7             9.2G  4.4G  4.4G  51% /usr

```

So how best to install in this setup?

I'd like to install the new distro into / while temporarily keeping the existing distro in place. Then be able to expand and/or rename partition(s) so new distro ends up in a single root directory. Should I be able to shrink the current / and create a new logical partition for new distro? In this case, what about /usr?  I have /home backed up and can repopulate if needed. But maybe it just stays?

An install on reformatted linux partitions my fallback option.

---

### Post by grahammechanical on 2012-09-06
First, a warning. If 9:10 is in sda5 and you install Precise into sda5 then you will lose 9:10.

Second, there are different opinions on partitioning. Some would say that you do not need a /usr partition.

I boot into 12.04 (mounted as /) with its own /home partition. I do not have a separate /usr partition. I also have at the moment two 12.10 installs each in their own partitions with a /home folder (not a partition). I can access the /home partition and work on my documents in that partition. This way if either of the 12.10 installs break and need re-installing I do not loose any data. The same appplies to my 12.04 install. The data is safe in /home partition.

My suggestion is this:

1) Install 12.04 in a separate partition and test it out.

2) If you decide to get rid of 9:10 and keep 12.04 backup all your data in the /home partition.

3) Install 12.04 in sda5 and make sda6 as its /home partition but format both partitions during the install. Otherwise you will have configuration files from 9:10 in your /home folder on the /home partition on sda5. Start 12.04 from a clean install. Not only will these take up space in that partition but may conflict with the new OS.

4) Then copy your backed up data back into the relevant folders in /home.

It is possible to expand the partition that you put 12.04 in but it will not be attached to the /home partition (sda6). It is easier to attach an existing /home partition during the install of 12.04 rather than afterwards.

The alternative would be to try and do progressive distribution upgrades from 9.10 to 10.04 to 10.10 to 11.04 to 11.10 to 12.04. But that is not only a lot of downloading but it increase the risk of a broken OS at the end. The libraries underlying to OS have completely changed since 11.10. Not Gnome 2 any more but Gnome 3 and other changes to.

Regards.

---

### Post by rawlins02 on 2012-09-06
Appreciate the suggestions. 

Is it possible for me to create another partition (for 12.04) from the existing disk partitions?  This way I keep the current OS in /dev/sda5. For example, I'm thinking of using GParted to create, say, /dev/sda9 from some of the space allocated to root. Then I'd nstall 12.04 into that new /dev/sda9 partition. Would this work?

---

### Post by oldfred on 2012-09-06
If you have room you can create sda9. I normally install to 25GB with all system folders & /home as a folder. But I have all data including some hidden folders like Firefox & Thunderbird in separate data partitions. I normally use about 7 to 9GB of my 25GB.

You can export a list of installed applications. But with as much change as you are doing you may reinstall a lot of older applications. I will not install if totally obsolete. I found I was still installing python2.5 when it is 2.7 now. Also OpenOffice is not LibreOffice and you do not need both.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

### Post by rawlins02 on 2012-09-06
OK, so it's possible for me to create another logical partition for new install.  Looking at my current setup, root has only 5GB of available space. Might not be large enough. Then there's the space currently allocated to /home. Assume I would carve out new space there.

But now I think it would be best to reformat the linux partitions and install like I did before, into /, without keeping current distro.  

Yes, I have saved a list of installed packages. Like you, I'm not sure I want to install all of them automagically. I'll likely recreate another list with only some of the current packages.

Marking this thread solved.

---

