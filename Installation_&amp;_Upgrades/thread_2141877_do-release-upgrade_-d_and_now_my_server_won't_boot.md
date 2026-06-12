---
title: "do-release-upgrade -d and now my server won't boot"
date: 2013-05-04
forum: Installation &amp; Upgrades
---

### Post by Maheriano on 2013-05-04
I have an Ubuntu server and last week I ran```
do-release-upgrade
```and it did the upgrade perfectly. It also did every other upgrade for the last 2 years no problem. When the upgrade finished and it rebooted, I SSH into it and it told me again there is an update. But when I run the command again it tells me there's no upgrade available. I searched around on Google for a reason and found you can run```
do-release-upgrade -d
```as another way to upgrade. So I ran it. Afterwards I rebooted and now I can't SSH into it anymore. Any idea why? The server is on site about 30 minutes away so I won't be able to look at it until tomorrow, is there any way to fix this remotely? Thanks.

---

### Post by Maheriano on 2013-05-04
I just got off my laptop and sat down at my desktop which I had used for the upgrade. I realized my terminal read this:
```
Installing new version of config file /etc/bash_completion.d/colormgr-completion.bash ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.9.0-0-generic

Searching for obsolete software
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 
Building data structures... Done 

Remove obsolete packages? 


12 packages are going to be removed. 

 Continue [yN]  Details [d]Write failed: Broken pipe

```

I rebooted the machine from my laptop when it was only halfway through the upgrade on my desktop. Can this be fixed if I go down there and hook up a monitor to the machine?

---

### Post by Cheesemill on 2013-05-04
One quick question.

Why would you want to update your server to 13.10 in the first place?
Development on it has only just started within the last week and it won't be released for another 6 months, the only people that should be using it at the moment are those who are willing to put in the time reporting bugs and fixing it when it breaks (and it ***will*** break). For servers it's recommended to stick with an LTS release such as 12.04.

Unless their is a good reason you mu

---

### Post by MAFoElffen on 2013-05-04
Yes... but a bit tedious.Here's how... 

It the Grub menu, try to use a Recovery Menu Item. If it boots the recovery menu, mount the filesystem, turn on networking, drop down to a root prompt...

If the recovery menu was wacked and didn't start, boot on a comparable LiveCD and mount the filesystem, chroot into it....

```

dpkg --configure -a
apt-get update
apt-get upgrade

```
At the start of the upgrade. it will list all the packages that are being held back. Copy down all the package names. Those are missing pieces and dependencies. If you manually install them, good-to-go.
```

apt-get install package_name another_package_name yet_another_package_name

```
Keep repeating that until you think you are finshed with that list... Then
```

apt-get update
apt-get upgrade

```
To confirm that there are no more held packages left...

If done with that, then check for broken dependencies
```

apt-get check

```
If there is, repair with 
```

apt-get install -f

```
Then you can remove those no longer needed build packages, via
```

apt-get autoclean
apt-get autoremove

```
Good Luck...

---

### Post by darkod on 2013-05-04
My personal opinion (you are free not to listen to it):

1. Upgrade servers only from LTS to LTS, not the normal releases. You can control whether the upgrade prompt appears only for LTS or normal releases. If you want details google should be easy to find the option you need to use/check. Also, this applies only when the current version is LTS, then you have the option to upgrade only to the next LTS without any normal releases in between.

2. Never ever use do-release-upgrade -d on a server. As Cheesemill mentioned, that command upgrades you to the current release that's in development (right now 13.10). Why would you want to upgrade your server to an unstable release still under development?

3. When you start an upgrade process on a remote server, work ONLY from that machine until the process is 100% finished. That way you can see where the process is and avoid making mistakes like this. Why would you touch your server from your laptop if you started the upgrade from your desktop??? First take a look how far the process went...

---

### Post by MAFoElffen on 2013-05-04
I'm curious to what that is really currently based on... I know it the past, but are those things still relevant today?

I was going to say something. I'll summarize. I try to not be bias and I can say things on both sides of that.([https://launchpad.net/~mafoelffen](https://launchpad.net/~mafoelffen))  Besides, I have 2 of my servers already on Saucy Salamander (13.10). ...and I'm gearing up one of my projects for 14.04LTS. 

I guess it all depends on the features someone is looking for... and what of those new features can be backported to. The old argument for LTS is that server LTS is supported for security updates for 5 years. It doesn't mean that release will receive all updates for 5 years... just the security updates. 8.04 LTS just reached EOS, but the technology and features were dated. It was the security updates from current new versions that were backported to the LTS versions (if they applied). So, that does not mean that 12.04LTS or 13.04 is "not secure," (or that one is more secure than the other) but there is a lot more lines of code that leverages probabilities to the chance for vulnerabilities. Of course on the other side of that, one could say that something older has had more time to be explored for vulnerabilities... As for "Stable"... Ubuntu is derived from Debian Testing. Would that mean Ubuntu 10.04LTS is stable now?

Even when you look at something as basic as Linux kernel support by release, some hardware support for current hardware is cover by current Linux kernel... where in the past we had to add them manually... For example Broadcom's NetExtreme, which was a standard in many server boards for years, just recently was added as an opensource kmod. Kernel support for virtual machines, SSD drives, USB 3.0, UEFI, etc... Now what kernel is current in 10.04LTS? On the other side of that, the Ubuntu base system which Server is based on... what really changes in server from one release to another? I feel it does change for enhanced security, stability and the ability to run current applications of current technology.

As for server services and applications... the same current version of Apache is available for an LTS than for non-LTS server right? MySQL? MAAS? Eucalyptus? How far back are those current versions packaged for?

---

### Post by Maheriano on 2013-05-04
Yes, you're all very right, I didn't realize until afterwards the -d flag upgraded to a development release until I saw it was downloading saucy packages. I went and retrieved the server, it's booting into BusyBox and I can't run any sudo commands from there. I'm going to try mounting it from a flash drive and see what happens.

---

### Post by MAFoElffen on 2013-05-05
FYI--
Yes- In the LTS versions, the apt release flag is set to check release versions of LTS releases only. If you install an non-lts that flag is set for all releases. Therefore the "-d" flag will over-ride that flag and upgrade to a non-lts version.

Translated: File /etc/update-manager/release-upgrades has a line on LTS releases saying "prompt=lts". In non-lts versions that line reads "prompt=normal"... the do-release-upgrade -d overrides the value "lts" as if it were "normal".

---

### Post by Maheriano on 2013-05-05
I'm in a LiveUSB environment, how do I chroot into the server? I keep trying to mount the device (RAID5 partition) and it keeps telling me it's already mounted or busy. So I try to unmount it and it tells me it's not mounted. I'm going in circles.

---

### Post by Maheriano on 2013-05-05
When I go to Grub and choose Advanced Options, I can boot into the previous Ubuntu kernel no problem, it brings me right to the command line. I changed my /etc/network/interfaces file to get a dynamic IP from DHCP and now I can run any upgrades I want, I upgraded the system and everything ran smooth. But every time I reboot it still halts with all kinds of errors and boots me into BusyBox like before. Any ideas?

---

### Post by MAFoElffen on 2013-05-05
Did you follow my instructions? Is it now saying it's 13.04?

To answer your previous, which you don't need anymore, see the second half of post #3 of my Graphics Resolution sticky (link in my sig line).

If you followed the instructions I posted... and no other packages are being held, no broken dependencies, etc... What I would do then is to boot on a previous kernel, remove/purge the last installed kernel version (I believe it was linux-image-3.8.0-19-generic) and reinstall it fresh. That will rebuild initrd and rerun update grub on a fresh installed current kernel, which is usually the last step in the do-release-upgrade process. That would be my best guess without seeing those errors.

Another thing to look at, archive and attach to a post would be the "log" files in /var/log/dist-upgrade/ Those are the logs written during that process. Somewhere during the process, it copies that last files from that directory into a subdirectory with a date/time timestamp. (those are the previous files)

---

### Post by darkod on 2013-05-05
After the do-release-upgrade -d I believe it's 13.10 actually. In post #2 kernel 3.9.0 is mentioned in the output.
Unfortunately there is no way to downgrade as far as I know. So you will have to fix 13.10 or reinstall clean another version. Even if you fix 13.10 I wonder how stable it will be, especially if this is a production server.

It's one thing if it's a server to play with, it's another if it's production.

You can try pruging the 3.9.0 kernel as Mike says, and reinstall it again. But I don't think you can downgrade fully.

---

### Post by Maheriano on 2013-05-05
> **MAFoElffen said:**
> Did you follow my instructions? Is it now saying it's 13.04?

To answer your previous, which you don't need anymore, see the second half of post #3 of my Graphics Resolution sticky (link in my sig line).

If you followed the instructions I posted... and no other packages are being held, no broken dependencies, etc... What I would do then is to boot on a previous kernel, remove/purge the last installed kernel version (I believe it was linux-image-3.8.0-19-generic) and reinstall it fresh. That will rebuild initrd and rerun update grub on a fresh installed current kernel, which is usually the last step in the do-release-upgrade process. That would be my best guess without seeing those errors.

Another thing to look at, archive and attach to a post would be the "log" files in /var/log/dist-upgrade/ Those are the logs written during that process. Somewhere during the process, it copies that last files from that directory into a subdirectory with a date/time timestamp. (those are the previous files)

I did this, thank you. I did all the updates and upgrades you posted, everything completed and all the packages were installed, there were no broken dependencies. I also purged the latest 3.9 kernel and am now booting into the previous 3.8.0.19 kernel with a mess of file not found errors at the beginning. But it does bypass those and boot.

Now when I SSH into it I get this which is very strange. It tells me I'm on Saucy Salamander but it's STILL telling me there is a 13.04 release I can upgrade to which is what started this mess. It was doing that right after I successfully completed upgrading to 13.04.

```
Welcome to Ubuntu Saucy Salamander (development branch) (GNU/Linux 3.8.0-19-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

  System information as of Sun May  5 11:37:27 MDT 2013

  System load:    0.05             Processes:           153
  Usage of /home: 0.0% of 1.60TB   Users logged in:     1
  Memory usage:   14%              IP address for eth0: 192.168.1.29
  Swap usage:     0%

  Graph this data and manage this system at https://landscape.canonical.com/

0 packages can be updated.
0 updates are security updates.

New release '13.04' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Sun May  5 00:04:50 2013
integrity@integrity-quote-server:~$ sudo do-release-upgrade
[sudo] password for integrity: 
Checking for a new Ubuntu release
No new release found
integrity@integrity-quote-server:~$

```

---

### Post by MAFoElffen on 2013-05-05
No!!!! Don't do "it" again... So is everything working now?

I can tell you that 13.10 is only a month into the cycle so is still in pre-alpha right now (I have 2 test servers on it). So is 13.04 (with 13.10 branding) with a month of dailies  But in +1, pieces go in and out in the dailies, with the good pieces all put back together the day before release. Between now and 14.04LTS, there's going to be a lot of changes in python... for when python 2.x support goes away. 13.04 would be okay comparatively, but if 13.10, "I" would try to back it off of a production server.

Darko's sort of idea--
Getting back to 12.04? If you backup the system and data... Export the package list. 
```

dpkg --get-selections > installed-software

```
Look at the package list and edit it to basic server app package names instead of the whole list with all plus server app package-versions. This would be the major portion of the work and would require some research. Backup the settings and server app conf files. Everything in the basic system framework is still functionally the same between 13.10 and 12.04- as for server system config settings files that we change.  

Then- Reinstall 12.04LTS fresh. Import the edited package list. 
```

dpkg --set-selections < installed-software
deselect

```
Replace the settings & app conf files. Replace the data... 

Not easy. Some work... but that sounds possible, right?

---

### Post by Maheriano on 2013-05-05
Yes, everything is working to an extent but I'm afraid of it breaking again so I don't want to bring it back to its home until it's more stable. It's only a web server for a quoting system for a building company so I've decided to copy out all the files, export the SQL and just reinstall everything fresh. So far I've copied out the /var/www folder to get all the web files and I've exported the database (which is huge) from PHPMyAdmin. I opened the SQL file with NANO to be sure that it includes the insert data statements and not just the table structure so that's good.  I'm going to install the database here on a local development server to make sure it completes fine and is usable, then I'll wipe the production server and reinstall 13.04, then set up Apache again.
Sorry, I'm not trying to ignore your help, I just don't completely understand some of what you posted and since it's a fairly simple server I think I can reinstall quite easily. I appreciate all the help so far.

---

### Post by MAFoElffen on 2013-05-05
Good deal. Happy things worked out.

I'm on to other things then... I'm here if you need other help.

---

### Post by Maheriano on 2013-05-05
Thanks. I have a new problem now with a blank screen and blinking cursor on boot even though the install was successful. I've started a new thread for this new problem here: [http://ubuntuforums.org/showthread.php?t=2142515](http://ubuntuforums.org/showthread.php?t=2142515). If  you have any idea why that is happening, any information would be appreciated.

---

