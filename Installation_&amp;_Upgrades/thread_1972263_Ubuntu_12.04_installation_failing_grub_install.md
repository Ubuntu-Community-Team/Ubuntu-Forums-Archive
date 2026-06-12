---
title: "Ubuntu 12.04 installation failing grub install"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by desater on 2012-05-03
I don't know what to do with it anymore, every single release of Ubuntu (since I've been using it from 10.04) has had installation problems.

Right now on 12.04 the issues rise to a climax.

Let me sketch the situation:

I'm trying to get dualboot (windows 7 64bit sp1 + ubuntu 12.04 64bit) working on an m17x-R1 alienware notebook.

Here's the hardware:
[LIST]
[*]2x Nvidia GTX20m in SLI
[*]an Nvidia 9800m (disabled in bios)
[*]2x 320GB HDD in raid 0
[*]an infrared receiver
[/LIST]

[SIZE="1"]* (I listed the video cards because Ubuntu had issues with that before)[/SIZE]

First I backup all my files, then I reinstall windows 7 (deleting  all partitions - including the ubuntu ones that I had) because I want a nice clean computer.

Windows 7 cleans the partitions, installs nice and easy. I already had my ubuntu live-usb made with 12.04 on it.

**_First problem_**
The Ubuntu couldn't boot to live-usb, it gave a kernel panic. Apparently it had to do with the infrared receiver inside my notebook. Long story short, I found the bug on launchpad ([[COLOR="Red"]**LINK**[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/972723")). Disabling the infrared receiver allowed me to boot into the installation.

**_Second problem (?)_**
I chose to specify the partitions myself. Although the partition manager went a bit crazy on me I think (maybe this is related to having a raid 0 setup?). In the partition manager UI I saw my partitions and some other strange things:

This is the path to my drive: /dev/mapper/nvidia_edffafeb

What I expected to see after I partitioned my free space:
[LIST]
[*]/dev/mapper/nvidia_edffafeb1 (windows boot loader)
[*]/dev/mapper/nvidia_edffafeb2 (windows drive)
[*]/dev/mapper/nvidia_edffafeb3 (/boot)
[*]/dev/mapper/nvidia_edffafeb5 (/)
[*]/dev/mapper/nvidia_edffafeb6 (swap)
[*]/dev/mapper/nvidia_edffafeb7 (/home)
[/LIST]

but there were "copies" of the windows partitions there - which I couldn't edit (gave ubi-partman error code 141).

looked like this: (tree structure)

/dev/mapper/nvidia_edffafeb
    /dev/mapper/nvidia_edffafeb1 (windows boot loader)

/dev/mapper/nvidia_edffafeb
    /dev/mapper/nvidia_edffafeb2 (windows drive)

/dev/mapper/nvidia_edffafeb
    /dev/mapper/nvidia_edffafeb3 (unpartitioned space)

Anyhow, I left those like they were and selected
/dev/mapper/nvidia_edffafeb for the grub-install.

Ubuntu installed fine after this point.

**_Third problem_**
After Ubuntu installation a problem I had earlier came up again - the grub-install failed on /dev/sda. Although I specified it to be on /dev/mapper/nvidia_edffafeb.

No matter, I could reselect the location and did so accordingly.

grub-install failed again; it couldn't install to (hd0) was the message.

I then chose it to install to /dev/mapper and other paths.
Each of them failing.

Exited saying: continue without installing boot loader.

**_Fourth problem_**
I rebooted to my live-usb again and got boot-repair working. It did it's auto-fix procedure and gave me this log ([[COLOR="red"]**LINK**[/COLOR]]("http://paste.ubuntu.com/964015/")).

When I rebooted I got into grub and it gave me 4 options:

[LIST]
[*]Ubuntu, with Linux 3.2.0-24-generic
[*]Ubuntu, with Linux 3.2.0-24-generic (recovery mode)
[*]Memory test (memtest86+)
[*]Memory test (memtest86+, serial console 115200)
[/LIST]

*My windows was gone*

booted into recovery mode - ran grub repair there. and it gave me 4 extra boot options on top of the ones above:

[LIST]
[*]Windows 7 (loader) (on ./dev/mapper/nvidia_edffafeb1) - this one boots into windows
[*]Windows 7 (loader) (on ./dev/mapper/nvidia_edffafeb2)
[*]Ubuntu, with Linux 3.2.0-24-generic (on ./dev/mapper/nvidia_edffafeb6)
[*]Ubuntu, with Linux 3.2.0-24-generic (recovery mode) (on ./dev/mapper/nvidia_edffafeb7)
[/LIST]

**_Fifth problem_**
The actual boot...
When trying to boot the first option (try to visualize both lists above as if they were under eachother) it gives me 2 "inotify watch" errors which disappear too fast for me to read and then turns into a half purple screen with some fragments on it (hangs there)
-same issue when trying to boot the ubuntu on nvidia_edffafeb6-

*Of course the infrared receiver had to be blacklisted here as well!*

edited parameter of first option: added "ite_cir.blacklist=yes" at the end of the parameter list.
This one actually booted a little bit, but loops endlessly in the "ubuntu ° ° ° ° °" screen where the dots change white to purple and visa versa.

Any idea on how I can actually make this work?

Thanks in advance.

---

### Post by oldfred on 2012-05-03
I do not know RAID, did you use the liveCD or the alternative installer version? LiveCD did not used to have any RAID drivers as it was uncommon. I have seen some others like you that seem to be able to install but grub2 does not, so is liveCD now partially work? I think alternative installer is still the correct one for RAID or LVM partitioning.

With nVidia, I have had to use nomodeset on all boots from liveCD and and first boot after install or until I have installed nVidia proprietary driver.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

---

### Post by desater on 2012-05-03
Tried the "nomodeset" option.

(with and without the "ite_cir.blacklist=yes" option as well)

Both the boot options for ubuntu and both combinations of those options result in a freeze after it says:

*Starting CUPS printing spooler/server [OK].
(don't know what comes after that).

I installed Ubuntu with the regular LiveCD. Should I try re-installing Ubuntu with the alternative installer?

---

### Post by oldfred on 2012-05-03
Does recovery mode get a command line? Then it is definitely your video. Not sure if SLI adds complications or not.

---

### Post by desater on 2012-05-07
Ok, update:

I installed Ubuntu using the alternate installer and everything went fine.
Install + boot are good!

New problems rose though, but not related to this topic!

Can mark this as solved!

Thanks!

---

