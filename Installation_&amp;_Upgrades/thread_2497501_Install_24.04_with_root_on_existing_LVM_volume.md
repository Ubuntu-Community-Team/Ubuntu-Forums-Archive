---
title: "Install 24.04 with root on existing LVM volume"
date: 2024-05-08
forum: Installation &amp; Upgrades
---

### Post by jan-swi-prolog on 2024-05-08
I have Ubuntu 22.04 running on two disks, each being an LVM group.    The first disk has an LVM volume that is my root, the other several LVM volumes.     I would like to upgrade to 24.04, but I understand that will take until about August.

So, I created a new LVM volume in the first drive (group), hoping I could install 24.04 there.    The installer gives the option for manual partitioning, but does not show any LVM devices.    After opening an terminal and running lvscan, I can see all volumes, but the installer still does not see them.    There is an option for LVM under the non-manual partitioning, but this seems to erase the entire disk.   That is not what I want.

Has anything changes?  In my memory it was possible to install to existing LVM volumes after manually loading LVM and activating the volumes.

Is it possible to use an existing LVM volume as Ubuntu root in 24.04?

---

### Post by TheFu on 2024-05-08
My understanding is that LVM was broken to support Bitlocker installs by the installation team.  The bug was known and reported.  You can find other threads here discussing it.[https://ubuntuforums.org/showthread.php?t=2492697&p=14166352#post14166352](https://ubuntuforums.org/showthread.php?t=2492697&p=14166352#post14166352) is one from MAFoElffen. He does server testing and has an open bug for lack of LVM support.

I'm with you.  Screwed.

Until LVM works with manually created volumes at install time, 24.04 will not be installed on any physical system here.  LVM is central to how we manage storage AND get non-corrupted backups.  I cannot imagine a server that doesn't support LVM.  Desktops with LVM are "nice to have" but on a desktop, storage management isn't nearly as critical.  My main desktop uses ZFS, but I haven't needed to learn too much about it because there haven't been issues.

---

### Post by Dennis N on 2024-05-08
> Is it possible to use an existing LVM volume as Ubuntu root in 24.04?
Yes it is possible. My strategy is to install 23.10 on the LV and then upgrade to 24.04 with Software Updater when the upgrade option becomes available. If it succeeds, then I continue to upgrade to future releases also using Software Updater.

For me, there only fresh install of Ubuntu after this will have to be as a virtual machine until a better installer arrives.

---

### Post by jan-swi-prolog on 2024-05-08
I see.    The 23.10 route suggested by @dennis N below is an option, but not very attractive and probably rather shaky in case the installation breaks and 23.10 does no longer exist.

Do people here think this will be fixed anytime soon, or are we likely not to see LVM support for a long time for Ubuntu? 

I consider this a show stopper.

---

### Post by Dennis N on 2024-05-08
> **jan-swi-prolog said:**
> I see.    The 23.10 route suggested by @dennis N below is an option, but not very attractive and probably rather shaky in case the installation breaks and 23.10 does no longer exist.

Do people here think this will be fixed anytime soon, or are we likely not to see LVM support for a long time for Ubuntu? 

I consider this a show stopper.

This situation has existed since Ubuntu 23.04 when the new installer was introduced. A bug report on this missing capability was filed back then, but now is marked "Won't Fix". That's not encouraging. Nothing is in the works to fix this.

The one-step upgrades are reliable based on my own experience, so I'm confident the plan will work. If not, I've got Ubuntu 22.04 to fall back on.

---

### Post by MAFoElffen on 2024-05-08
I do test Dev Cycle Server Editions, because of being on the Ubuntu Server Team. It's part of what I do to try to help. But I also test Dev Desktop Editions. 

The 24.04 Server Live Installer is still Subiquity. The partitioner in it will recognize existing LVM2 storage containers. We can still setup LVM2 on it in the Live Environment from a system prompt (or anything before), go back to the partitoner as manual partition, and it see's it. Set the mounts to those containers, and continue the install. After the install is finished, either chroot into /target and install ubuntu-desktop... or wait until after the first reboot, to do the same.

Yes, this has been around since they went to the newer Desktop in Lunar (23.04) and is a sore spot with me.

Wait a few minutes. No one answered me with my last comment on that Bug Report that they closed, so I will file another. I will come back here to post the URL of that Bug Report. I would appreciate "anyone concerned" to please join it as affected. We really need to be heard out on this and have it fixed. Tell your friends. Tell your friends dog. Tell your enemies. We need help pushing this through.

BRB.

---

### Post by MAFoElffen on 2024-05-08
Okay. Done. New Bug Report for all we can get to join as affected (interested, concerned, outraged, etc.):
[https://bugs.launchpad.net/ubuntu-desktop-provision/+bug/2065236](https://bugs.launchpad.net/ubuntu-desktop-provision/+bug/2065236)

---

### Post by Dennis N on 2024-05-09
I added to the "affects me" count. I was person #2. Nice report!

---

### Post by MAFoElffen on 2024-05-09
I added a post in the DEV-Ocular (Ubuntu Development) Section: [https://ubuntuforums.org/showthread.php?t=2497520&p=14189077](https://ubuntuforums.org/showthread.php?t=2497520&p=14189077)

To try to stress that we need to address this further in the Ocular Dev cycle...

I also found a similar Bug report filed on Noble that just addresses LVM2 issues (I linked that into this Bug Report) , but that Bug Report really is not aware that it really is a bigger problem that needs to be resolved, in that it also needs to recognize LUKS containers and mdadm arrays like the older partitioner did. 

That other Bug Report (later on) says that Users should 'just' use the autoinstall scripts as a work-around... But that ignores the problem with the new partitioner completely. Using those scripts is beyond the common User skill-set that we recommend solutions for here. I've tested those. They work (now). I've filed bugs to get & keep those working... But those are honestly targeted towards the skill-sets of Systems Admins, not the average Ubuntu User.

Heck. I have Systems Admins telling me this issue is a deal breaker for their infrastructure. I hate hearing that. It could be so much simpler if this was working again.

---

### Post by gezzer2 on 2024-05-09
@ MAFoElffen
i have also just posted on your bug report. cheers ..

---

### Post by #&amp;thj^% on 2024-05-09
> **MAFoElffen said:**
> 

That other Bug Report (later on) says that Users should 'just' use the autoinstall scripts as a work-around... But that ignores the problem with the new partitioner completely. Using those scripts is beyond the common User skill-set that we recommend solutions for here. I've tested those. They work (now). I've filed bugs to get & keep those working... But those are honestly targeted towards the skill-sets of Systems Admins, not the average Ubuntu User.

Heck. I have Systems Admins telling me**_ this issue is a deal breaker for their infrastructure_**. I hate hearing that. It could be so much simpler if this was working again.
+1 I PM'ed you on those scripts.
I've added to it as well. (Bug Report)

---

