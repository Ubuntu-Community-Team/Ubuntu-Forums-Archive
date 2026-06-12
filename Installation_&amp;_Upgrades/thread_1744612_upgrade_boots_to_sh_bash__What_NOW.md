---
title: "upgrade boots to sh: bash  What NOW?"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by matt5555 on 2011-04-30
Upgraded from 10.1 to 11.04 and now it's crashed.  Boots to terminal screen that says sh: bash.  So what do I do now?  Obviously I'm not a programmer.  If I download an new installation to cd and do a new install is there anyway I can get my evolution email.  Real bummer.

---

### Post by oldfred on 2011-04-30
Welcome to the forums.

You are getting a bash prompt not a grub>? Are you getting a login at the command line? Then it is probably a video issue, not a boot issue.

If you hold the shift key down from BIOS until a menu appears, do you get a grub menu? Try rescue mode, and/or try adding nomodeset paramter.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

You should be able to recover everything from a liveCD. But you also should have a good backup of /home. Do you have a separate /home as then it is somewhat easier to do a clean install as all your user settings & files are in /home. If doing a clean install a few other things to backup before the install are a list of installed programs, custom system settings in /etc, saved scripts and maybe a few other things. 

Even if major issues you often can chroot into a broken system from a liveCD and fix it.

---

### Post by matt5555 on 2011-04-30
Tried shift key from BIOS.  Results in terminal screen "sh:grub>"  Is rescue mode only available from a GUI?  If it makes any difference I'm using an HP nc6000 with ATI Mobililty Radeon 9600 video.

---

### Post by oldfred on 2011-04-30
Can you manual boot, then reinstall grub from there. If not use liveCD to reinstall grub's boot loader to the MBR.

Manual boot:
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg

Adjust drive, partition to your install, this example is sdb1 change to your drive, partition:
sh:grub>ls
#If on (hd1,1) or sdb1
sh:grub>ls (hd1,1)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd1,1)/vmlinuz root=/dev/sdb1
sh:grub>initrd (hd1,1)/initrd.img
sh:grub>boot

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by matt5555 on 2011-04-30
I only get the sh:grub prompt.  Tried tab key, but don't know what I'm doing.  I downloaded the iso for 11.04 and booted from CD.  Video is a mess, but can make it out enough to find my files in home.  Tried to backup (of course I didn't make a backup first), but some files won't transfer because of permission rights.  How can I boot from CD and get permissions to files?  I don't see any login prompts?  Am downloading 10.04 iso now in hopes the video improves.  In meantime I'm going to mow the yard before it starts raining.  Sure would hate your job today, but I feel better at least knowing my files are still on the drive.  Thanks for helping.

---

### Post by oldfred on 2011-04-30
Ubuntu's liveCD does not have a password. Just use sudo (gksudo for graphical apps) like on an install and you will be at root. But if working on other partitions be careful not to delete important files.

```
gksudo Nautilus
```

---

### Post by matt5555 on 2011-04-30
Booted from 10.04 live cd.  Now have clear video.  Problem with 11.4 is the video.  Even the live cd will not run correctly on my notebook.  When booting from 10.04 live cd I can locate my old home/me files on the hard drive (only one partition), but when I try to copy them to a usb drive some copy, but most will not copy because I don't have permission.  Says I'm not the owner so I can't change permissions.  When booting from live cd, how do I become owner of my old files on the hard drive so I can get a backup?

---

