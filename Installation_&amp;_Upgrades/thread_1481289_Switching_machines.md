---
title: "Switching machines"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by AdamMO on 2010-05-12
Hello,

I have recently ordered a new laptop, and would like to transfer my entire system over to it once it arrives.  I currently have a primary Ubuntu partition, as well as a small Windows partition.  I plan on replicating this partitioning on my new machine.

Now my question is this- is there any way to directly transfer all my Ubuntu installed programs, files, and settings over to the new machine?  Should I simply copy-and-paste the files, or will a fresh re-install be required, with manual installation for each application? Or, should I do a fresh only copy over some particular files?

Thanks for the help!

---

### Post by oldfred on 2010-05-12
Welcome to the forums.

Some like to copy -  I have not used these:
Make live CD or DVD
[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

Clonezilla

I prefer to do a clean install so system is up to date. copy all of /home into a new partition if you do not have a separate one. If you have any special system wide settings in /etc you may want to copy them. And you can export a list of all installed apps and reinstall:

from lovinglinux
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
dpkg --get-selections | grep -v deinstall > ubuntu-files
Then on new system:
sudo dpkg --set-selections < ubuntu-files
sudo apt-get -y update
sudo apt-get dselect-upgrade

I totally reinstalled ubuntu onto my portable from my desktop this way and it is a little more work than some of the automatic copies but I have a clean install and know it works. Part of why I installed Ubuntu on my portable was frustration with samba, so I converted to NFS and copied most of the data directly from the desktop to the portable.

---

### Post by AdamMO on 2010-05-12
Thanks for the tips.  That sounds like a solid plan!

I should have the new system Friday or Monday, so I will start preparing now.  Is it safe to run dpkg --get-selections | grep -v deinstall > ubuntu-files at this time, or will that deinstall things on my present machine?

Thanks again!

---

### Post by oldfred on 2010-05-12
No, that just creates a text files listing the program names. Of course if you add any between now and then they are missing. I did have a minor problem on my first use. I had used the same system for 3 years and not really housecleaned it. Packages that were totally obsolete did not get reinstalled. I went back into synaptic and I had pages of stuff that was old. But I did install some older packages that I really did not need or want anymore. 

Another way to list (I do not think this can be used for reimporting) and it shows the titles.
List with explanations of programs
```
dpkg -l > ~/Desktop/installed_programs.txt
```I install some apps before running the update. see attachment for my current version. Edit & use at your own risk.

---

### Post by AdamMO on 2010-05-12
Sounds good!  I recently upgraded to 10.04 from 9.10, so my installed packages shouldn't contain any redundancies.  I'll post how everything goes later on :)

---

