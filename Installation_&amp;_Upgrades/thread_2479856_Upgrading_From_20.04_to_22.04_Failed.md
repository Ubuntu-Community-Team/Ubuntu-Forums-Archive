---
title: "Upgrading From 20.04 to 22.04 Failed"
date: 2022-10-10
forum: Installation &amp; Upgrades
---

### Post by jim-ruxton on 2022-10-10
[FONT=Arial]I'm stuck. I was upgrading from Ubuntu 20.04 to 22.04 and during the install my network stopped working. I believe all packages were downloaded by that point. When I tried rebooting to get back my network (big mistake) I no longer had a working system. Booting into recovery mode I tried finishing the upgrade. For some reason the system doesn't see my /boot/efi partition even though it is mounted. My fstab file looks correct. Below is my screen when I try the upgrade command.  By the way this is dual boot beside Windows which is still working. [/FONT][FONT=Arial][https://photos.app.goo.gl/fozqMvjWhpi2kUeF9](https://photos.app.goo.gl/fozqMvjWhpi2kUeF9)

I tried using boot-repair from a USB stick. it gives me the information here [http://paste.ubuntu.com/p/M5KprSc7dP/](http://paste.ubuntu.com/p/M5KprSc7dP/) 
When I tried running boot -repair to fix it , it never returned and seemed to do nothing. For 12 hours it said "Applying changes: This may take several minutes".  until I stopped it. Does anyone have ideas what is wrong and how to fix this?
Thanks,
Jim[/FONT]

---

### Post by tea for one on 2022-10-10
In your image, there is the text:-
> EFI System Partition (ESP) not usable
Your EFI System partition (ESP) is not mounted at /boot/efi
Please ensure that it is properly configured and try again.
[COLOR="#0000FF"]Line 138[/COLOR] - nvme0n1	: is-GPT,	no-BIOSboot,	[COLOR="#0000FF"]hashidESP[/COLOR], 	not-usb,	not-mmc, has-os,	has-win,	2048 sectors * 512 bytes  
I imagine that this means the ESP is hidden and therefore grub could not be restored correctly.

Either boot into Windows and see if Disk management can adjust the ESP to "reveal or unhide or make visible".
Or boot into a live Ubuntu session, open Gparted and double check the ESP flags.

---

### Post by jim-ruxton on 2022-10-11
Thanks after I unhid the ESP I tried running a do-release-upgrade to finish the new release upgrade process. A message told me I had to finish updating first so I ran 
sudo apt update 
and
sudo apt upgrade
Then I got a message stating I needed to reboot. After this I could still only boot into recovery mode and the keyboard no longer worked. I tried connecting an external keyboard and that wouldn't work either. I guess the upgrade messed things up further. Wondering where to go from here without being able to enter commands? Should I try chrooting into the system partition from a Live USB and try the do-release-upgrade that way? 
Thanks 
Jim

---

### Post by mIk3_08 on 2022-10-11
> **jim-ruxton said:**
> 
Then I got a message stating I needed to reboot. After this I could still only boot into recovery mode and the keyboard no longer worked. I tried connecting an external keyboard and that wouldn't work either. I guess the upgrade messed things up further. Have you tried to run a New Ubuntu 22.04 release via live usb? Its seems that you have really missed things up. If keyboard wont work anymore even in tty I prefer to run a Ubuntu 22.04 live usb for this. Regards and cheers.

---

### Post by jim-ruxton on 2022-10-11
Thanks. Yes I am downloading the iso now. Time to start with a fresh install I think.

---

### Post by vanadium on 2022-10-11
One way to rescue your bricked update while preserving user data and config on disk is a [reinstall where you do not format the target file system](https://ubuntuforums.org/showthread.php?t=2479866&p=14115234#post14115234).

---

### Post by jim-ruxton on 2022-10-11
Thanks. Yes the only way I got back to a working system was a fresh install. I was able to save my home partition.

---

