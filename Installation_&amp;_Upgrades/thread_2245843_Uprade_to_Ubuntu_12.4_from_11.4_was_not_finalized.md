---
title: "Uprade to Ubuntu 12.4 from 11.4 was not finalized"
date: 2014-09-26
forum: Installation &amp; Upgrades
---

### Post by altkon on 2014-09-26
Upgrade to 12.4 was interrupted 8 mnutes before finalization.
Nevertheless I restarted and managed to install 12,4 but with plenty of defects.
dpkg was corrupted, tried to purge or reinstall but it freezes.
Ubuntu Software Center refuses to remove or install apps.
Update manager is also freezing due to corrupt dpkg and some cache missing.
Icon indicators such as Network Wireless condition, battery charge and sound volume cannot be activated.
Also dropbox not working.
Tried to repair thru sudo commands on Terminal but do not respond.
Besides these the rest is fine except that at start up I select Basic Gnome and then at restart at recovery mode again.
Thanks.
Andre

---

### Post by yancek on 2014-09-26
Generally you must not skip a release in non-LTS releases such as 11.04.  10.04 to 12.04 is OK, 12.04 to 14.04 OK.  Some options at the link below:

[http://askubuntu.com/questions/200960/how-to-upgrade-ubuntu-11-04-to-12-04](http://askubuntu.com/questions/200960/how-to-upgrade-ubuntu-11-04-to-12-04)

---

### Post by altkon on 2014-09-28
You can force to upgrade the release with:

sudo do-release-upgrade

From 11.04, it will upgrade to 11.10 I think and you do it again to upgrade to 12.04.

I tried but was rejected due already other application working.

I was guided to 12.4 Ubuntu from Update Manager.

[COLOR="#B22222"][/COLOR]Recently an icon pops up on the top systray stating "Update info outdated due to a repository is no longer available"

due corrupt dpkg...trying to repair with command "dpkg-configure -a" but unsuccessfully.

---

### Post by altkon on 2014-10-25
> **yancek said:**
> Generally you must not skip a release in non-LTS releases such as 11.04.  10.04 to 12.04 is OK, 12.04 to 14.04 OK.  Some options at the link below:

[http://askubuntu.com/questions/200960/how-to-upgrade-ubuntu-11-04-to-12-04](http://askubuntu.com/questions/200960/how-to-upgrade-ubuntu-11-04-to-12-04)

Unfortunately all the  suggestions stated in the above link were not helpfull, because in my case the dpkg system was interrupted and needs to be run manually and I dont know how to proceed, 
The "dpkg --configure -a" is asked by the system when a previous update/upgrade process have not completely performed good, and it must run with "root" privileged administrative user.
Using the "sudo" command we can do a command as "root" user, and "dpkg --configure -a" need be run from root user.

So can you tell me if it is better to do a clean install, and how to work around this issue.

As I am totally confused. Thanks.

---

### Post by altkon on 2014-10-25
> **altkon said:**
> Unfortunately all the  suggestions stated in the above link were not helpfull, because in my case the dpkg system was interrupted and needs to be run manually and I dont know how to proceed, 
The "dpkg --configure -a" is asked by the system when a previous update/upgrade process have not completely performed good, and it must run with "root" privileged administrative user.
Using the "sudo" command we can do a command as "root" user, and "dpkg --configure -a" need be run from root user.

So can you tell me if it is better to do a clean install, and how to work around this issue.

As I am totally confused. Thanks.

Package Manager wants me to perform the following also:

autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
user@user-Satellite-A200:~$

---

### Post by ian-weisser on 2014-10-25
> **altkon said:**
> So can you tell me if it is better to do a clean install, and how to work around this issue.

I think it's much simpler for you to backup your data and do a clean install.

Recovering a broken install from an obsolete version while trying to do an untested and unsupported upgrade path, and without a good understanding of the package manager, is slow (several days of work, perhaps a week or more) but possible. You will learn a lot along the way.

---

### Post by altkon on 2014-10-26
Can you please give me the sudo command for a clean install?? I am on a dual boot system with Windows, 
Because I tried an auto clean without success.
user@user-Satellite-A200:~$ apt-get autoclean
E: Could not open lock file /var/cache/apt/archives/lock - open (13: Permission denied)
E: Unable to lock the download directory
user@user-Satellite-A200:~$

user@user-Satellite-A200:~$ apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
user@user-Satellite-A200:~$

---

### Post by Vladlenin5000 on 2014-10-26
A clean install is like what you would do in a "bare metal" system, ie, you boot from the installation media and proceed to install as usual.
Upgrading from obsolete versions is no longer possible without major tweaking. All the repositories needed are no longer available.

---

### Post by altkon on 2014-10-26
> **Vladlenin5000 said:**
> A clean install is like what you would do in a "bare metal" system, ie, you boot from the installation media and proceed to install as usual.
Upgrading from obsolete versions is no longer possible without major tweaking. All the repositories needed are no longer available.

In my case what would you suggest to be done??? Because my system at this stage is cripled as I cannot update/upgrade install/uninstall, and all other synaptic features.
Thanks a lot for your guidance.

---

### Post by Vladlenin5000 on 2014-10-26
> **altkon said:**
> In my case what would you suggest to be done???

I suggest you read post #6 again. It's all there: Backup and do a clean install. If you don't know how to backup given that you no longer can access the OS normally, I suggest you boot a live session as usual and then copy what you need to copy to an external drive.

---

### Post by altkon on 2014-10-26
For back up OK, I can handle. But I dont know the command for a clean insatll sudo...could you please advise....Tks

---

### Post by Vladlenin5000 on 2014-10-26
A clean install is a clean install, an install from scratch... Like you would do in a machine WITHOUT any OS, in a new hard drive, ... It has been suggested because it's much easier than fixing the mess your current installation already has.

---

### Post by altkon on 2014-10-26
Since I dont have an OS system like upgrade Manager to choose from, from where should I pick up the new OS version for Ubuntu.
Sorry for my ignorance..

---

### Post by Vladlenin5000 on 2014-10-26
Sorry but I have to ask: Are you for real or are you trolling in this nice sunny Sunday, of all days?... C'mon :p
You need to obtain an ISO from ubuntu.com, either 14.04 (LTS, recommended) or the brand new 14.10, choosing 32-bit or 64-bit according to your system needs. Then follow the instructions to burn a DVD or to make a bootable USB pendrive and simply boot from it when you're ready to say good-bye to your old installation and proceed to do a clean install (you can select the same partitions and format or delete everything in the hard drive, create new partitions or simply let the Ubuntu installer do everything for you).

---

### Post by altkon on 2014-10-26
Of course I am for real, and I am calling you from Athens Greece , on a cloudy Sunday Noon.
I am truly obliged for the time you spend on this issue with me.
I will follow the instructions and I will let you know once I have resolved this case.
Thanks a lot.
Andre

---

### Post by altkon on 2014-11-02
Hi..
My case now resolved with a clean install of 14.04. As you told me I had backed up  my home files to an external USB disk but now the system does not let me restore .
What I do is I copy one file from my back up archive on the Usb and paste it to forward but it fails.
I have also managed to convert 14.04 Ubuntu to Classic Gnome  Mode from Software Store instead of Synaptic which no more available.
All these for your info and comments.
Regards.
AA

---

### Post by kansasnoob on 2014-11-02
> **altkon said:**
> Hi..
My case now resolved with a clean install of 14.04. As you told me I had backed up  my home files to an external USB disk but now the system does not let me restore .
What I do is I copy one file from my back up archive on the Usb and paste it to forward but it fails.
I have also managed to convert 14.04 Ubuntu to Classic Gnome  Mode from Software Store instead of Synaptic which no more available.
All these for your info and comments.
Regards.
AA

Probably best to open a new thread titled something like **Can't restore previous backup** here:

[http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

I'd guess that it has something to do with permissions but I'm not proficient in that matter.

---

### Post by altkon on 2014-11-02
> **kansasnoob said:**
> Probably best to open a new thread titled something like **Can't restore previous backup** here:

[http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

I'd guess that it has something to do with permissions but I'm not proficient in that matter.

I already did it, thanks a lot for your guidance.

---

