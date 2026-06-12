---
title: "Error after upgrading to 17.10 from 16.04"
date: 2018-01-02
forum: Installation &amp; Upgrades
---

### Post by Poleh on 2018-01-02
Hi Folks

gnarly problem, which I am stuck with and would appreciate any help that you can provide.

**Background**
I manage my Mom's System76 box remotely and have done for quite a few years. Works fine, TeamViewer is my friend and it's been pretty rock solid.

Over the weekend, I decided to upgrade her to 17.10 from 16.04 - used the command line and did a full update before a release upgrade. All *seemed *to go well until at some point (I guess on first reboot) I couldn't get back into the system via TeamViewer - always a warning flag on my end that something has gone wrong. Apparently the "screen was black" and not responding - this after many hours after the upgrade was started.

The catch is, her machine is in Africa, and there's a very real chance there may have been a power failure at some point.

**The Error**
Right now, when she boots the machine, there's a brief flash of purple boot screen, and then we are left with the following message:
```
Scanning for Btrfs filesystems
Ubuntu: clean, 261754/7036928 files, 4040009/28124928 blocks
[ 494.721506] usb 3-6: device not accepting address 8, error -71
```

**My challenge**
Diagnosing this remotely without access is tough, so I am reduced to hosting a phone based hangouts video call with my Mom pointing the camera at the screen so I can see what's going on :) #funtimes

I have researched this error message, and came up with very little that was applicable on initial investigation. It's also important to note that I am also passably capable with Ubuntu and Linux in general - reasonably comfy on the command-line, but not deeply knowledgeable.

I am looking for suggestions on next steps to get the machine booting to a point where I can either remote SSH in, or get a GUI going with TeamViewer so I can clean up further. Any and all help is greatly appreciated.

---

### Post by DuckHook on 2018-01-02
Remote administration is a bad idea on top of a GUI. Far too many additional points of failure. Teamviewer is not even native to Linux, but a Windows port that often misbehaves. Then you went and did a full release-upgrade *remotely, across continents*, which is sort of like saying: since I've dodged many bullets up to now and even the occasional cannonball, I think I'll try dodging a nuclear missile this time.

Don't. Do. This.

As for unscrambling this egg:

[LIST=1]
[*]Is your Mom's important data backed up? That's the first thing I would do if I were her.
[*]How knowledgeable is your Mom? The least painful solution may be to simply have her reinstall, then restore data from backups.
[*]Why are you going to Artful? Is there some Xenial limitation that she can't live with?
[*]What odd things have been done to this machine? *btrfs* is not part of a default Xenial install. Please list all of your customizations (i.e. additions to/departures from a default install).
[*]Power failures are ubiquitous in some parts of Africa. Is she on battery backup when updating/upgrading? Especially when release-upgrading?
[*]Does your Mom have access to another computer on which she can create a LiveUSB? The idea would be to run a live session and at least be able to backup. This also allows her to chroot into the broken machine.
[/LIST]
I'll be brutally candid:

Your chances of successfully rescuing a failed release upgrade halfway across the world are very poor. Rescuing regular upgrades or the occasional *dpkg* error is not too bad, but release upgrades are a completely different kettle of fish. As my sig tagline says: they are heart, lung and brain transplants. Since you suspect that a power failure occurred during the process… well… the outlook is very bad.

Your strategy of getting to a SSH session is likewise not practical. You need a good working install to get SSH working. You are therefore caught in a chicken-or-egg situation. I've already given my thoughts on using Teamviewer to administer a remote box. In general, RDCs (and I would recommend something more robust with Linux than Teamviewer) are great for collaborations, interactive teaching/learning, conferencing, but it's highly inadvisable for administration.

From now on, consider using SSH exclusively for all management tasks, disable passwords and set up rsa key pairs for security, and use either *screen* or *tmux* so that a dropped session does not lead to breakage or corruption.

At this point, the best course of action that I can see is to reinstall a pristine system and restore all data from backups. Even chrooting into a broken install is not practical, especially for a general user like your Mom, unfamiliar with the CLI, listening to directions over a hangouts connection across continents.

---

### Post by Poleh on 2018-01-02
I appreciate the response, and will stick to the topic at hand which is looking to solve for the problem. I'll happily get into lectures on my behaviour/life choices/risk posture once she's back online :)

In order of your questions below:
[LIST=1]
[*]Data is backed up.
[*]Not at all, hence the need to have remote administration tools.
[*]No particular reason, I upgrade her when I go through my own upgrade cycles. Have done so for years.
[*]Nothing odd that we've done to the machine. Vanilla installation, a few apps loaded like TeamViewer and Skype. Certainly no custom file-systems etc.
[*]Battery backup failed - we unfortunately found out the hard way.
[*]We do have another computer, and the LiveUSB option with backup and full re-install is my last resort, and am comfortable managing through that myself.
[/LIST]

> **DuckHook said:**
> 

[LIST=1]
[*]Is your Mom's important data backed up? That's the first thing I would do if I were her.
[*]How knowledgeable is your Mom? The least painful solution may be to simply have her reinstall, then restore data from backups.
[*]Why are you going to Artful? Is there some Xenial limitation that she can't live with?
[*]What odd things have been done to this machine? *btrfs* is not part of a default Xenial install. Please list all of your customizations (i.e. additions to/departures from a default install).
[*]Power failures are ubiquitous in some parts of Africa. Is she on battery backup when updating/upgrading? Especially when release-upgrading?
[*]Does your Mom have access to another computer on which she can create a LiveUSB? The idea would be to run a live session and at least be able to backup. This also allows her to chroot into the broken machine.
[/LIST]


---

### Post by DuckHook on 2018-01-02
> **Poleh said:**
> …the topic at hand which is looking to solve for the problem. I'll happily get into lectures on my behaviour/life choices/risk posture once she's back online :)
We deal with lots of new users on these forums who do things a certain way because they drag over old habits from commercial OSes or don't know any better. It looks like you are a power user who knows the risks and have weighed your options. All good then.

Well, the approach I would commonly recommend when things get this bad is to chroot into the broken install, and try to complete the process. But first, it takes a lot of detective work to figure out where the process has stalled/is broken. This depends crucially on when (where in the process) the power failure happened.

Examples:

[list=1]
[*]Is dpkg corrupted? If so, you might be able fo fix it.
[*]Is it just GRUB? Or badly generated initramfs? Then you can try generating new ones.
[*]Corrupted download? Those are tough to fix because you don't know where the problem is.
[*]The worst case is if the new system is only half-installed. You are left with a mix of old, new and missing. Untangling a mess like that is pretty much impossible even if the computer were sitting right in front of you. I wouldn't know where to start on a remote box with a newbie trying to follow command line instructions.
[/list]

The following is a pretty good short tutorial on chrooting into a failed update/upgrade and trying to complete the process: [https://aaronbonner.io/post/21103731114/chroot-into-a-broken-linux-install](https://aaronbonner.io/post/21103731114/chroot-into-a-broken-linux-install)

Note that a failed update/upgrade is a far cry from a failed do-release-upgrade. However, most attempts to fix things will start from such a chroot environment.

---

