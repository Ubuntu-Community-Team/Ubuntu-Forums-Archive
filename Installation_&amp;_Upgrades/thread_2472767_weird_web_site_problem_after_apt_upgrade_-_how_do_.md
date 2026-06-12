---
title: "weird web site problem after apt upgrade - how do i roll back?"
date: 2022-03-11
forum: Installation &amp; Upgrades
---

### Post by robjkampen on 2022-03-11
First a little history - I am new to ubuntu, less than a year of use. My previous two+ decades of Linux have been CentOS / Red Hat.
For a number of reasons I have left the CentOS distro for my servers (4 HW plus numerous virtual machines spread around the globe) and am now using Ubuntu 20.04 LTS for the servers and 21.10 for workstations.
Overall the migration has been okay, many little differences but I can get them working as needed.

Until this week, I haven't had any issues I have been unable to fix or work around.

So now to the situation at hand. A QEMU/KVM based 20.04 virtual machine on a 16 CPU / 32 Thread HW machine also running 20.04.
This particular VM is running a LAMP stack as a web server. The web site is somewhat complex, scrapes data from a number of other websites each night and serves pages based upon the data and images updated every 24 hours.
So it has been running just fine for a couple of weeks, each evening various scripts are triggered by cron and run the php to do the work. The admin part of the web site allows for manual running of the same php scripts to do "scrapes", "downloads" etc.
So the last time it ran okay was the 8th March. On the 9th of March I ran apt upgrade and the following were "upgraded"
2022-03-09 14:48:01 upgrade motd-news-config:all 11ubuntu5.4 11ubuntu5.5
2022-03-09 14:48:01 upgrade base-files:amd64 11ubuntu5.4 11ubuntu5.5
2022-03-09 14:48:04 upgrade libssl1.1:amd64 1.1.1f-1ubuntu2.10 1.1.1f-1ubuntu2.11
2022-03-09 14:48:05 upgrade openssl:amd64 1.1.1f-1ubuntu2.10 1.1.1f-1ubuntu2.11
2022-03-09 14:48:05 upgrade linux-firmware:all 1.187.26 1.187.27

Since this upgrade happened, the over-night cron triggered jobs fail to complete. Funny thing is, if I run the jobs from the admin portal/browser, all works as expected.
If I manually run the bash scripts that trigger the php - the jobs fail.
There are separate scripts (modules) for each site and the two major sites are both failing, but only if run outside of the apache2 hosted web-site; i.e. manually invoked by bash script.
I have made no other changes to the host or any of the php code.
In my old CentOS world I would now do a yum downgrade to rollback each of the packages that were upgraded, so that I can get back to a previously working system.
I see no such options with Ubuntu.
Yes, taking a snapshot prior to running the apt upgrade would have been a great idea, however I do not yet have all my Ubuntu Sys Admin skills and processes in place.
Looking at the list of packages, the only packages that may have impacted this are the base-files:amd64 (no real idea at this point what they are) and real long shot, the linux-firmware:all.

So, my question is - how do I roll back? Or is it going to be easier to stand up a new VM and setup the LAMP stack and web site from scratch? - that will be about 6 - 8 hours of work, work I don't need.
TIA for your thoughts and suggestions

---

### Post by TheFu on 2022-03-11
So, advanced volume management like LVM2 or ZFS have snapshots.  LVM2 is the same across all Linux. Snapshots use the same commands, same options, but you have to install using LVM AND take the snapshot BEFORE it is needed.  Snapshots are part of any enterprise backup solution too. I don't know of any other method that will safely quiesce a filesystem and prevent backup files from becoming corrupted.

If you are using ZFS, then you'll know the commands for snapshotting and pool backups for that tool suite.

I'd have to look up the **apt** commands to download and install an exact version of the packages. If you haven't run **sudo apt autoclean** or **sudo apt clean**, then the packages are still on your system under /var/cache/apt/ (I think). We can use those existing packages directly via the 'apt' command (apt-get doesn't work). 
The history of the installed packages are in the APT history ... /var/lib/apt/.... so you can see what was updated/removed over time.  So, after you put the specific versions of your LAMP stuff back (that's what I'd do **sudo apt install /exact/path/to/file.deb**), I'd make a solid backup (using LVM snapshots) and during the scheduled weekend maintenance period, have apt provide a report for what will be upgraded. Recent versions of apt kick out the command at the end of the **sudo apt update** run. I've never used it, but perhaps "apt list --upgradeable" is the command?

People who patch too quickly sometimes get packages which have issues.  A few times a year, I'll see dependency problems in a few packages.  If the packages to be updated aren't any different than the last time, I'd use **apt-mark** to place a hold on the key packages (just the ones reinstalled) to prevent those from being updated until I'm ready, then try again in 7 days (remove the hold, make backups, etc.).  I only patch over the weekend, never on a weekday.

If the APT history and snapshots aren't working, that's where we have these things called, automatic, daily, versioned, backups.  So, you can restore the system from the backup made overnight. That restore should take relatively little time. A fresh install is 15 minutes.  Restoring settings and core data (say 20G) another 15 minutes, followed by feeding the list of manually installed packages into APT for reinstall ... because you've already restored the settings, APT will see those and assume this is a reinstall, honoring those settings and the locations spelled out as they were prior to the failure. That's another 15 minutes - worst case.  45 min to a restored system, including a fresh OS install.

When you do that fresh install, you can completely change the underlying file systems and volume manager, adding LVM2 of you like. The key is to make the directory structures appear to be the same after the restore as they were before, but the underlying partitions or LVM-LVs are completely unimportant, provided the fstab (same on all Linux) mounts them where you need them. Obviously, there are some files in /etc/ which should NOT be restored into the new OS, but a very handy to have as references. I've gotten into a habit of placing a tag commend inside files under /etc/ so they are easy to find during the restore. I backup all of /etc/ --- it is tiny, so why not?  But I selectively restore files from those backups. Sometimes I'll restore the passwd/shadow/group files, but not always. Just depends.

If your backup restore process, including a fresh OS installation takes more than 45 minutes, I'd say you need a better backup+restore method. 6+ hrs seems like crazy talk to me.  Of course, it will take days to get backups and restore methods so they are that fast. The first 5 restore attempts taught me, through restore failure, what was needed.  Initially, I had a few chicken-egg problems with my encrypted backups.  I was backing up the decryption key ... inside the encrypted backups.  .... uh ... not my proudest moment. I ended up changing from a daily, random, backup key to a system-based generated key with some parts that could be recalculated on any Linux system, if the person knew the method and had the random part stored somewhere to combine for the full, daily, key.

Definitely use VMs for your restore testing.

---

### Post by TheFu on 2022-03-12
So, I patched and rebooted all my systems today.  Haven't seen any issues with the LAMP systems.  I run Nextcloud and Wallabag servers.

There were some warnings during the process, but those didn't break anything that I've noticed. I've come to think of them as 'standard warnings.' ;)

For the nextcloud server (it is a KVM VM), 
```
The following NEW packages will be installed:
  linux-headers-5.4.0-104-generic linux-hwe-5.4-headers-5.4.0-104
  linux-image-5.4.0-104-generic linux-modules-5.4.0-104-generic
  linux-modules-extra-5.4.0-104-generic
The following packages will be upgraded:
  libexpat1 libexpat1-dev linux-firmware linux-generic-hwe-18.04
  linux-headers-generic-hwe-18.04 linux-image-generic-hwe-18.04 linux-libc-dev
  sosreport
```

On the wallabag server (it is an LXD container system), 
```
Calculating upgrade...
The following package was automatically installed and is no longer required:
  libfwupdplugin1
Use 'sudo apt autoremove' to remove it.
The following NEW packages will be installed:
  libfwupdplugin5 libmbim-glib4 libmbim-proxy libmm-glib0 libqmi-glib5
  libqmi-proxy modemmanager usb-modeswitch usb-modeswitch-data
The following packages will be upgraded:
  alsa-ucm-conf fwupd fwupd-signed libfwupd2 libjcat1 libssl1.1 openssl rsync 
  sosreport
9 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.

```

After the update process, I ran apt autoremove and apt autoclean too.
I don't have any other php webapp systems. None of the other 20 systems had any new issues.  

I am seeing a few issues on a desktop where firefox isn't displaying TV schedule data correctly on 18.04, but works perfect on 20.04. Odd.  And the handbrake transcoder stopped handling recorded TV with text captioning. The transcodes crash every time. That's a few weeks old now. I don't see either of these issues as being related to LAMP.

Sorry, that I'm not seeing the same issues.  I'm afraid you'll need to delve deeper into the exact php and MariaDB versions, perhaps php modules as well, to find the issue.  Are the webapp log files of any help?

---

### Post by robjkampen on 2022-03-13
Hi TheFu,
Thanks for the observations and suggestions.
I used to use LVM but could never quite get used to how it worked. It adds a layer of complexity over the HW and core file systems that I found un-necessary. For the last decade I have used simple mdadm managed RAID1 directly on hard drive partitions - with the added benefit that they can be used as a direct drive including boot if raid not up and running. This has served me well for over 10 years, with hard drive failures very simple to deal with, only need someone to swap the physical device, a couple of mdadm commands and all is well again.
Until now (the change is to now run VMs and partition servers to only serve specific tasks, e.g. mail server, web site server, etc.) and the historic awesome stability of CentOS releases (started with 5, then 6 and 7) never had any reasons to rollback, other than where I tried new releases (e.g. major php versions) and then decided to hold off.
The VM world is a little different, thus I will now do snapshots prior to updates.
Back to my specific problem server. I was unable to see any OS and package update that could be the cause. So I had to delve into the application and find out why the php would work when invoked via the browser and not when invoked via php-cli.
Still not 100% sure what the real issue was, as I took the opportunity to refactor chunks of the code base - most of which was developed under php 5.6 and only updated as needed as moved to php 7.x 
I suspect name-spaced issues as most of the objects / classes are called re-iteratively and thus found that some calls returned FALSE for no apparent reason and thus triggered error fail safes. 
So all is now working again, just a slightly dis-quietening feeling at not finding a specific something.
Hopefully I can get my re-build process down to the kind of time frames you suggest - on my most recent hardware systems a simple re-boot takes well over three minutes as all the hardware and memory checks happen, thus even with 12Gb/s SAS SSD, getting complex email systems working and tested takes many hours.
Once again, thanks for the pointers, just not sure I will embrace the LVM way. ZFS maybe, need to research it more - but so far my servers are engineered for a specific task, generously sized, thus never need to grow them outside of original specifications.
Final observation - Ubuntu seems just a little more prone to updates breaking things, but on the flip side, usually much easier to find packages to do what I need, provided I can live with all the Snap mounts that exist.....
Regards
Rob

---

### Post by TheFu on 2022-03-13
If I were starting all over, I'd use ZFS for all my data devices, not LVM and definitely not mdadm.  I've used both LVM and mdadm for decades, but learned about 4 yrs ago at a storage conference that LVM has mdadm code inside it and can do the RAID1/10 stuff itself.  I have some 15 yr old mdadm arrays to be migrated into LVM mirrors, but that system will be retired soon, so the migration will be more of a wipe and connect the storage elsewhere. There is little need for mdadm these days and I would never do without the flexibility that a volume manager provides ever again.

You say you use VMs but not LVM?  How do you actually get a snapshot?  Without LVM providing it, I don't see it happening.  For our VMs, we use LVM LVs on the host provided to the guests as block devices.  Crazy fast and it makes VM storage management trivial to extend while the VMs keep running.  I've posted steps to accomplish that in these forums, but they are tied to LVM.

If you like CentOS, why not just buy a RH license and be happy? Certainly a business can afford that small cost vs having you relearn everything.  At my normal rate, it would be about 1 day of pay for RH license ... and rates are going up.

We run Zimbra for our email/communications server.  Restoring it is under 45 minutes.  Just sayin.

Snaps ... ah ... the stuff I hate and snap abuse is extremely common.  The Canonical linux container manager lxd is really amazing, but they only provide it as a snap package which sorta pisses me off.  Further, the lxd team is 100% in on ZFS to the point that getting LVM to be used as backing storage was too hard for me to figure out, so my LXD containers are LVM with a ZFS overlay.  Arrrrrg!  

OTOH, I love that alpine Linux in a container is 22MB.  Ubuntu's LXD image is much larger and quickly grows to about 1G, but still extremely fast and lighter than a full VM.  

I only use container based stuff for internal-only access. Full VMs are used for internet facing systems.  Thing my next Zimbra upgrade will be into an lxd container - I don't trust Zimbra to be directly on the internet and we've required using a VPN for our users to have access to it for nearly a decade. Security matters.

---

### Post by TheFu on 2022-03-16
You've probably already seen this, but there was a bug in the certificate handling of openssl.  Appears they released multiple fixes. I just got one on my high-risk web-server today. 1.1.1-1ubuntu2.1~18.04.15 and 1.0.2n-1ubuntu5.8
I don't have a webserver running on 20.04. Too new for me.

If you don't already have a solution, those might help.

You can block snaps if you like. Also, there are some aliases for **df** and **lsblk** which can remove all loop devices to prevent the clutter. Since snap loop-mounts aren't using extra storage that isn't already counted in /var/snap/, hiding that data isn't a problem.

---

### Post by robjkampen on 2022-03-17
<rant>
Yeah, looks like something busted in the SSL handshake on https connections to some of my sites. They seem to work fine on my workstation browsers but totally locked out on my android chrome - aahhhhhggg!! 
Trying to debug is a PITA without a roll-back option - so dumb that Ubuntu don't offer this - particularly given the poor quality of some recent updates they have released.
I am not used to having to waste time debugging update issues - maybe only had to do this twice in the 20+ years of CentOS, now I have my second problem within a month with Ubuntu.
I haven't normally run a development server, rather I have used my work station as the development / testing box and when all is well, then move the stuff to production. This is for my software development as well as OS updates.
Unfortunately I am running 21.04 -> 21.10 on my workstation, unaware when I made this choice that the LTS release (20.04) is quite separate and neither the twain meet.
Then I find two days ago that php has just rolled over to v8.0 and 8.1 and I'm trying to write for 7.3/4 on LTS - aahhhggg! another gotcha by Ubuntu. 
Yeah after a few hours I managed to find a way to get 7.4 installed onto 21.10, but then a few hours later went to add a php module and it reverted to 8.1
So now I am coming to the reluctant conclusion that I need to rebuild my two desktop work stations to LTS. Pity I didn't understand this until it bit me in the butt - hard!
For one of my work stations this may turn up other problems as it is a ASUS-PN50 and some of the hardware is too new even for 21.10 - i.e. screen lock doesn't work to shut off my monitors properly and I need to run a manual script as root to make it behave.

I left CentOS for the stability and log term support which has dropped markedly - I still read their mail list and the number of CentOS 8/9 stream update errors are much like what I am experiencing here with Ubuntu.

Maybe I need to keep looking for a viable server OS.
</rant>
 
I looked at Zimbra, but decided to roll my own as I need a couple of rock solid email servers, I have run my own for over 20 years, and they have "just worked" after the initial setup process which is long a laborious to get all the bits working as needed.
So I have two VM's on different hardware running 20.04 LTS and after a couple of weeks (remember I do this in my free time, to support some charities (not for profits) I support) had them working reliably. So far, so good - until the problem that led me to this series of posts.

Now the HSTS / SSL / HTTPS problem I have yet to solve.
Not enjoying the ride thus far.

---

### Post by TheFu on 2022-03-17
Stay with LTS releases. Non-LTS releases are for testing, nothing more.

Have daily, automatic, versioned backups. For internet-facing servers, 120+ days are standard.  Just too many bad people in the world today looking to pwn php, especially.

With and scripting language, always use the the OS installed default. DO NOT CHANGE IT!  If you need other versions, use some sort of virtual environment.  I'm a perl webapp dev and use perlbrew. It is like rvm for ruby.  I think php and python have similar facilities. Use them.

Use ZFS or LVM for snapshots. Retain each for a few weeks to make rollbacks easy.

Much of the stuff in your rant is ignorance about Ubuntu. Don't assume that the CentOS method is what any other distro does. It isn't.  Also, don't assume that how Debian works is the same for Ubuntu. There are important differences.  Ubuntu tries to be more current with packages that have to change all the time. Debian can get really old, fast, especially for desktops.

I have to say, I haven't seen any TLS/HTTPS issues on any of my systems.

New is the enemy of stable. Always remember that.

My Zimbra setups are very stable, but I don't let them on the internet.  My architecture is to have email gateways which are on 20.04 and block 99% of all email in and help me trace inappropriate outbound emails. Workstations aren't allowed to send email except to Zimbra. The gateway only accepts outbound email from the zimbra systems.  I'm fortunate that blocking huge areas of the internet is fine for our inbound email and all our websites. I tweak the ipset rules weekly based on logs. Started blocking a huge part of an commercial ISP in France  last weekend due to thousands of attack attempts per hour.  Felt a little bad, but not really. We don't and never plan to do business there.  I'm less willing to block residential subnets, but have from 'certain' parts of the world over the decades.

---

