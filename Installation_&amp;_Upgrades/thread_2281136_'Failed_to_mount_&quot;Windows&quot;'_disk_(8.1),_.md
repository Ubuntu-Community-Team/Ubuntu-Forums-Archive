---
title: "'Failed to mount &quot;Windows&quot;' disk (8.1), from Ubuntu Studio 14.10"
date: 2015-06-04
forum: Installation &amp; Upgrades
---

### Post by Henry04 on 2015-06-04
I know this is a common problem... I've tried turning off the fast shutdown in Windows 8.1... did not help.

The error message is as follows:

> Failed to mount "Windows"

Error mounting /dev/sda4 at /media/henry/Windows: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda4" "/media/henry/Windows"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.


Not wishing to mount read only, I'm asking for some possible advice.

Using a HP 500-046 Pavillion desktop... Ubuntu on an external usb HD. I also use rEFind mounted upon a usb flashdrive to access Grub, Ubuntu, through the UEFI (secure boot disabled, legacy enabled).

Thanks,
Henry04 ):P

---

### Post by Bucky Ball on 2015-06-04
You have just installed Ubuntu? You installed it in UEFI mode? If Win8 is installed in UEFI mode, and it probably is, then Ubuntu should be also.

Something's going on, though, and this is a clue:

```
Windows is hibernated, refused to mount.
```

---

### Post by oldfred on 2015-06-04
WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast startup
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast startup is hidden.
If issues you may need these?
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavailable, make sure fast startup is unchecked 
powercfg /h off

---

### Post by Henry04 on 2015-06-04
> Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavailable, make sure fast startup is unchecked
powercfg /h off 

Hi All,

Thanks for replies.

Please note,  I misstated in that I double triple checked that ***fast startup is unchecked...*** & I still get the above stated error msg.

To restate; I turn off secure boot & fast boot, enable legacy, in the HP UEFI configuration, *then do a restart using another device...* (FROM Windows 8.1 to Ubuntu...), I then get to Grub with a program called "rEFind" which is a kind of boot loader... installed on a USB flashdrive. All of this works fine, & I have been doing this for over a year... I also can reverse the routine through the UEFI configuration panel (minus the rEFind program), & boot into Windows... 

The problem that I (now) cannot resolve is the change that Windows made, apparently causing the error message I quoted... & more importantly, will not allow for mounting the Windows disk... I have, for going on for a couple of years, been able to access my NTFS/Windows data files FROM Linux until just recently... This is what I am trying to resolve, presently.

Henry04

---

### Post by oldfred on 2015-06-05
You cannot do restart, but must do shutdown.

---

