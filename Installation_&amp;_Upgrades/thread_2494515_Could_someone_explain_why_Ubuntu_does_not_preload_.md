---
title: "Could someone explain why Ubuntu does not preload Snaps"
date: 2024-01-18
forum: Installation &amp; Upgrades
---

### Post by 7-webmaster on 2024-01-18
This is a suggestion for product improvement.

I understand the support issues which have induced Canonical to migrate to Snaps for packaging services.  However some of the Snaps are hundreds of megabytes in size and they are not downloaded from the repository until a request is made to update the service.  This is particularly an issue with packages which are often in use almost continuously, like Firefox.  Why are the packages not downloaded in the background so that I can just shut down the application for a brief time, upgrade the Snap, and then resume my work?  Why must I wait while hundreds of megabytes of data are downloaded into my computer?  Also I have three computers in my office.  Why must I perform that download three times when all three computers are connected to the same Ethernet LAN?

---

### Post by TheFu on 2024-01-19
> **7-webmaster said:**
> This is a suggestion for product improvement.
 

Nobody here works for Canonical, so this post won't get to anyone with any ability to make changes.
Canonical employees are either on Discord or reading Landscape bugs.  Use one of those methods to submit a "bug report".

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)


You don't need to manually download anything once a snap package is installed.  That will happen automatically, whether you want it or not.  I've only been able to delay snap updates to a specific day of the week, but but short of firewall blocks, haven't found any way to actually prevent updates.  

I've also tried to prevent major version upgrades in the nextcloud snap package multiple times, but this is also ignored and not just minor, but major upgrades keep getting installed.  Most of the time, this hasn't been a problem, but about 1-2 times a year, the primary reason for my nextcloud instance, which is as an RSS news reader, gets totally screwed and breaks.  Snaps can only be rolled back within the same major release, so if the breakage happened due to an major release, which seems to be the only time it breaks, I'm screwed.
I really wish that nextcloud snap would no update if any of the add-on applications don't specifically say they support the new release. Sigh. It will never happen, but I can dream.

---

### Post by MAFoElffen on 2024-01-19
@TheFu --- If I am reading his post right... He is talking about the update process of Snap Applications.

Which to me, in how I read what you wrote: No matter what an "Update Type" is... Whether that is APT, Snap, Flatpak, whatever...

If you have 3 computers at your home, yes you are going to have to download updates 3 times, one for each computer, unless... (Notes below.) That is no difference there with any or whatever type of application or system updates. Basically they are all the same under the covers. Then after an update, either restarting the application, or rebooting the computer if a system update, for those installed updates to apply. That is true for any OS, not just Ubuntu, any other Linux, BSD, Windows, etc. That is just the reality of applying updates or patches.

(The below noted exceptions)
Unless: You setup a local APT Cache (such as apt-cache-ng) or Local Repo (such as apt-mirror) where you setup a web server on one computer, to download your updates to, then point your other computer to it, so that the update process only downloads "externally" to your local network once.

Most users are not going to set that up. There's a cost, were that cost/benefit fallover has to make that worth it to them.

Then there is Livepatch is a client side software that runs on individual machines and periodically checks for the availability of kernel patches. Once a patch becomes available, it is downloaded, verified and applied to the current kernel. It allows the kernel to be patched without having to reboot. It sounds like a good thing right? What I don't like about that, is that until the system actually reboots, the kernel changes are running in cache, which adds "some things" to the workload. You have less maintenance downtime, but there is a cost.

---

### Post by TheFu on 2024-01-19
My understanding is that snap packages - .snap files - can be downloaded once then installed manually across hundreds of systems.  Look in /var/lib/snapd/snaps for the snap packages.

For example, 
```
/var/lib/snapd/snaps$ sudo file core20_2015.snap 
core20_[COLOR="#FF0000"]2015[/COLOR].snap: Squashfs filesystem, little endian, version 1024.0, compressed, 3918684743046004736 bytes, -684851200 inodes, blocksize: 512 bytes, created: Tue Jan 10 12:49:40 2096


$ snap list
Name    Version        Rev    Tracking       Publisher   Notes
bare    1.0            5      latest/stable  canonical&#10003;  base
core20  20230801       [COLOR="#FF0000"]2015[/COLOR]   latest/stable  canonical&#10003;  base

```

---

### Post by ian-weisser on 2024-01-20
> **7-webmaster said:**
>  Why are the packages not downloaded in the background so that I can just shut down the application for a brief time, upgrade the Snap, and then resume my work?  Why must I wait while hundreds of megabytes of data are downloaded into my computer?

Thanks for your suggestion.
It was implemented already in snapd v 2.59, March 2023.

See [https://github.com/snapcore/snapd/releases/tag/2.59.1](https://github.com/snapcore/snapd/releases/tag/2.59.1) :
> - Pre-download of snaps ready for refresh and automatic refresh of the snap when all apps are closed

If you are using Ubuntu 23.04 or newer, you should see the feature in action. If using a newer release but still seeing the older behavior, please file a proper bug report in the proper place.

---

### Post by cigtoxdoc on 2024-01-23
Here is what I am getting with 23.10

john@john-Precision-7720:/var/lib/snapd/snaps$ snap list
Name               Version          Rev    Tracking          Publisher   Notes
bare               1.0              5      latest/stable     canonical&#10003;  base
core22             20231123         1033   latest/stable     canonical&#10003;  base
firefox            121.0.1-1        3626   latest/stable/&#8230;   mozilla&#10003;    -
gnome-42-2204      0+git.ff35a85    141    latest/stable/&#8230;   canonical&#10003;  -
gtk-common-themes  0.1-81-g442e511  1535   latest/stable/&#8230;   canonical&#10003;  -
libreoffice        24.2.0.2         304    latest/candidate  canonical&#10003;  -
snapd              2.61.1           20671  latest/stable     canonical&#10003;  snapd

Is this what it should look like?

John

---

### Post by TheFu on 2024-01-23
> **cigtoxdoc said:**
>  
Is this what it should look like?

It should like like you want, based on your decisions about snaps.

Someone else would have to answer if that list is the default or not.  I remove as many snaps as I can.

---

