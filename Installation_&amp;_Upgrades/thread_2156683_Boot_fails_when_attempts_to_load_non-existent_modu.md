---
title: "Boot fails when attempts to load non-existent modules.dep"
date: 2013-06-22
forum: Installation &amp; Upgrades
---

### Post by tidon12 on 2013-06-22
First time posting on this forum so apologies if this is not the correct post location or format.

**Summary**:
I've done a fresh install of Ubuntu 12.04 64 bit from a usb stick on a Dell XPS 15z and the system is unable to boot. To me the problem appears to be that it is trying to access modules in an old kernal that is no longer on my computer. The kernal I'm using is 3.5.0-23-generic but it appears to be attempting to access 3.0.0-12-generic for modules at least. I've tried reinstalling again in the hopes that there was a simple install error but that does not appear to fix the problem.

**Events Sequence:**
Computer boots through BIOS, grub appears
GRUB appears to recognize correct kernal (options listed as "Ubuntu, with Linux 3.5.0-23-generic")
I adjust boot options based on instructions on [XPS 15z hardware support page]("https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z") (I've tried acpi=noirq; acpi_backlight=vendor dell_laptop.backlight=0; or no changes at all. All of these options lead to the same error below.)
After I initiate boot, I get the errors below:

modprobe: FATAL: Could not load /lib/modules/3.0.0-12-generic/modules.dep: No such file or directory

which repeats several times then is followed by

ALERT! /dev/disk/by-uuid/d55de20a-c30e-45c3-adf4-cd411648e7aa does not exist.
Dropping to a shell!
FATAL: Could not load /lib/modules/3.0.0-12-generic/modules.dep: No such file or directory

This is puzzling to me for a couple of reasons. I've tried running boot repair after booting from the usb directly ([results available here]("http://paste.ubuntu.com/5790646/")), and the UUID listed in the alert statement is my actual ubuntu partition, so I don't know why it would be stated as not existing.

Does anyone have any advice on what has gone wrong or how to fix things?

Thanks

---

### Post by oldfred on 2013-06-22
What mode is BIOS in for hard drive. AHCI is preferred, but Windows 7 may need a driver before you change to it. Your drive should not be in IDE nor RAID mode, but other alternatives if no AHCI is large or LBA.

If BIOS settings are ok, then it is just some combinations of BIOS and grub do not see grub or boot files beyond a certain point on hard drive. Some have had it work if they just continue and wait a bit, some if just retrying, but most have to make a small 300MB /boot partition totally within the first 100GB of the hard drive. Issue is more with large drives and boot files far into hard drive.

---

### Post by kwalters on 2013-06-23
I have experienced similar problems after upgrading to Ubuntu 13.04 32 bit. My Ubuntu root partition is fairly well down the hard disk on which it resides - something like SDB6, so the second post above might be a clue.  I am also fairly limited on RAM  -  only 1400 MB.

I have found a work round, but not a solution.  If the aubergine screen goes on for too long with nothing happening, or if I get a message that the UUID for my Ubuntu partition does not exist, I just type "exit" on the keyboard and press the enter key.  Most times, some disk activity starts and Ubuntu starts up and works perfectly.

No idea why that work around works; and no idea about a solution. Any ideas out there?

kwalters

---

### Post by tidon12 on 2013-06-30
Thanks for the help. After some partition juggling with my Windows installation and calling in to get the original boot cd, I was able to get rid of my windows recovery partition and create a separate ubuntu boot partition in its place. Unfortunately, I still appear to be getting the same modprobe error I mentioned above.

This is the latest [boot repair output]("http://paste.ubuntu.com/5814393/"). Does anyone have any other ideas on how to fix this?

Thanks

---

### Post by oldfred on 2013-06-30
Are you still getting that same UUID error? As that UUID is not on system and Boot-Repair says it reinstalled grub?

---

### Post by tidon12 on 2013-06-30
Just tried to boot again. this is the exact text of the error. the uuid referenced is the uuid of my root partition per the [boot repair output]("http://paste.ubuntu.com/5814393/")

[COLOR=#000000]modprobe: FATAL: Could not load /lib/modules/3.0.0-12-generic/modules.dep: No such file or directory[/COLOR]

[COLOR=#000000]which repeats several times then is followed by

Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - CHeck root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)

ALERT! /dev/disk//by-uuid/ff6eb009-776f-491e-8079-74d721453ee9 does not exist.

Dropping to a shell

[/COLOR][COLOR=#000000]FATAL: Could not load /lib/modules/3.0.0-12-generic/modules.dep: No such file or directory[/COLOR]

---

### Post by oldfred on 2013-06-30
I wonder if grub did not fully update. 
Boot-Repair has a way to help you chroot into your install and fully un-install grub2 and reinstall it. I would try that.

---

### Post by tidon12 on 2013-06-30
Still getting the same error, although it's possible I'm doing something wrong. New pastebin is below

[http://paste.ubuntu.com/5815267/](http://paste.ubuntu.com/5815267/)

How would I know if I did it correctly?

---

### Post by oldfred on 2013-06-30
Most desktops do not have the separate /boot. Are you mounting both the /boot & the main install when you chroot repair? Many instructions do not mention that little but vital point as /boot is more for servers.

 drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

---

### Post by tidon12 on 2013-07-05
I followed the instructions here under chroot with a separate /boot partition and still got the same error when i try to boot from the hard disk.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Everything seemed to work fine and grub reinstalled, but still no changes when I actually try to boot. Any other ideas?

Error repeated from above:

[COLOR=#000000][COLOR=#000000]modprobe: FATAL: Could not load /lib/modules/3.0.0-12-generic/modules.dep: No such file or directory[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]which repeats several times then is followed by

Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- CHeck root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)

ALERT! /dev/disk//by-uuid/ff6eb009-776f-491e-8079-74d721453ee9 does not exist.

Dropping to a shell

[/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]FATAL: Could not load /lib/modules/3.0.0-12-generic/modules.dep: No such file or directory[/COLOR][/COLOR]

---

### Post by tidon12 on 2013-07-14
Does anyone have any ideas on this? I've tried the chroot method and the error seems to persist. I've also tried running boot repair to no avail.

Can anyone think of any other method to diagnosis this? I don't know why I'm consistently being told that my partition doesn't exist.

---

### Post by oldfred on 2013-07-14
Some BIOS or grub do not boot from larger drives beyond 100GB. Grub seems to get lost or BIOS does not report it correctly. It is not easy for you to move Windows to have /boot at beginning of drive, but that often is the solution.

Not sure what all the duplicate sources or falling back to Teletype errors are. That is an old terminal text mode before monitors or  new fangled "glass Teletypes"? Or your install does not seem totally correct??

---

### Post by steeldriver on 2013-07-14
You're not exactly being told the partition doesn't exist - you're being told the *symlink* from /dev/disk/by-uuid doesn't exist - that *may* be just because the boot process fails before that gets created (by udev?)

I don't have much experience of boot-repair reports but this stuck out

```

shim-signed available
linux-signed-generic NOT available (apt-cache policy  problem) 
Please type: sudo chroot "/mnt/boot-sav/sda5" dpkg --configure -ansudo chroot "/mnt/boot-sav/sda5" apt-get install -fynsudo chroot "/mnt/boot-sav/sda5" apt-get purge -y --force-yes grub*-common shim-signed

```

Is it possible that there's some left-over secure boot stuff invoking the 3.0.x kernel? I'm guessing that didn't render quite right and should be 3 lines (i.e. the n's are supposed to \n newlines)

```

shim-signed available linux-signed-generic NOT available (apt-cache policy  problem) Please type: 
sudo chroot "/mnt/boot-sav/sda5" dpkg --configure -a
sudo chroot "/mnt/boot-sav/sda5" apt-get install -fy
sudo chroot "/mnt/boot-sav/sda5" apt-get purge -y --force-yes grub*-common shim-signed

```

Again, I have no experience with secure boot but maybe someone who has will see this and be able to advise

---

