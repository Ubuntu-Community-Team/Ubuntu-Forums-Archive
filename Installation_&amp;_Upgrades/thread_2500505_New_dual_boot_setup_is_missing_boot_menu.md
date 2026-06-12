---
title: "New dual boot setup is missing boot menu"
date: 2024-09-04
forum: Installation &amp; Upgrades
---

### Post by deaks63 on 2024-09-04
I recently installed the latest Lubuntu alongside Windows 7, on an old Dell all in one machine.
The install seemed to go fine, but on startup there's no option to select between Windows or Lubuntu and, the system boots into Lubuntu.
I've used 'boot-repair' to generate a summary report and uploaded to [https://paste.ubuntu.com/p/2QpCVS2Jcw/](https://paste.ubuntu.com/p/2QpCVS2Jcw/)

Any help would be appreciated.

---

### Post by tea for one on 2024-09-04
While you are booted into Lubuntu, can you edit your grub configuration as follows:-
```
sudo nano /etc/default/grub
```
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR='Ubuntu'
GRUB_CMDLINE_LINUX_DEFAULT='quiet splash'
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false
```
Ctrl O to save & Ctrl X to exit
```
sudo update-grub
```
Power off and power on
Any joy?

---

### Post by tea for one on 2024-09-04
Also, Windows 7 reached End of Life in January 2020 and it should not be used for internet activity

---

### Post by deaks63 on 2024-09-04
Thanks for that. I now have a boot menu but there's no option for Windows.

Here's the output of sudo update-grub

Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/lubuntu-grub-theme.cfg'
Generating grub configuration file ...
Found theme: /usr/share/grub/themes/lubuntu-grub-theme/theme.txt
Found linux image: /boot/vmlinuz-6.8.0-41-generic
Found initrd image: /boot/initrd.img-6.8.0-41-generic
Found memtest86+x64 image: /boot/memtest86+x64.bin
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows 7 on /dev/sda1
Adding boot menu entry for UEFI Firmware Settings ...
done

Kind of looks like it would work, but no such luck!

---

### Post by guiverc on 2024-09-04
I'll add this, but I'm unsure if this is your issue or not..  Your description (install alongside I'm assuming) would not be expected to trigger this, but I'll provide it.

In QA (Quality Assurance testing) I encountered an situation where grub wouldn't offer a dual boot though I already had two OSes and it was triggered when you installed into (without format) the first installed system's partition on the disk (as that OS wasn't aware of another OS), so I'll provide the bug report.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/2060624](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/2060624)

If this is the issue, just flipping the OS_PROBER flag will fix it...   This bug just cases the upstream GRUB default to be used (ie. no scan for other OSes is done) and doesn't use the Ubuntu patches that cause dualboot scans by default.

On my system (dual boot Lubuntu) I have grub showing me my other OS (I'm using oracular currently; it allows me to select my LTS or noble install) and the following check is what I see when looking at my current OS_PROBER state

```

guiverc@d7050-next:~/uwn/issues/855$   grep OS_PROBER /etc/default/grub 
#GRUB_DISABLE_OS_PROBER=false

```

I wonder what you have for that line, is it commented out as mine is?

Probably worth a check.

---

### Post by deaks63 on 2024-09-04
I've got this, having previously uncommented the line as suggested by tea for one

simon@till2:~$ grep OS_PROBER /etc/default/grub
GRUB_DISABLE_OS_PROBER=false

---

### Post by deaks63 on 2024-09-04
It doesn't seem to matter whether that line is commented out or not, the output of sudo update-grub is the same!

simon@till2:~$ sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/lubuntu-grub-theme.cfg'
Generating grub configuration file ...
Found theme: /usr/share/grub/themes/lubuntu-grub-theme/theme.txt
Found linux image: /boot/vmlinuz-6.8.0-41-generic
Found initrd image: /boot/initrd.img-6.8.0-41-generic
Found memtest86+x64 image: /boot/memtest86+x64.bin
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows 7 on /dev/sda1
Adding boot menu entry for UEFI Firmware Settings ...
done

os-prober still runs and finds Windows 7

---

### Post by yancek on 2024-09-04
Go to your /boot/grub/grub.cfg file and find the menuentry for windows 7 and post it here.  Is sda1 your original windows 7 /boot partition?

---

### Post by oldfred on 2024-09-04
Please use code tags for terminal or text output.
If using Quick Reply then[noparse] ```
 at the beginning and 
``` at the end. [/noparse]
Easy to add with Forum's Go Advanced editor and # icon.
[https://ubuntuforums.org/showthread.php?p=12776168#post12776168](https://ubuntuforums.org/showthread.php?p=12776168#post12776168)

Did you also change this entry as tea for one suggested?
> GRUB_TIMEOUT_STYLE=menu

And/or, can you hold shift key from BIOS menu until grub would normally appear?

Note, to make Windows repairs on your system, you may have to temporarily reinstall Windows boot loader to MBR.
But Windows uses boot flag, grub does not. But you now have boot flag on Linux partition. Use gparted to moved flag back to sda1.

---

### Post by deaks63 on 2024-09-04
@yancek

```

simon@till2:~$ sudo grep windows /boot/grub/grub.cfg 
menuentry 'Windows 7 (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-CE3A91293A910F97' {
menuentry 'Windows 7 (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-0064928B649282D8' {

```

@oldfred

```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR='Ubuntu'
GRUB_CMDLINE_LINUX_DEFAULT='quiet splash'
GRUB_CMDLINE_LINUX=""

# If your computer has multiple operating systems installed, then you
# probably want to run os-prober. However, if your computer is a host
# for guest OSes installed via LVM or raw disk devices, running
# os-prober can cause damage to those guest OSes as it mounts
# filesystems to look for things.
GRUB_DISABLE_OS_PROBER=false

```

I also applied the boot-repair fix but to no avail.
I'll reboot and hold shift key down now.

---

### Post by tea for one on 2024-09-04
@deaks63
Was Windows 7 working perfectly before you installed Lubuntu?

---

### Post by deaks63 on 2024-09-04
Yes it was. It's only used to run a point of sale application since the machine it's installed on is used as one of two shop tills on a LAN.
As you pointed out in your first reply, Windows 7 is no longer supported and shouldn't be used for internet activity. I have an app called NetDisabler installed on three Windows 7 machines, which prevents internet access while still allowing LAN access. The reason for installing Lubuntu alongside Windows was so that I could use one of the shop front machines to access the internet as and when the shop is quiet enough.

---

### Post by tea for one on 2024-09-04
> **deaks63 said:**
> The reason for installing Lubuntu alongside Windows was so that I could use one of the shop front machines to access the internet as and when the shop is quiet enough.
Then, you could have prepared a USB stick with Lubuntu and run a live session without interfering with your existing set-up.
In your position, as Windows 7 is critical for your business, I would remove Lubuntu and fix the Windows Boot Manager with Windows tools (assuming that they still exist for Windows 7)

---

### Post by deaks63 on 2024-09-04
I tried Lubuntu on a live USB, liked it and since I've previously had a Windows/Ubuntu dual boot setup, assumed it would be fine to dual boot with Windows/Lubuntu.
Windows 7 isn't critical for my business, I just prefer it to later Windows versions. I use Linux for everything else whenever possible.
If think my issue is probably related to the bug mentioned by guiverc

 [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/2060624](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/2060624)

and hopefully a fix will be implemented before too long :)

---

### Post by deaks63 on 2024-09-05
FYI I used gparted to move the boot flag back to sda1 but it changed nothing.
I get a boot menu but with no Windows 7 option and the system boots into Lubuntu.

---

### Post by tea for one on 2024-09-05
The bug report (post 14) refers to the calamares installer and Legacy systems.
If you have the time and inclination, you could try Xubuntu in place of Lubuntu.
Xubuntu uses a different installation package and may be more friendly towards Windows 7?

---

### Post by deaks63 on 2024-09-05
I did look at Xubuntu on a live USB but preferred Lubuntu which I've used in the past.
For the last few years I've been using Linux Lite and always found it remarkably stable although I never tried it on a dual boot setup.
I went with Lubuntu because it offered a minimum install option which suits me. However, since installing it yesterday morning it's hung on me a couple of times already which is offputting to say the least.
I think I might do a fresh install of Windows 7 then try a dual boot setup with Linux Lite and see how that goes.

Thanks for the suggestion anyhow.

---

### Post by tea for one on 2024-09-05
> **deaks63 said:**
> I went with Lubuntu because it offered a minimum install option which suits me.
> The final release images for Xubuntu Desktop and Xubuntu Minimal are available as torrents and direct downloads 
Xubuntu also has a minimal install 
[https://xubuntu.org/news/xubuntu-24-04-released/](https://xubuntu.org/news/xubuntu-24-04-released/)

---

### Post by deaks63 on 2024-09-05
tea for one,

I'm happy to report that I now have the option to boot into Windows 7 and it works fine so I have my till back!
In a nut shell what I did is install Xubuntu (minimum) alongside Windows 7 and Lubuntu (there didn't seem to be an option to replace Lubuntu).
The Xubuntu installer was a bit glitchy (visually) on my machine and seemed to hang at the end until I pressed <enter> a couple of times but lo and behold, on startup I have a fully populated boot menu.
I'd like to remove Lubuntu now, would you suggest gparted for that?

---

### Post by tea for one on 2024-09-05
> **deaks63 said:**
> I'm happy to report that I now have the option to boot into Windows 7 and it works fine so I have my till back!
Splendid, admirable perseverance on your side
> **deaks63 said:**
> In a nut shell what I did is install Xubuntu (minimum) alongside Windows 7 and Lubuntu (there didn't seem to be an option to replace Lubuntu)
You would have to choose "Something Else (Manual Partitioning)" and override the Lubuntu partition
> **deaks63 said:**
> I'd like to remove Lubuntu now, would you suggest gparted for that?
Yes, I would use gparted to remove/add/manipulate partitions.
Backups essential to avoid catastrophic human error i.e. choosing the wrong partition.

When you are completely happy with everything, it's very helpful to mark the thread as solved for the benefit of other users/members.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

