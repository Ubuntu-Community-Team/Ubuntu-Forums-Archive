---
title: "Updating Ubuntu 24.04 LTS from Ubuntu 22.04 LTS"
date: 2024-04-27
forum: Installation &amp; Upgrades
---

### Post by mrtkntt53 on 2024-04-27
Hello everyone, hope that all of you are well.
I wanted to use upgrade my Ubuntu to its new version, but I learned that I have to wait to upgrade it until August update of Ubuntu 24.04 LTS.
But are there any other method to upgrade?
I also used sudo do-release-upgrade -d , but it says there is no upgrade for Ubuntu LTS.
Is it a problem?
And is it worth to upgrade it?
Thanks for now.

---

### Post by deadflowr on 2024-04-27
Wait.
I don't even think they've opened the channel for any upgrades yet.

---

### Post by mrtkntt53 on 2024-04-27
Thank you for your answer. So, there is no way to upgrade. Then, I will wait for the upgrade release.

---

### Post by ajgreeny on 2024-04-27
Potentially risky, and the online update from 23.10 or 22.04 to the new 24.04 is not yet available by normal means. It will probably be available when the first point version (24.04.1) of noble is released

However, this is Linux so it is certainly not impossible, but before you try to do anything in order to carry out this version upgrade make sure that you have full backups of everything that is important to you, ie all the files and folders including the hidden ones (starting with . and not visible by default in your /home)

If you decide it is worth the risk there were two ways to try this though I have never used either in Ubuntu but have done one method in other distros particularly Debian in the past.

1)
You can try a "dirty" install where you run the installer using manual partitioning to choose the same partitions as used in the old version. Normally you ensure that the old partitions are formatted before the new install happens but in this "dirty" install method you do not format but just let the installer upgrade everything as it goes.
This is the method I have never used so can say nothing more.

2)
The second method is normally done simply be editing the ***/etc/apt/sources.list*** file and changing the codename for the version, ie replace jammy with noble in the file.
However, noble has moved the sources.list file to ***/etc/apt/sources.list.d/ubuntu.sources*** and changed its format so this method may not work now.

Personally I would not bother to try either method yet and would either clean reinstall after backing up my personal files so they can be restored after the install or stay with 22.04.

Your choice; your risk!
Whatever you decide, BACKUP! BACKUP! BACKUP!!

---

### Post by #&amp;thj^% on 2024-04-27
> **ajgreeny said:**
> 
Personally I would not bother to try either method yet and would either clean reinstall after backing up my personal files so they can be restored after the install or stay with 22.04.

Your choice; your risk!
Whatever you decide, BACKUP! BACKUP! BACKUP!!

+1 Wise to wait....

---

### Post by mrtkntt53 on 2024-04-27
Thank you so much for the message, so I understand the methods and their risks right now. So, I will stay with 22.04 LTS. I will wait for 24.04.1 LTS.

---

### Post by hal8000b on 2024-04-28
Its probably wise to wait as the forum moderator stated.

However I think the installer is broken in Ubuntu 24.04 if you have multiple hard drives, don't have a Motherboard with UEFI BIOS or are using disk encryption.
When trying to install, open a terminal and watch the processes using 'top' or 'ps aux'
In my case 3 times the subiquity installer failed on block probe and no other message was given.

For me, I downloaded Ubuntu 22.04 and used the installer, Casper ? or whatever the script is got a lot further and installed the system.
Most of the instructions on the internet are wrong.
To upgrade to 24.04 from 22.04 you have to edit
/etc/update-manager-release upgrades

and change the prompt to 'normal'
Then running
sudo do-release-upgrade  -d
will find a development realease 23.10 Mantic.
You update Mantic and run the same command again and this gets you to Ubuntu 24.04

In my case it was a fresh install, nothing to back up, but install takes longer because each install package
is checked against dependencies.  The last step will be to remove redundant packages but have to say
that so-release-upgrade worked flawlessly,   much better than the installer.

In time the installer may change and accommodate multiple hard drives etc , but this is the first time an Ubuntu OS has failed to install
for me since Ubuntu 4,10 (Warty) from memory.

---

### Post by deadflowr on 2024-04-28
> To upgrade to 24.04 from 22.04 you have to edit
/etc/update-manager-release upgrades

and change the prompt to 'normal'
Then running
sudo do-release-upgrade -d
will find a development realease 23.10 Mantic.
No -d needed to upgrade from 22.04 to 23.10 as 23.10 is considered the next available release already.
Since they downgraded the support from 18 months to 9 months for interim releases they've updated the mechanism of upgrading lts releases to the next supported release available.
So the only releases between 22.04 and 24.04 that is currently still supported is 23.10.

You would need to use the -d flag, however, to upgrade from 23.10 to 24.04.
But as posted, there be dragons right now. So best to keep waiting.

---

### Post by superian on 2024-05-02
> **ajgreeny said:**
> However, noble has moved the sources.list file to ***/etc/apt/sources.list.d/ubuntu.sources*** and changed its format so this method may not work now.

All I want for my birthday is for distros that are ultimately based on Debian to stop messing around with the Debian package manager way of doing things.

---

### Post by ajgreeny on 2024-05-02
> **superian said:**
> All I want for my birthday is for distros that are ultimately based on Debian to stop messing around with the Debian package manager way of doing things.
But don't forget this is open source, so any users or other distro developers can make any changes they want to and move away from the default Debian versions.

---

### Post by superian on 2024-05-03
"Yeah, yeah, but your devs were so preoccupied with whether or not they  could that they didn't stop to think if they should", as Jeff Goldblum  so nearly said.

---

### Post by peyre on 2024-05-03
This is ridiculous.  I understand waiting a few days for an upgrade after the .iso comes out, but three and a half months?  That's more than halfway to the next release.

---

### Post by deadflowr on 2024-05-03
> **superian said:**
> All I want for my birthday is for distros that are ultimately based on Debian to stop messing around with the Debian package manager way of doing things.

This is a debian package manager change.
Upstream from debian.
Ubuntu simply has decided to use it.
Old Sources will still work, for a while at least.

---

