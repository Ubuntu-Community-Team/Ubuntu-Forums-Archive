---
title: "GRUB not working"
date: 2016-09-07
forum: Installation &amp; Upgrades
---

### Post by aavshr on 2016-09-07
help needed with grub. Not working still after running boot repair.

here's the boot repair log. [http://paste2.org/MhBkzbxY](http://paste2.org/MhBkzbxY)

I have turned off secure boot. I tried changing the boot entry of the windows bootloader but access was denied.

---

### Post by yancek on 2016-09-07
Was this a new install of Ubuntu or was something changed after the install?  You have a recent windows version installed along with Ubuntu with the correct boot setup and files for both system.  The only really obvious thing is down past the center of the page and also at the bottom of the page where it indicates an NTFS partition is in an unsafe state.  That means you left your windows hibernated and therefore you will not be able to access it from any Linux system as there is too much likelihood to cause damage.  That's the reason for the accesss denied.  This is a default setting for windows 8 and newer so that your  windows appears to boot faster.  You need to reboot windows and fully shut it down which you should always do when you may access the windows partitions from another system.

You haven't explained what you can and cannot do, boot either or neither?

---

### Post by oldfred on 2016-09-07
I see reference to Acer in script.

If an Acer it has unique UEFI requirement of setting a UEFI password and enabling "trust" on the grub/ubuntu .efi boot files.
Also make sure you have newest UEFI. Some before had to downgrade to older UEFI, but newest works. 

These are all essentially the same, but some give more details or different way to explain how, so best to review at least a couple.
       Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757
[/URL]
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 
      
 One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335) 
    [URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]
[/URL]

---

