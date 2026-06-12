---
title: "How to install 18.04 over 16.04 while preserving windows 10"
date: 2018-07-07
forum: Installation &amp; Upgrades
---

### Post by jgwphd on 2018-07-07
I have a Dell Insperion model 5555 (64 bit machine) using Grub dual boot that is currently running Ubuntu 16.04 and Windows 10. It runs fine but I'd like to be able to remove 16.04 and add 18.04 and also keep windows. I had to adjust the Dell bios settings for "EFI" and "Secure boot" to get the laptop to boot from the DVD drive which had a current copy of 18.04 .iso. 

I am "assuming" windows requires secure boot and/or EFI to be enabled before you can boot into windows 10 AND you need to turn them OFF to install a new OS, such as 18.04??? Once disabled EFI and Secure boot I was able to boot from the DVD drive. At that point everything was working well but instead of going directly to the Ubuntu install sequence I got the trial 18.04 desktop with a disk icon to select (I typically find when I install a new version of Ubuntu that I enter the install sequence directly not the desktop - so I become suspicious something wasn't proceeding as expected). I selected it and it started the install process. Once I finally got to the screen with prompt selections such as: do you want to erase 16.04 and reinstall 16.04, do you want to erase the disk and install 18.04, Do you want to install 18.04 beside 16.04....etc. There was NO selection WITH windows 10 being acknowledged as present. I was worried about deleting windows 10 by accident so I stopped at this point. My GOAL is to replace 16.04 with 18.04 and keep windows 10. 

What is the correct way to do this? Can I upgrade directly to 18.04 from a running 16.04? ...or do I need to use the DVD .iso image to erase/overwrite 16.04 and install 18.04? If I use the .iso then what are the proper Bios settings for EFI and secure boot so that I can my goal to replace 16.04 with 18.04 and keep windows 10. Any assistance is appreciated. Many thanks!

---

### Post by Dennis N on 2018-07-07
**"I selected it and it started the install process..."**

You were on the right track. After starting the installation, when you are on the first "Installation Type" page, select the "something else" option (at the bottom). This sends you to the partitioning screen. Select the 16.04 root partition, click the "change" button, and fill in details in the popup dialog in order to reuse this for the new root partition. Also mark the partition to be formatted ext4. You can then proceed with the install. 

You probably don't, but if you have a separate home partition, you have another step to choose the old home partition for reuse as new home partition on the partitioning screen. You can format it, which will erase the data, or not format which should preserve data on it.

To be safe, back up any important data before installing.

---

### Post by jgwphd on 2018-07-07
Dennis N, thanks for the information. I am just being very cautious and I don't want to lose windows 10. I am already dual boot with Ubuntu and Windows. Can I just boot into Ubuntu 16.04 and then use the Upgrade process (describe here: [https://itsfoss.com/upgrade-ubuntu-version/](https://itsfoss.com/upgrade-ubuntu-version/)) to get to 18.04 instead of playing with partitions ....which always makes me nervous. I "assume" once I am running in 16.04 and do an upgrade from that 16.04 system partition it won't do anything to disturb the windows partition and I'll remain dual boot with 18.04 and not lose windows. Is that true? ...or an "ok" strategy. Thanks for your patience and explanations.

---

### Post by yancek on 2018-07-08
You should be able to upgrade directly from 16.04 to 18.04 and not lose data.  I would backup any important personal data to another device before beginning.  Doing an update, in my experience takes much longer than a new install.  Doing an upgrade should not have any effect on windows because it is on separate partitions.  If you were to do a new install, you could create a new partition on which to install 18.04 if you have available space and keep 16.04 on separate partitions.  Whichever choice you make, you need to do backups first.

---

### Post by jeremy31 on 2018-07-08
I would hold off on doing an upgrade from 16.04 to 18.04 for a week or so.  It seems some mesa packages in 16.04 have a higher version number than 18.04 and it may cause issues

---

### Post by Dennis N on 2018-07-08
> Can I just boot into Ubuntu 16.04 and then use the Upgrade process

I think the upgrade is a good bet to try first. The 17.10 to 18.04 upgrade has been available since the 2nd week after 18.04 release. I did six of them and all were successful. Some people use terminal commands, but I used the regular Software Updater to to it when a popup notice offers to do the upgrade to 18.04 when completing a regular 17.10 update. After it's available, there will also be an 'upgrade' button at the bottom of the Software Updater window.

The 16.04 to 18.04 upgrade hasn't been offered yet. I am also waiting to do two of those. A while ago, I did the LTS to LTS upgrade of a 14.04 to 16.04. No problem there either.

I use a separate data partition, so no worry about losing my files should the process fail. For peace of mind, you should always prepare for a disaster, even if unlikely, so back up your important data before starting upgrades.

---

### Post by jgwphd on 2018-07-08
Ok I did upgrade! Some interesting things happening. I did the upgrade via the terminal. The upgrade appeared to complete but when I boot and I get past the log on screen then the mouse click doesn't work. I can move the mouse but can't click on anything! I used the keyboard techniques to navigate without a mouse. When i got into the terminal, I found out I was at Ubuntu 17.10 (not 18.04). So the upgrade from 16.04 only took me to 17.10. When I executed update-manager from the terminal at this point the software updater said I was at 17.10 and 18.04 was available. So I selected upgrade option and proceeded to upgrade to 18.04 (hoping that would solve my mouse issues). The dual boot windows still works fine, so I still have windows to do my work. But no Ubuntu. When I now boot into Ubuntu 18.04 I can't get to the login screen. What happens is that booting simply stops at the Ubuntu logo, with the first of these five Ubuntu splash screen dots filled. The login screen only appears briefly and then I see a black  screen most of the time, with some text blinking up shortly from time to  time. This strongly looks like [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1727356](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1727356). I will close this thread and start another with this current problem to bypass this bug by disabling "Wayland" on boot. This is an AMD A8 processor with Radeon R5 graphics (no Intel).

---

### Post by jgwphd on 2018-07-09
Since my initial question was resolved on this thread. I am closing this as solved. The new problem that I discovered is being investigated on another thread (in caes anyone wants to follow) titled.  "Ubuntu 18.04 hangs at boot with black screen, occasional flashing text". Many thanks for everyone's assistance

---

