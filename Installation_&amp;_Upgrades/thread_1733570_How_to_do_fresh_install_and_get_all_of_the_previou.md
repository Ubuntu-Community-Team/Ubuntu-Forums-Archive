---
title: "How to do fresh install and get all of the previously installed packages?"
date: 2011-04-19
forum: Installation &amp; Upgrades
---

### Post by bartonlp on 2011-04-19
I would like to do a fresh install but keep the packages I previously installed instead of having to reinstall all the extras. I am sure there must be a way to keep my apt_get database with all the additional packages I have loaded. I just don't know how.

Thanks

---

### Post by oldfred on 2011-04-19
This downloads everything so it is good for upgrades as you get the same app but any newer versions.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

dpkg --get-selections > ~/my-packages
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings'

But do not just import all sources as that can lead to issues of versions:
[http://askubuntu.com/questions/2038/backup-software-sources](http://askubuntu.com/questions/2038/backup-software-sources)
sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, the tip will only reinstall Ubuntu files,

List with explanations of programs, not for reinstall
dpkg -l > ~/installed_programs.txt

Location of downloaded debs
/var/cache/apt/archives/

---

### Post by bartonlp on 2011-04-19
Thanks I knew there must be a simple way to do what I wanted.

---

### Post by Splat_NJ on 2011-04-19
OldFred, thanks for writing this, but I'm a confused man right now. I just got a SATA drive and will be replacing my old EIDE drive so I need to backup my Ubuntu's programs and their configurations. Let me please run this past you to hopefully ensure I didn't screw anything up. :)

This is what I've done so far:
*Backed up my keys with command "sudo apt-key exportall > ~/repositories.key"

*Backed up  "sources.list" file and "sources.list.d" folder.

*Backed up the "archives" folder so I don't have to redownload all the packages.

*Backed up program/package configurations with commands:  "dpkg --get-selections "*" >myselections" and "debconf-get-selections > debconfsel.txt"

*Backed up the Thunderbird and Firefox profile directories.

Anything else I should do or change?

---

### Post by oldfred on 2011-04-19
All of /home. Your hidden setting and files are in /home as well as your data, not just Firefox & Thunderbird profiles. Only if reinstalling the same version, will saving any of the downloaded .debs do any good.

Someone posted this:

backup the following:

1. /home (Users' personal files and settings)
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup

sudo cp /etc/apt/sources.list ~/sources.list.backup

More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

I try to manually change system settings so I know which files I have edited and usually put a copy into my /home as a backup. I usually do not then backup /etc. But I now keep my last install as a working system so I can go back anytime and get something that is missing. I have three (smaller) drives and just install to different partitions, copy some settings from /home and link in my /data partitions.

---

### Post by Splat_NJ on 2011-04-21
First off, thanks again OldFred. I did manually backup everything recommended. But before undertaking the fresh install, then copying it all back over I wanted to try something. 

I installed XP first onto the SATA drive. I then used my Ubuntu backup "live install cd" that Remastersys created to install my backed up Ubuntu onto the new SATA drive. I even changed the size of the "/, "/home", "/usr", and "swap" partitions from what was originally used in the backup.  There were only two issues needing to be corrected. (1) After the initial Ubuntu bootup Grub didn't see XP so it wasn't listed in the boot menu. This was fixed via "sudo update-grub" and a reboot.   (2) My auto-mountings of a few partitions on the other drives needed to be added to fstab.  Since all that was done everything's been running fine.

I actually did this whole XP/Ubuntu install three times because I wanted to change a few things like partition sizes, etc., and I was curious if it was a fluke the first time. Each time it worked! This worked for adding a new harddrive and changing the location of a Ubuntu install but I don't know if it would work for a new PC altogether. I may have to try that this weekend!

---

### Post by oldfred on 2011-04-21
@Splat_NJ

Glad to hear it worked.

---

### Post by Elludium_Q-36 on 2011-04-22
Hey, thanks for the good information here!

I tried starting a thread looking for these answers but got no helpful info.  [http://ubuntuforums.org/showthread.php?t=1729000](http://ubuntuforums.org/showthread.php?t=1729000)
Perhaps this should be made a sticky.

I'm running Kubuntu 8.04 "Hardy Heron".

Could we spell it out for those of us on the earlier stages of the learning curve?

I have backed up the /home/ directory.

Once I realized that the ">" was part of the syntax, I was able to follow backing up the keys, as in post #4 above.  I backed up mine to removable media, a usb flash-drive.

It's pretty easy with Dolphin to find your directory path in the menu: View -> Navigation Bar -> Edit Location; or by keyboard shortcut: Control + L.

I did:
```

sudo apt-key exportall > /media/disk/Kubuntu2/repositories.key

```

So in my case, after reinstallation, I can issue:
```

apt-key add /media/disk/Kubuntu2/repositories.key

```
Or is it:
```

apt-key add > /media/disk/Kubuntu2/repositories.key

```
?

The full paths would be appreciated. I did find the software sources, "sources.list" files in: /etc/apt/   I usually use Synaptic Package Manager to edit repositories.  What are the "sourceslist.d" files?  I see the Medibuntu repository is listed in the sources.d folder.

If the archives folder contains the data for downloaded packages, that's great since I'm now offline, on "sneakernet"  I can use Keryx [http://keryxproject.org/](http://keryxproject.org/) for updates but would rather use what's in the system now.  Where does this folder lie?

Program/package configurations...  I'm in 8.04 and tried:
```

kubuntu@Kubuntu-jc1:~$ dpkg-get-selections --help
bash: dpkg-get-selections: command not found
kubuntu@Kubuntu-jc1:~$ debconf-get-selections --help
The program 'debconf-get-selections' is currently not installed.  You can install it by typing:
sudo apt-get install debconf-utils
bash: debconf-get-selections: command not found
kubuntu@Kubuntu-jc1:~$ 

```

I copied the /etc/ directory to my flashdrive, that is, those files that allowed copying; even when doing so as root.

I have nothing in /var/spool/cron/crontabs/

It would be great if someone packaged an application to back this stuff up.  Not Keep though, I tried it and it did not work...

---

### Post by Splat_NJ on 2011-04-22
> **Elludium_Q-36 said:**
> It would be great if someone packaged an application to back this stuff up.  Not Keep though, I tried it and it did not work...

Instead of going thru all that headache use [Remastersys]("http://remastersys.sourceforge.net/").  I've never had a problem with it.

---

### Post by Elludium_Q-36 on 2011-04-26
Remastersys looks great.  I can add it to my bag of tricks, along with Keryx. [http://keryxproject.org/](http://keryxproject.org/)

In the meantime, my reason for reinstalling is not a hard drive issue but that I hold some incorrect packages from a later version; as I outlined here: [http://ubuntuforums.org/showthread.php?t=1729000](http://ubuntuforums.org/showthread.php?t=1729000)

Therefore, I need to know what I'm backing up and reinstalling.  I'm sure I will edit my sources/repositories file.

Thanks for recommending Remastersys.  I will check it out but for now I may need to do it old school and need the info :-|

---

