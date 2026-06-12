---
title: "3 Options for Upgrading to New Version"
date: 2023-02-24
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2023-02-24
This question may help a lot of people when upgrading to new version of Ubuntu, as its been stated many places - its best to install from Disk.

I have the Home folder backed up off v20.04, minus an ignore list, using rsync. Now a few questions!

1. Will the v22.04 allow installation over v20.04 - in other words - upgrade via the Disk? and Will the Home folder still be intact?

2. What if I install v22.04 fresh utilizing the whole drive (SSD). Afterward, just copy / restore the Home folder from the Backup?

3. Would it be better to partition the SSD in 2 parts, Install v22.04 in 1, and copy the Home folder to part 2?

Thanks!

---

### Post by MAFoElffen on 2023-02-24
Am I confused? You have a current thread open [here]("https://ubuntuforums.org/showthread.php?t=2484308") where your 20.04 installation is failed and you are faced with fixing a grub boot problem. That's correct right? Where you are having problems booting?

You can install fresh and connect an existing home folder in that install. But you are faced with more than that right? Because of your booting problem?

---

### Post by Rick St. George on 2023-02-24
Incorrect, that's not my thread. Here is my thread --> [https://ubuntuforums.org/showthread.php?t=2484308]("https://ubuntuforums.org/showthread.php?t=2484308")

My UbuntuStudio v20.04 is back up and running. Just haven't done a Shutdown and Restart to see if Rebuilding via Live-Disk worked yet. So I am pondering Upgrading to v22.04 since I'm haveing issues. But have much Data, Domains, and VirtualBox, etc. to keep ... all in the Home Folder. Knowing what I know now, I should use Option #3 above, but am unsure of Partitioning an SDD drive. Disks program shows it in OK condition. But being a logical thinker, I personally don't believe its safe to partition a SSD.

So there is my delimma. And I'm sure a lot of others would enjoy a good answer!

Thanks!

---

### Post by MAFoElffen on 2023-02-24
Yes... I just corrected that and updated my previous post... Sorry.

Glad to hear the other thread is resolved now. (Please go back and mark that thread as "Solved".)

I would keep what you have now, and do a 'sudo do-release-upgrade"...

EDIT: Recommendation based on the experiences of your last thread / issues.

---

### Post by Rick St. George on 2023-02-24
Every time I have dont that, over the last 13+ years, it has corrupted my system. I end up installing a fresh version from DVD Live-Disk. 
Hence my 3 questions / options don't include your suggestion.
So ... can you answer the 3 questions???

---

### Post by guiverc on 2023-02-24
> **Rick St. George said:**
> This question may help a lot of people when upgrading to new version of Ubuntu, as its been stated many places - its best to install from Disk.

I have the Home folder backed up off v20.04, minus an ignore list, using rsync. Now a few questions!

1. Will the v22.04 allow installation over v20.04 - in other words - upgrade via the Disk? and Will the Home folder still be intact?

2. What if I install v22.04 fresh utilizing the whole drive (SSD). Afterward, just copy / restore the Home folder from the Backup?

3. Would it be better to partition the SSD in 2 parts, Install v22.04 in 1, and copy the Home folder to part 2?

Thanks!

I'll give a response, but as I'm not a Ubuntu Studio user, and my own QA (*Quality Assurance testing*) on it is somewhat minimal. I'll keep this generic with my thoughts.

- Ubuntu Studio 20.04 LTS used the Xfce desktop, Ubuntu Studio 22.04 LTS uses KDE Plasma, which *will likely complicate re-installs*, thus I cannot give specific advice for that system here.

- Ubuntu Studio is more than just a different desktop; ie. switching from Xubuntu 20.04 to Kubuntu 22.04 I would feel *somewhat confident* providing advice for, but your system is more than just that.

I regularly perform QA-testing of *non-destructive* re-installs, in fact did multiple just this last week; eg. [here]("http://iso.qa.ubuntu.com/qatracker/milestones/442/builds/271702/testcases/1701/results") which is a Lubuntu *jammy.2* install (ie. RC or release candidate for Lubuntu 22.04.2 LTS ISO); meaning the d780 which was an "*Install using existing partition*" testcase install which will mean nothing for you... If interested you'll find it written up [here ]("https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743")where you need only search for "*Install using existing partition*". This *re-install* or *repair install *maybe an option for you now, which is why I'm talking about it this much... ie. I have a Lubuntu 20.04 (*focal*) LTS system on that box, where I'll use this install method to change release to Lubuntu 23.04 (*lunar*) rather soon. it allows me to change releases easily & quickly.

There can be complications though; if you use *third party* (non-Ubuntu) software, are going backwards (ie. *I use the install method going to older releases too, but I always do my homework first when doing this to ensure I'll not have problems*), and you're switching Desktop.  It can work with changing desktops though (eg. Lubuntu 18.04 LTS used LXDE, and I used that to change installed to Lubuntu 20.04 LTS using LXQt), but your Xfce to KDE Plasma install is more complex due to Ubuntu Studio configs....

ie. here (^) I was talking about how I read your "v22.04 allow installation over v20.04" point 1.

Thoughts on Restoring data:

My old PC power supply died, so I had to switch to this newer box earlier this year.  My system is dual boot (a LTS release so *jammy* or 22.04 & the *development* release so *lunar*). 

Normally I put setup my partitions on a new box as I want them, restore (*or copy across my data*) and use the re-install option to install a newer system (*but not altering my data*) on it.  I didn't do this on this box however, as I used the new (*actually refurbished second-hand, but new to me!*) machine for QA-test installs so the system that was installed was brand new (*two installs; jammy [22.04] & lunar [23.04]*). 

I then booted each of the systems, and copied my data across from a network share... As I recall I used the equivalent of `cp -prn`  (ie. copy, recursive & NEW) so the new configs on my 'new install' would not be overwritten... I did this purposely so this install is more *default* than my prior 2017 install was.  For the apps where I wanted my old config; I just manually replaced those as I discovered I wanted them.

(I'm using *lunar* now and this `firefox` setup is a new one, however if I boot *`jammy`* that firefox setup is exactly what existed on my old box..  As for which is best, I've been unable to decide.. and I've been using this box for about a month now!)

This (^) discussion is around your point 2 "*install v22.04 fresh utilizing the whole drive (SSD). Afterward, just copy / restore the Home folder from the Backup*" 

Finally your 3rd question; my thoughts....

Ubuntu Desktop systems (*up to 22.10 anyway, using either `ubiquity` or `calamares`*) can re-install non-destructively with a single partition (/) or separate /home which I've tried to allude to with my re-install types, so how you partition is completely your choice.

The primary reason I use a separate /home is that whilst Ubuntu can non-destructively re-install even if only a single partition is used, many GNU/Linux systems cannot - thus I've almost always used a separate /home partition.  My older box had / & /home (for both LTS & *devel* releases) plus a shared swap. 

 I actually expected that same setup replicated on this box too, just looked at NOPE I have installed everything on a single partition (/) (*I'm ignoring the ESP or uEFI System partition*) and have only *swapfile* too.  My only conclusion is I've installed assuming I'm going to remain on Ubuntu into the future on this box  (*I'm still actually surprised with what I saw; but I think its the default setup for the QA test I used for my installs; which is why the install is this way**; not my usual option*). 

Ubuntu Studio uses the `calamares` installer that is shared with Lubuntu.. I know it pretty well given I'm *rather heavily* involved with Lubuntu and we've used it for all releases from 18.10 & up. It allows non-destructive installs, as does `ubiquity` which is used by most *flavors* and Ubuntu Desktop (*inc. Ubuntu Studio with their 20.04 release** & earlier*).

I've not had successful *non-destructive installs *with the new *canary* desktop installer; but I've not tried again recently; so I can't confirm you can re-install with Ubuntu Desktop 23.04 *successfully* yet, but its expected to have it working there too (*and into the future with plans to return the "Repair Installation" choice in the installer menu*). 

Partitioning though is completely your choice; Ubuntu will cope with almost anything that works for you.

---

### Post by Rick St. George on 2023-02-24
> **guiverc said:**
> 
Partitioning though is completely your choice; Ubuntu will cope with almost anything that works for you.


Very Good Info, Thanks so much for your time and efforts. Regarding the above, one question remains.

What about the safety of partitioning an SSD drive with 3 partitions. 1) small for Boot, 2) 1/2 for main sys install, 3) 1/2 size for Home Dir.?

Just an idea I had, but concerns over having to re-install other pkgs such as VirtualBox. If the 22.04 Disk will Upgrade the 20.04 version then all may be fine!
IF there is an option for that in the Release for 22.04.  I have 117GB in my Backed-up Home Folder.

HMmmmm!
Should I -or- shouldn't I !!!

---

### Post by guiverc on 2023-02-24
I would avoid having a partition for `/boot`....

Years ago my opinion differed to my current one, but I got tired of needing to maintain it, ensuring I had sufficient space & needing to create more space on it (*ie. issues installing new kernel upgrades*).. So for my systems `/boot` is now just a directory on the `/` partition.  I'd only use a separate `/boot` partition for some server installations that can benefit from it; not desktop systems.

Note:  I'm not talking about `/boot/efi` or the ESP (*uEFI System Partition*).   My old box (*with the dead CPU*)  was a 2009 dell & thus didn't have one, but this box is much more  modern and for sure has it. This refurbished box had windows 11  installed which I've not yet deleted; it came with asmall ESP (*too small for my intended multi-boot setup*)  so I had the first install create a new *larger *one which is now used. The  second install just used the larger ESP created by my first install (*I've  called the installs first & second here because I can't recall if I  installed jammy/22.04 or lunar/23.04 first/second... the windows I've  not used, except to confirm the 'install alongside' didn't adversely  impact it for QA purposes; that disk space I consider 'available; not  yet allocated' for either of my two Ubuntu systems, as I'm not  interested in windows*).

> **Rick St. George said:**
> 
IF there is an option for that in the Release for 22.04.


Ubuntu Studio uses `calamares` same as Lubuntu, thus instructions on the re-install will be as per my *understanding the checklists* link I provided.  ie. read [https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743](https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743) especially the "*Install using existing partitions*", do you understand it?  If you have questions you can ask there here...

FYI:  That *doc/link* was written with *Quality Assurance* testers the intended audience (*not end-users*), but I use it as reference now even for support as it's easier to find than the 30+ times I've written about the install type on askubuntu etc.

I will note that `calamares` has received a SRU (*stable release upgrade*) that I believe is of benefit, thus I'd for sure try and use updated media that benefits from it (ie. 22.04.2 media if possible or 22.04.1, avoiding 22.04 initial media if you can), as the fixes are of benefit.

Always backup first; in my own experience (*which involves lots of QA-test installs; maybe 20 just in the last week*) I've found `calamares` a little more *fragile* than `ubiquity` is... (though to be honest I know I can rather easily cause `ubiquity` to crash where `calamares` won't; ie. all installers all have strengths & weaknesses)

Given what an installer does; it is a somewhat risky procedure... 

Yes I do trust the install process, having used a system I use for non-destructive re-installs at least twice in the last week, without any *real* backups for that box too!  (*In my case though I'll not lose my data, just the hours re-creating my setup/data needing to reconstruct it from elsewhere*), but as I use installers rather often, I'm less likely to make a mistake (*I hope*) as its very easy to do!

---

### Post by Rick St. George on 2023-02-25
> **guiverc said:**
> I would avoid having a partition for `/boot`....

I already have one for 'boot/efi'

> 
Ubuntu Studio uses `calamares` same as Lubuntu, thus instructions on the re-install will be as per my *understanding the checklists* link I provided.  ie. read [https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743](https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743) especially the "*Install using existing partitions*", do you understand it?  


Yes, I studied it, and I understand it. Therefore, I'm going to use the option to install in existing partition.

You posting a reply is very much appreciated. And I had to laugh at your using Clementime to listen while you work. 
Your one coool kat man! Keep up the good work, and I'll do the same.

Peace!
:guitar:

---

### Post by guiverc on 2023-02-25
> **Rick St. George said:**
> 
What about the safety of partitioning an SSD drive with 3 partitions. 1) small for Boot, 2) ...

You probably meant ESP with "1) small for boot"; but that was why I responded as I did.

ESP = (u)EFI System Partition & stores specific data needed to boot uEFI systems; it must also be of specific format (ie. *file-system*) so themachine *firmware* can access it.  There are no such restrictions on `/boot/`. The `/boot` directory contains everything except ESP data, which is mounted on `/boot/efi/` so it can be found for updating. 

`/boot/` is what is optional & mentioning.

`calamares` will default to creating an ESP if the machine requires one (*it determines this by how its booted and the installation media; alas it can be mislead to a wrong conclusion if the ISO isn't written as it was intended*).

---

