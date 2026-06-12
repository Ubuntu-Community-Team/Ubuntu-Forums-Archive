---
title: "Cannot Upgrade Ubuntu 10.10 to Natty Narwahl"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by hexxd on 2011-05-17
For some reason, I am unable to upgrade 10.10 to 11.04. When I open the update manager, I see the option to upgrade, and upon clicking that, the CPU downloads two files, then does nothing, and when I open the update manager again, the option is still there, as if I haven't upgraded. How can I fix this?

---

### Post by mörgæs on 2011-05-17
Hi, welcome to the fora.

There is no need to worry. 11.04 is still having its problems, so staying with 10.10 is not a bad idea. Just apply the ordinary updates to 10.10.

---

### Post by hexxd on 2011-05-18
Is that to say that the update will eventually update once 11.04's kinks are worked out?

---

### Post by mörgæs on 2011-05-18
My advice is to stay with 10.10, just applying upDATES as always. The upGRADE to 11.04 is risky.

There is support for 10.10 almost a year from now, so there is no need to hurry.

---

### Post by Blasphemist on 2011-05-18
Just do your homework before upgrading, and use a live cd to upgrade to natty (11.04). Look at the web site and the resources on unity and classic session types in natty. Just get a feel for what the upgrade will provide and what changes. This upgrade is a bigger step than normal in preparation for the next LTS release.

Download and burn the iso for the live cd. Use this and boot to it to ensure that your hardware is supported without issue. Most hardware is but especially with old hardware there have been issues. Natty also more fully implements kernel mode settings and that can affect video issues. This is where there have been the most upgrade issues.

Many people recommend clean install upgrades as a matter of best practice. By this I mean that you back up your home directory at least to a usb or other storage and install upgrades from cd instead of through update manager. I've done both and do feel that using the live cd is a better practice though I've successfully done both.

As you to your update manager issue, if you want to keep going that way, are you able to tell what files it does download? Provide screen shots if you want and maybe we can see what is stopping it. You may also want to use synaptic package manager to run fix broken packages from the edit menu. There may be an issue there.

It may help if you upgrade from the command line if you can't use the live cd. At least it may give you more information about what is causing your current issue. Here are the steps.
> ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
(Note: the first two lines simply make sure your current distribution is current before upgrading the entire distribution, and are optional.


This will help you back up your current apps and settings, in addition to the backup of /home.
> **Reinstalling applications after a fresh installation**
If you upgrade your Ubuntu system with a fresh installation, it is possible to mark the packages and services installed on your old system (prior to the upgrade) and save the settings ("markings") into a file. Then install the new version of Ubuntu and allow the system to reinstall packages and services using the settings saved in the "markings" file. For instructions, see this Ubuntu forum thread. In brief:
On the old system:
_Synaptic Package Manager -> File -> Save Markings_
Save the markings file to an external medium, such as a USB drive.
Complete the backup of your system's other important files (e.g. the /home directory) before the installation of the new system.
In the freshly-installed new system:
_Synaptic Package Manager -> File -> Read markings_ and load the file on your USB drive (or other external storage) previously saved.
Note: Many packages, dependencies, and compatibilities change between version of Ubuntu, so this method does not always work. Automated updates remains the recommended method.
Alternatively you can use this command-line method.
Prior to the clean installation. run:
```
dpkg --get-selections > ~/my-packages
``` 
This creates a my-packages file in the ~ (home) directory which will contain a list of the packages installed on the old system. Copy this file to a safe place (as you will need it after the new installation).
Proceed with the clean installation. Enable the same repositories that were enabled in the old system.
Now copy the my-packages file to the ~ (/home) folder. Run:
```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```
Any packages that you had installed (that are in the new repositories) will now be installed. Excluded will be any manually-installed packages (that are not in the new repositories) and any packages that were compiled from source.


---

### Post by moshmage on 2011-08-04
I've been on a quest today, I've been updating my ubuntu 2008 CD i had (i did not have any more cds so i couldnt just make a 10.10 or 11 copy).

Here is how i made it, after butload of time looking on how to make the update gui work:
go here: [http://changelogs.ubuntu.com/meta-release](http://changelogs.ubuntu.com/meta-release)

find the version you want to update to, in your case is naty, and then find the link to the upgrade tool (yours is [http://archive.ubuntu.com/ubuntu/dists/natty-proposed/main/dist-upgrader-all/0.150.2/natty.tar.gz](http://archive.ubuntu.com/ubuntu/dists/natty-proposed/main/dist-upgrader-all/0.150.2/natty.tar.gz) )
then unpack it somewhere and sudo ./name_of_upgrade

```
wget http://archive.ubuntu.com/ubuntu/dists/natty-proposed/main/dist-upgrader-all/0.150.2/natty.tar.gz

tar xvzf natty.tar.gz
sudo ./natty
```
wait for it... you are done.

---

