---
title: "Separate 'home' partition?"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bwallum on 2010-03-22
I had a separate hard drive for home on Karmic. I have tried to do the same with Lucid and get a system configuration error. I read somewhere that maybe home will be installed on a separate partition with Lucid.

Will home be installed on a separate partition in Lucid?

Can I, using Lucid, connect my (ex karmic) home that resides on a separate hard drive?

---

### Post by cariboo on 2010-03-22
I have all my system set up with a separate home partition, during the installation, you should select manual partitioning, and setup your partitions the way you like. Setup the home partition to mount as /home, and make sure you don't format it if you want to use the information already on it.

---

### Post by bwallum on 2010-03-22
> **cariboo907 said:**
> I have all my system set up with a separate home partition, during the installation.....

How about if I have set up Lucid already and loaded all my non default apps. Can I still link to the home hard drive?

I have labelled the home hard drive as HomeHD. I have put the following line in /etc/fstab```
LABEL=HomeHD	/home	ext3	relatime	0	2
```

I get a system config error and then get the Desktop appear without the top and bottom panels.

---

### Post by miegiel on 2010-03-22
> **bwallum said:**
> How about if I have set up Lucid already and loaded all my non default apps. Can I still link to the home hard drive?

I have labelled the home hard drive as HomeHD. I have put the following line in /etc/fstab```
LABEL=HomeHD	/home	ext3	relatime	0	2
```

I get a system config error and then get the Desktop appear without the top and bottom panels.

But your */home* does mount propperly, right?

It sounds like you have some old leftover configuration files in your home dir that are causing trouble. I think that stuff is all in the hidden *.gconf* dir in your home dir. If you move/rename *.gconf* (or backup and remove it) a new *.gconf* will be created with default settings the next time you start ubuntu.

I'm not 100% sure about the dir name, so verify that ;) In any case you can just put the backup back.

---

### Post by HoboJ on 2010-03-22
I've always wondered this. If you're /home is on a separate partition and you reinstall ubuntu wouldn't the existing system configuration files in /home conflict with the new ones?

---

### Post by bwallum on 2010-03-22
> **HoboJ said:**
> I've always wondered this. If you're /home is on a separate partition and you reinstall ubuntu wouldn't the existing system configuration files in /home conflict with the new ones?

I guess that is what is going on. I set my Desktop background on my HomeHD drive to be different so I know that I am accessing the 'HomeHD' home directory fine. The problem is with some configuration files. The gconf file(s) as suggested above might be the issue. I have tried to copy over .gconf using gksudo nautilus and it appeared to copy over ok. I use the same username and password for sudo on both the system default drive and HomeHD.

Currently the Desktop background appears, a usb drive appears as expected on the Desktop but I have no top and bottom panels. I can use Alt F2 to bring up a terminal and this allows me to # out the fstab line and reboot back into Lucid with the default home on the system drive.

??

---

### Post by miegiel on 2010-03-22
I just wanted to add: The best way to avoid problems like this is to select what partition you want to use for */home* in the manual partition-setup section when installing ubuntu.

> **HoboJ said:**
> I've always wondered this. If you're /home is on a separate partition and you reinstall ubuntu wouldn't the existing system configuration files in /home conflict with the new ones?

Sometimes there is a conflict, but normally it saves a lot of time configuring your GUI and apps.

---

### Post by seeker5528 on 2010-03-22
> **HoboJ said:**
> I've always wondered this. If you're /home is on a separate partition and you reinstall ubuntu wouldn't the existing system configuration files in /home conflict with the new ones?

It's not always the case, but usually the installed software will recognize older configuration files and update/migrate the configuration files and data bases.

If there are incompatibilities with configuration files and/or databases, it's not that common to support going backwards. If you do share the same home directory with multiple installations that use different versions of the same software, then the older software may have trouble with the newer configurations and databases and if they write to these things that have been updated by a newer version of software, they may mess things up for the newer software as well.

It's not a solution I'm particularly fond of, but if you use different user names in each installation, that would be one way to use the same /home partition with multiple installations without the conflicts.

If have an old /home directory that you want to use and it didn't get set up during the installation you can chown the files:

```
sudo chown UID:GID -R /media/XXXX/username
```

'UID:GID' should be your user and group name in the current install 'XXXX' the mount point for the /home parition and 'username' the user name you used in the previous install.

From there you can install mountmanager then use it to set up where the partition gets mounted, or edit fstab.

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Note that the fsck option (the last column) should only be '1' for the root file system, '2' for any other file systems that should be periodically checked during boot up and '0' for file systems you don't want checked (typically NTFS and maybe FAT), so for your home partition this would typically be a '2'.

Later, Seeker

---

### Post by bwallum on 2010-03-23
Got there in the end....

To recap, my separate home folder is on a dedicated hard drive labelled HomeHD. What I did was:- 

1) Make sure that the default home (on same drive and in same partition as the system files - that in itself is not good imho) was populated with all my HomeHD data folders (Documents, Desktop etc). Some dot files can be very important, (ctrl h shows these hidden files). The .evolution file contains all past emails and contacts for example and should be copied to the default home. I used the same username and authentication password on both old and new installations. You may have to 'chown' your files if they differ. I also used gksudo nautilus to move root owned dot files around and step 4 below to make them accessible. 

2) Reboot and test your copied over 'system' home. When running ok then copy all the /home/USER/ files back to the HomeHD/USER/ folder. I did this to avoid (hopefully) any compatibility issues re Karmic to Lucid.

3) Delete HomeHD/USER/.gconf folder and the .ICEauthority file. This will give you a default Desktop and gnome installation. When running evolution you will be asked to set up your email account. I did this and found that my ex Karmic email and contacts came through ok.

4) Make sure you own /HomeHD/USER/ with```
sudo chown -R USER:GROUP /media/HomeHD/USER
```You need this if you see padlocks everywhere on your folders.

5) Insert a line into the /etc/fstab file```
LABEL=HomeHD	/home	ext3	relatime	0	2
```

6) Reboot

7) When running check for broken dependencies and run ```
sudo apt-get upgrade
``` to tidy up.

That should do it. If it doesn't work, to recover put a # in front of the new fstab line and you should get back to the system default home folder. If you get to the HomeHD Desktop but without panels you may be able to get a terminal up with Alt F2 and then edit the fstab file with ```
gksudo gedit /etc/fstab
```During my 'experiments' I did have to resort to editing fstab with a live cd at one stage so best to have a good one ready.

What I would like to see is true separation of system from personal data files. The dot files in the home folder screw up what should be a seamless migration data wise. Other distros (SUSE for one) appear to have achieved this from some comments in postings that I have seen. It would be great if Ubuntu could achieve this. 

Thanks all for piecing it together for me.

...and it might be easier to configure /home when installing Lucid as miegiel suggested above.

---

### Post by leorolla on 2010-04-09
> **HoboJ said:**
> I've always wondered this. If you're /home is on a separate partition and you reinstall ubuntu wouldn't the existing system configuration files in /home conflict with the new ones?

There should be no system configuration file in the home folder.
System configuration files are stored in system folders.

What you have in your directory are user configuration files.

There should be no serious problems about it.

Upgrading from Karmic to Lucid is just upgrading a lot of programs in this sense, and it is not a catastrophe if Program 2.1 finds the user configuration files of Program 1.9.

The only problem I had is that with the severe change in the gnome theme my windows looked ugly with Lucid, but a drastic solution is to just remove a few .gnome* and .gconf* in your folder.

Even Thunderbird 3 could read reasonably well my Thunderbird 2 with all the sotred mails and configurations.

> **bwallum said:**
> How about if I have set up Lucid already and loaded all my non default apps. Can I still link to the home hard drive?

I have labelled the home hard drive as HomeHD. I have put the following line in /etc/fstab```
LABEL=HomeHD    /home    ext3    relatime    0    2
```I get a system config error and then get the Desktop appear without the top and bottom panels.

There can be a problem if the userid (which is a number) is not the same.

What keeps stored in this partition is the number and not the name.

Run
```
ls -l /home
ls -l ~
 
```and see what it gives.

It's possible that some accounts got mixed up.

Make sure that the folder that "looks like" yours is really the one it was supposed to be. Check if names, permissions and the actual content of the folders do match.

If you haven't deleted the Karmic install yet, you can try this:
[http://www.cyberciti.biz/faq/howto-move-migrate-user-accounts-old-to-new-server/](http://www.cyberciti.biz/faq/howto-move-migrate-user-accounts-old-to-new-server/)
Disclaim: I never tried.

---

