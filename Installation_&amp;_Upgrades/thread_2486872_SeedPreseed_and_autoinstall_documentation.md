---
title: "Seed/Preseed and autoinstall documentation"
date: 2023-05-15
forum: Installation &amp; Upgrades
---

### Post by faldrich on 2023-05-15
I'm new-ish to Ubuntu's seed method.  We are using Focal, and I want to understand the seed file creation process.   I searched for documentation, found broken/missing pages on Ubuntu's official site, others there are example seed files -- but no tutorial about order of operations, etc. etc.   

I'm also puzzled by the new autoinstall (cloud-init) -- the docs seem geared toward using a VM in/from the cloud.   We are using real-iron systems and some VMs.  It's not clear to me whether the new autoinstall process can/should replace the seed procedure, as per above.   It's easy to get lost in this.

Might anyone point to some useful documentation on creating a seed file.   Note: I don't believe we want a pre-seed image, not yet anyway.   We have a central purpose to the uniform installation, we also use Puppet/Foreman for a good many configuration elements.

We are forming a seed file for Focal which will include FIPS and a bunch of other things.


Thanks in advance....

---

### Post by MAFoElffen on 2023-05-15
seed/reseed is old verbiage, and in reality is dead. Gone with the old debian-installer, which is pre-20.04. Since then is the Live-Installer.

From what I have done... With the initial base install- partitioning, installing the base system, the Live-installer scripts... But it seems to be challenged on installing extra applications... Which I now install with cloud-init.

As I remember, when the Live Installer rolled out, In the Server Section, there was a running thread-- on what worked, not worked, and work-around's for the Live Installer and scripts for it. Search on threads started by LHammonds, and the Live Installer...

Found it: [https://ubuntuforums.org/showthread.php?t=2443047](https://ubuntuforums.org/showthread.php?t=2443047)

This seems to be changing "again" for the next LTS release. Lunar uses a new SNAP ubuntu-installer, which even for user creation and user settings, that is done with cloud-init during the first boot after the base system is installed.

I have a personal feeling that there will be more changes coming. I can foresee a lot of support challenges and new documentation on installation scripts when that LTS version rolls out.

So... My recommendation would be-- I would concentrate on cloud-init.

---

### Post by and-account on 2023-06-22
As far as I understood it's using only config syntax from Cloud Init. Subiquity is using same syntax and that's all at the moment of writing. If I'm not right correct me please.

Concerning preceed for Ubiquity: Debian's features often do not work in a way as it described in Debian's doc as features were modified for Ubuntu. There is no valuable documentation on it. Because of it it's not convenient for use in context of the installer. Certain time it's easier to use two hooks. Early commands hook is launched directly before storage partitioning is going to be applied. And on install finish hook is launched after Ubiquity done it's job. Hooks are documented on the Web.

However, Ubiquity with Python is going out of the game. Google's Flutter+Dart app as desktop installer plus Subiquity with Python are instead.

You may need to study snaps details in order to understand how do they are installed. It's not easy. They can be injected into a file system, but it is not a straightforward process, as it has been designed to work under Systemd daemon strictly with pid=1. It is not preventing injection of files into an FS, of course, but no easy way to do a preinstall with a package manager. Thus, if it's acceptable, software may be added during first boot, which may need an extra job.

---

