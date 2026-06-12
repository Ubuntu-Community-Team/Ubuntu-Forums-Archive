---
title: "Problems installing 18.04.4 on a Dell Latitude 7400"
date: 2020-05-18
forum: Installation &amp; Upgrades
---

### Post by Martin_Kuemmel on 2020-05-18
I bought a Dell Latitude 7400 with pre-installed Ubuntu 18.04.4 in January.

The first boot is good, but as soon as a "Software Update" updates software and kernel, there are problems. It does **not  **boot anymore reliably and does not wake up from hibernation reliably. When booting, it stops with a flat reddish screen. When booting from the grub selection menu, it prints "Loading initial ramdisk" and that was it.

The behaviour seems to be associated with the update of the kernel and/or grub.

I tried various ways to boot the machine, none is reliable. It may boot a couple of times, but then not for a couple of days.

Dell says the machine is okay and the internal hardware tests do not find any issues.

I also tried other Linux flavours such as Suse and Fedora, it is always the same: It boots until the software is updated, then it is a lottery game whether it wakes up or boots.

The only way to work with it might be to inhibit any kernel and grub update (have not tried for more than a couple of days though, and updating is important for security and other reasons).

Any ideas?

---

### Post by malangaman on 2020-05-18
I had a machine behave in a similar fashion. These links helped me:
[https://askubuntu.com/questions/1174833/disable-kernel-auto-updates-in-ubuntu-18-04-cli-only](https://askubuntu.com/questions/1174833/disable-kernel-auto-updates-in-ubuntu-18-04-cli-only)
[https://hollysydney.com/article/prevent-ubuntu-upgrading-kernel](https://hollysydney.com/article/prevent-ubuntu-upgrading-kernel)
I also use grub customizer:
[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

---

### Post by oldfred on 2020-05-18
Not sure this will help, but it does document your system.

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

I might not use grub customizer as the Dell version of grub is a bit customized and grub customizer overwrites standard grub and adds its own proxy files, so you may lose any Dell specific grub entries like restore system.

---

### Post by Martin_Kuemmel on 2020-05-19
Thanks for the replies!

* I installed and ran boot-repair;
* I did **not** do the auto-repair (as suggested);

The report is here:
[http://paste.ubuntu.com/p/qDHPYxmMKh/](http://paste.ubuntu.com/p/qDHPYxmMKh/)

Any clues what is wrong?

---

### Post by oldfred on 2020-05-19
Some systems do not recover from hibernation well. But sleep should work.
Often faster just to boot, especially now with SSDs.

Not sure why nvme0n1p1 is FAT16. Was it FAT32 before?
But FAT16 should work.

It looks like second partition p2, is FAT32 and has a grub to boot an ubuntu ISO to restore your original configuration.

Your ESP has old entries for Fedora & OpenSuse. You can delete with efibootmgr -b command.
See 
man efibootmgr

You  still show OEM kernels. I thought with OEM installs, first boot is to create user & password like you do with a new install. Did you do that?

What video card/chip?

What sources does it use. Post this, long enough to use Code Tags # in Forum's advanced editor.
cat /etc/apt/sources.list; for X in /etc/apt/sources.list.d/*; do echo; echo; echo "** $X:"; echo; cat $X; done

---

### Post by Martin_Kuemmel on 2020-05-20
> Not sure why nvme0n1p1 is FAT16. Was it FAT32 before?
But FAT16 should work.

I did not actively change that.

> It looks like second partition p2, is FAT32 and has a grub to boot an ubuntu ISO to restore your original configuration.
Your ESP has old entries for Fedora & OpenSuse. You can delete with efibootmgr -b command.
See 
man efibootmgr

I deleted those entries. The new repair report is here:
[http://paste.ubuntu.com/p/9GqBwtW7sd/](http://paste.ubuntu.com/p/9GqBwtW7sd/)

> You  still show OEM kernels. I thought with OEM installs, first boot is to create user & password like you do with a new install. Did you do that?

It was always a "normal" install process, and on first boot I created a user and pwd.

> What video card/chip?
$ lspci | grep -i --color 'vga\|3d\|2d':
 00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (Whiskey Lake) (rev 02)
 

> What sources does it use. Post this, long enough to use Code Tags # in Forum's advanced editor.
cat /etc/apt/sources.list; for X in /etc/apt/sources.list.d/*; do echo; echo; echo "** $X:"; echo; cat $X; done
Not sure whether I am doing the right thing. I execute that command, and the result is:
```
** /etc/apt/sources.list.d/bionic-dell.list:

deb http://dell.archive.canonical.com/updates/ bionic-dell public
# deb-src http://dell.archive.canonical.com/updates/ bionic-dell public


** /etc/apt/sources.list.d/bionic-dell.list.save:

deb http://dell.archive.canonical.com/updates/ bionic-dell public
# deb-src http://dell.archive.canonical.com/updates/ bionic-dell public


** /etc/apt/sources.list.d/bionic-dell-merion.list:

deb http://dell.archive.canonical.com/updates/ bionic-dell-merion public
# deb-src http://dell.archive.canonical.com/updates/ bionic-dell-merion public


** /etc/apt/sources.list.d/bionic-dell-merion.list.save:

deb http://dell.archive.canonical.com/updates/ bionic-dell-merion public
# deb-src http://dell.archive.canonical.com/updates/ bionic-dell-merion public


** /etc/apt/sources.list.d/bionic-dell-service.list:

deb http://dell.archive.canonical.com/updates/ bionic-dell-service public
# deb-src http://dell.archive.canonical.com/updates/ bionic-dell-service public


** /etc/apt/sources.list.d/bionic-dell-service.list.save:

deb http://dell.archive.canonical.com/updates/ bionic-dell-service public
# deb-src http://dell.archive.canonical.com/updates/ bionic-dell-service public


** /etc/apt/sources.list.d/bionic-oem.list:

deb http://oem.archive.canonical.com/updates/ bionic-oem public
# deb-src http://oem.archive.canonical.com/updates/ bionic-oem public


** /etc/apt/sources.list.d/bionic-oem.list.save:

deb http://oem.archive.canonical.com/updates/ bionic-oem public
# deb-src http://oem.archive.canonical.com/updates/ bionic-oem public


** /etc/apt/sources.list.d/google-chrome.list:

### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main


** /etc/apt/sources.list.d/google-chrome.list.save:

### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main


** /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-bionic.list:

deb http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu bionic main
# deb-src http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu bionic main


** /etc/apt/sources.list.d/bionic-dell.list:

deb http://dell.archive.canonical.com/updates/ bionic-dell public
# deb-src http://dell.archive.canonical.com/updates/ bionic-dell public


** /etc/apt/sources.list.d/bionic-dell.list.save:

deb http://dell.archive.canonical.com/updates/ bionic-dell public
# deb-src http://dell.archive.canonical.com/updates/ bionic-dell public


** /etc/apt/sources.list.d/bionic-dell-merion.list:

deb http://dell.archive.canonical.com/updates/ bionic-dell-merion public
# deb-src http://dell.archive.canonical.com/updates/ bionic-dell-merion public


** /etc/apt/sources.list.d/bionic-dell-merion.list.save:

deb http://dell.archive.canonical.com/updates/ bionic-dell-merion public
# deb-src http://dell.archive.canonical.com/updates/ bionic-dell-merion public


** /etc/apt/sources.list.d/bionic-dell-service.list:

deb http://dell.archive.canonical.com/updates/ bionic-dell-service public
# deb-src http://dell.archive.canonical.com/updates/ bionic-dell-service public


** /etc/apt/sources.list.d/bionic-dell-service.list.save:

deb http://dell.archive.canonical.com/updates/ bionic-dell-service public
# deb-src http://dell.archive.canonical.com/updates/ bionic-dell-service public


** /etc/apt/sources.list.d/bionic-oem.list:

deb http://oem.archive.canonical.com/updates/ bionic-oem public
# deb-src http://oem.archive.canonical.com/updates/ bionic-oem public


** /etc/apt/sources.list.d/bionic-oem.list.save:

deb http://oem.archive.canonical.com/updates/ bionic-oem public
# deb-src http://oem.archive.canonical.com/updates/ bionic-oem public


** /etc/apt/sources.list.d/google-chrome.list:

### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main


** /etc/apt/sources.list.d/google-chrome.list.save:

### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main


** /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-bionic.list:

deb http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu bionic main
# deb-src http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu bionic main


```

---

### Post by oldfred on 2020-05-20
I did not know there was a bionic-dell and bionic-oem sources for the Dell systems with pre-installed Ubuntu.
So you do not get the normal bionic updates, but some modified for your specific Dell.
And then that is why your kernels are different.

I do know Dell has Sputnik which are additional drivers for new Linux. But those typically get included in newer Ubuntu releases.
New Dell 2020 & Sputnik history
[https://bartongeorge.io/2020/01/01/introducing-the-2020-xps-13-developer-edition-this-one-goes-to-32/](https://bartongeorge.io/2020/01/01/introducing-the-2020-xps-13-developer-edition-this-one-goes-to-32/)
[https://www.dell.com/support/article/uk/en/ukdhs1/sln310507/ubuntu-based-developer-and-engineering-systems-project-sputnik?lang=en](https://www.dell.com/support/article/uk/en/ukdhs1/sln310507/ubuntu-based-developer-and-engineering-systems-project-sputnik?lang=en)

You are only showing 8% use of / or p3 partition.
I might shrink that and install standard 20.04 in 30GB just to see if it works. Make sure you have good backups. Do not just rely on reinstall from ISO to restore system.
A new install will change the /EFI/ubuntu/grub.cfg to boot new install. But you can edit back to default boot 18.04.

Otherwise you may do better with Dell forum.

[https://www.dell.com/community/Latitude/bd-p/Latitude?ref=lithium_menu](https://www.dell.com/community/Latitude/bd-p/Latitude?ref=lithium_menu)

---

### Post by Martin_Kuemmel on 2020-05-20
> **oldfred said:**
> 
You are only showing 8% use of / or p3 partition.
I might shrink that and install standard 20.04 in 30GB just to see if it works. Make sure you have good backups. Do not just rely on reinstall from ISO to restore system.
A new install will change the /EFI/ubuntu/grub.cfg to boot new install. But you can edit back to default boot 18.04.

Otherwise you may do better with Dell forum.
[https://www.dell.com/community/Latitude/bd-p/Latitude?ref=lithium_menu](https://www.dell.com/community/Latitude/bd-p/Latitude?ref=lithium_menu)
Do I understand correctly that:
[LIST]
[*]the cause of the problem is not clear; 
[*]I should give 20.04 a try; 
[*]I could try a generic Dell Forum; 
[/LIST]

Could it be a hardware problem?

---

### Post by oldfred on 2020-05-20
If it boots once ok, then I doubt it is a hardware problem.

It seems like some setting & then update adds something that does not like that setting or needs a different setting.

Have you done the firmware updates?

Those with a Dell may know of issue or have good suggestions. So Dell forum and perhaps Dell support.

---

### Post by Martin_Kuemmel on 2020-05-20
> **oldfred said:**
> 
Have you done the firmware updates?
Yes, Dell suggested that, and actually also today was a forced BIOS update

> **oldfred said:**
> 
Those with a Dell may know of issue or have good suggestions. So Dell forum and perhaps Dell support.
Dell Support sent me to here.....

---

### Post by Martin_Kuemmel on 2020-05-21
Now I have 20.04 as a parallel installation to 18.04.

And actually 20.04 is the first OS (out of 4) that rebooted after a kernel update.

So far it:
[LIST]
[*]always rebooted; 
[*]always wake up from suspend; 
[*]there were no problems so far; 
[/LIST]

I'll still test for a week or so with frequent reboots and so on, and, if everything goes well, go ful on 20.04 and move my data.

---

### Post by oldfred on 2020-05-21
I prefer to keep / (root) in a smaller 25 to 30GB partition and have data in other partition(s).
If new user easier to use separate /home as that auto adds mount in fstab, and sets ownership & permissions. If you use or add your own data partitions, you have to manually do all those settings.

You can move /home from old install to its own partition and mount it in new install.

To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
[https://ubuntuforums.org/showthread.php?t=2343317](https://ubuntuforums.org/showthread.php?t=2343317)

---

### Post by Martin_Kuemmel on 2020-05-24
Okay, everything looks fine and from 20.04 the laptop boots consistently and comes back from suspend.

I'll mark the thread as solved though technically this is not the case. The situation is only mitigated by the lucky coincidence that the laptop works with 20.04.

I am still puzzled how:

[LIST]
[*]Dell gets a certificate for a system that does not work; 
[*]Dell does not help to solve the problem; 
[/LIST]
 
Thanks for helping me through this.

---

