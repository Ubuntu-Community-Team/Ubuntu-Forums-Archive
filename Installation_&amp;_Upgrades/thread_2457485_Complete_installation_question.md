---
title: "Complete installation question"
date: 2021-02-03
forum: Installation &amp; Upgrades
---

### Post by jmichaels29 on 2021-02-03
I gave a command line instruction to upgrade my Aunt's computer, but had to leave. So I told her to leave it on a couple hours. She probably turned it off after a few hours.
Is there a chance that it would have asked her a question (like to delete unneeded files) or other question, and her turning it off messed up the computer?

---

### Post by Impavidus on 2021-02-03
It can ask questions and turning it off can mess things up. Just running a```
sudo apt full-upgrade
sudo apt autoremove
```may clean it up. If not, it may take quite some effort to clean it up.

---

### Post by grahammechanical on 2021-02-03
It all depends on what version we are upgrading from and what version we are upgrading to.

I started with Ubuntu 18.04 that had both Gnome 3 shell and Unity 7 installed. I was asked to approve the removal of obsolete packages. Unity 7 was removed. As I was also using the Light Display Manager (LightDM) for the login screen I was asked to configure the Gnome Display Manager (GDM).

So, yes an upgrade sometimes, perhaps usually, asks for user input. I expect similar questions will be asked when upgrading from 20.04 (LTS) to 22.04 (LTS). The upgrade process to 22.04 may ask us to approve greater security for our home folder and whether we want to switch to using a Wayland display server if we are not already using one. I am just guessing.

[https://www.omgubuntu.co.uk/2021/01/private-home-directory-in-ubuntu-21-04](https://www.omgubuntu.co.uk/2021/01/private-home-directory-in-ubuntu-21-04)

[https://www.omgubuntu.co.uk/2021/01/ubuntu-21-04-will-use-wayland-by-default](https://www.omgubuntu.co.uk/2021/01/ubuntu-21-04-will-use-wayland-by-default)

Regards

---

### Post by TheFu on 2021-02-03
System files that are not the default will prompt for change confirmation. Depending the how many config files were changed, this could stop an upgrade at diffferent points of the process.

---

### Post by jmichaels29 on 2021-02-03
> **Impavidus said:**
> It can ask questions and turning it off can mess things up. Just running a```
sudo apt ful-upgrade
sudo apt autoremove
```may clean it up. If not, it may take quite some effort to clean it up.

Thanks to the 3 of you that replied.  I just talked to her on the phone, and she said she was using the computer today with no problems.

Perhaps I will still run those 2 sudo commands, next time I'm down there, just to make sure all is ok.

I was attempting to update from 16.04 to the latest version.  I was following directions to do this:
 sudo apt update && sudo apt upgrade
  sudo do-release-upgrade

Was hoping to get an LTS upgrade

---

### Post by Impavidus on 2021-02-04
Note that I fixed a typo in the command above. It's full-upgrade, not ful-upgrade.

From a PM:
[QUOTE=jmichaels29]When running those 2 sudo commands.  How long do you think it will take.[/QUOTE]
Better ask such things on the forum. Others may respond faster.

Now way to tell. It will show a list of packages that will be upgraded. The longer the list, the longer it will take. A few seconds per package, on average. Or it could take forever, if there's some problem.

"The latest version" is ambiguous. Do you mean the latest LTS version (20.04), the latest interim version (20.10) or even the current development version? As you're maintaining this system at a distance and are not the primary user, best to use the LTS version. But even then, 16.04 to 20.04 is a double upgrade, going via 18.04.

---

### Post by yancek on 2021-02-04
I would think it would be much simpler to shrink the partition on which she currently has Ubuntu and install the latest LTS on a newly created partition.  This woulds likely not  take more than 30 minutes and if something goes wrong, she would still have the old system.  Obviously, you would need to know the process, do some research beforehand.

The last time I did a full upgrade was from 14.04 to 16.04 and that took 3+ hours with average hardware and average internet connection.  The upgrade process in this case will require a total upgrade to 18.04 and then an additional total upgrade to 20.04.  If you lose power or have a brownout during the process, major problems and this is something the user has absolutely no control over..

---

### Post by TheFu on 2021-02-04
> I was attempting to update from 16.04 to the latest version. I was following directions to do this:
sudo apt update && sudo apt upgrade
sudo do-release-upgrade

So, I just did multiple upgrades from 16.04 --> 18.04 in the last month.
A few comments.
```
sudo apt update # good start. Required.
sudo apt full-upgrade # this is needed to get updated kernels and remove out-of-date packages which have been replaced. 
# For normal patching, no need for sudo apt upgrade if you use full-upgrade.  One or the other, depending on your 
# specific needs and stability requirements.
# If a new kernel or new libc* gets installed, 
sudo reboot
```

Now try the 
```
sudo do-release-upgrade
```
On my 16.04 systems, this didn't do anything, but I remove a bunch of unwanted Canonical apt-nag packages, so it may work on your system.  If it doesn't, then you get to manually edit all the sources in /etc/apt/ and rename the PPA files so those don't break on the new OS.

I've done this over ssh to remote systems many times.

As for the time needed, sometimes it is 1 hour and sometimes it is 3+ hrs.  On a system last week, the release upgrade ran out of disk and failed. Think it had 5G free on / before starting.  I'd been careful to ensure /boot/ (I use LVM), had sufficient storage, but not /.  The root LV was full and I had to make some more room on other LVs so I could extend the root LV and finish.  Even then, some of the post-install cleanup tasks refused to run due to lack of space, so I deleted an old 10G test LV and added that back to the root LV. Once everything was done, 
```
$ df /
Filesystem                  Size  Used Avail Use% Mounted on
/dev/mapper/hadar--vg-root   32G   18G   13G  58% /
```
This isn't a desktop system, so I wasn't looking forward to setting up 15 LVs and reconfiguring 50 server processes after a full install. As you can see, there is plenty of extra space now, normally, it would only have 20G on a 16.04 system.  18.04 and 20.04 are hogs and need more storage (not including swap).  Looks like 30G for / is now the safer amount, assuming HOME and swap are in other LVs.  
Plus, I'm not 100% certain how to do some non-trivial network things under netplan, but with an upgrade, the interfaces file is retained and pulled forward nicely, unmolested.

On a typical desktop, if you have 30G free, it would make sense to just do a fresh install into a new partition/LV. That would be 10-20 minutes.  Then you can use typical backup/restore techniques to reload the same old applications that were previously on the old system.

---

### Post by jmichaels29 on 2021-02-04
> **Impavidus said:**
> Note that I fixed a typo in the command above. It's full-upgrade, not ful-upgrade.

From a PM:

Better ask such things on the forum. Others may respond faster.

Now way to tell. It will show a list of packages that will be upgraded. The longer the list, the longer it will take. A few seconds per package, on average. Or it could take forever, if there's some problem.

"The latest version" is ambiguous. Do you mean the latest LTS version (20.04), the latest interim version (20.10) or even the current development version? As you're maintaining this system at a distance and are not the primary user, best to use the LTS version. But even then, 16.04 to 20.04 is a double upgrade, going via 18.04.

I was attempting to get to the latest LTS version of 20.04
Which command line is best for this (the sofware updater app doesn't work for some reason).

---

### Post by TheFu on 2021-02-04
To get from 16.04 to 20.04, there are 2 upgrades necessary. That's a bunch of risk for a single week.

---

### Post by Impavidus on 2021-02-04
> **jmichaels29 said:**
> I was attempting to get to the latest LTS version of 20.04
Which command line is best for this (the sofware updater app doesn't work for some reason).

Depends on where you're now. To go from 16.04 to 20.04, the best way is (I think) a fresh install, keeping your home directory (works best if it's in a separate partition). If the system is already on 18.04, you could try another release upgrade, but I'd first make sure that the 18.04 system is fully functional. You can start the upgrade when the package manager is in a consistent state and all available upgrades for 18.04 have been installed. If the software updater doesn't work, that's something you should fix first, even if you intent to stay on the current version, because it will also block security upgrades.

The fast route to 20.04 is a fresh install, as you don't have to fix things first. But if you want to fix things, try these commands:```
sudo apt update
sudo apt full-upgrade
```Show the output of the first command. If the second produces a lot of output, we don't need all of it. Just the main bits if there's some error.

FYI, my last upgrade was last month, when I went from 20.04 to 20.10. It was 50 minutes work, including an 8 minute download (at 5 MB/s). All went well, but going just one release forward is more reliable than going four or even eight.

---

### Post by rsteinmetz70112 on 2021-02-06
For what it's worth I did an upgrade from 18.04 to 20.04 yesterday afternoon. It took about three and a half hours and asked a number of questions all of them about keeping or replacing old configuration files.
The only problem I had was the upgraded computer forgot how to access the Internet, that is DNS stopped working. Asking here I was able to fix it this morning.

---

### Post by TheFu on 2021-02-06
I did another 16.04 --> 18.04 upgrade today. Took about 45 minutes for the core stuff. 8th-gen Core i5 in an average laptop with SATA SSD. Was asked about keeping old config files about 10 times.  login.conf, journalctl.conf, ntp.conf, /etc/default/grub, stuff like that. I suspect average users wouldn't have modified those files.

Then I went through to clean up all the left over 16.04 packages and broke some things.
[LIST]
[*]DNS got broke.
[*]LUKS worked before and after.
[*]My primary yubikey w/ challenge-response didn't work to unlock the LUKS volumes. A secondary yubikey without C-R did work.
[*]Other issues were self-inflicted during my cleanup of old packages from 16.04. I removed all input packages, so the mouse and keyboards didn't work on the device. That was funny. Had to ssh in from a different system and install the HWE-kernel modules for the input packages - which fixed it.
[/LIST]
Need just a few more minutes. Also moved to the HWE kernel, 5.4, while I was at it.

---

### Post by jmichaels29 on 2021-02-10
Deleted

---

### Post by coffeecat on 2021-02-11
@jmichaels29, you edited the first post to read "deleted". I have restored the original text. Please do not delete OPs like that; it makes a nonsense of the whole thread. Thanks.

---

### Post by jmichaels29 on 2021-02-11
Oops, sorry.  Meant to edit the last post to say deleted.

---

