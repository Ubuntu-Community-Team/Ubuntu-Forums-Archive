---
title: "XP fails to boot after Gutsy install"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by harry-smith on 2007-10-23
... unfortunately yes, I still have to use XP for some things, however having just finished dual booting the wife's laptop I assumed that doing the same with my desktop would be a straighforward affair.

Problem:
During boot I get the Grub menu with an option to boot into XP, selecting this option even brings up the boot options from boot.ini, however no matter which XP boot option I choose I always get the same response

[FONT="Courier New"]<Windows Root>\system32\ntoskrnl.exe missing or corrupt[/FONT]

I know that the XP install is still good as I can easily boot back into XP by firing up the Windows Repair Console and using the FIXMBR command to replace the Grub loader with the original MBR.  This ofcourse means that I can no longer boot to Ubuntu :(

To be honest I'm at my witts end with this problem, I've been trawling the net for days looking for an anwer, but nothing has as yet solved this, any help would be appreciated.

---

### Post by Pumalite on 2007-10-23
From Ubuntu, at the Terminal, post:
cat /boot/grub/menu.lst

---

### Post by harry-smith on 2007-10-23
Thank you for the swift reply and here is the contents of menu.lst as requested,  the rest of the file is all commented out except for the default and timeout sections, but here is the interesting bit

[FONT="Courier New"]
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=022eec0e-074a-4abf-8ba6-98d7cf5fb86b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=022eec0e-074a-4abf-8ba6-98d7cf5fb86b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
[/FONT]

---

### Post by Pumalite on 2007-10-23
Well, obviously we need to include XP. I'll need:
sudo fdisk -lu

---

### Post by harry-smith on 2007-10-24
Hello again, hopefully the following will shed some light on this problem.  The Linux partitions were created manually during install, both are logical partitions.


[FONT="Lucida Console"]
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x002c002c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81915434    40957686    7  HPFS/NTFS
/dev/sda2        81915435   156296384    37190475    5  Extended
/dev/sda5        81915498   146368214    32226358+  83  Linux
/dev/sda6       146368278   156296384     4964053+  82  Linux swap / Solaris
[/FONT]

---

### Post by Pumalite on 2007-10-24
You might need to fix your Windows first and later to reinstall Grub.
Boot your XP installation CD>hit 'r' for Recovery>FIXMBR>FIXBOOT
This will leave you without Grub and Ubuntu.
Fix this by following: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by harry-smith on 2007-10-25
I followed your advice...

After FIXMBR and FIXBOOT, the Grub menu disappears and XP boots as expected, unfortunately after I re-installed Grub I am back to square 1, Ubuntu works XP complains about ntoskrnl.exe

Below is the output from Grub whilst I was replacing the XP mbr, any ideas?

[FONT="Courier New"]
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,4)

grub> root (hd0,4)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,4)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> quit
[/FONT]

---

### Post by Pumalite on 2007-10-25
Maybe the only thing you need to change is the Windows entry in menu.lst once you have it reinstalled:
From this:
[FONT=Courier New] title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
To this:[/FONT][FONT=Courier New] 
title		Microsoft Windows XP Professional
rootnoverify		(hd0,0)
makeactive
chainloader	+1
Let's see what happens.
[/FONT]

---

### Post by harry-smith on 2007-10-25
Okay, replaced Grub with the XP MBR, booted Ubuntu with the Live CD, edited menu.lst and reinstalled Grub as before.

.... no joy I'm afraid

XP still complains about missing or corrupt ntoskrnl.exe, 

I have debugging enabled during the Windows boot.  XP seems to be able to find ntkrnlpa.exe which I understand loads prior to ntoskrnl.exe, I'm stumped!!

---

### Post by Pumalite on 2007-10-25
ntoskrnl.exe is a know bug in XP dual boot situations I'm afraid. A Windows bug, mind you. Sorry.

---

### Post by Pumalite on 2007-10-25
> **harry-smith said:**
> Okay, replaced Grub with the XP MBR, booted Ubuntu with the Live CD, edited menu.lst and reinstalled Grub as before.

.... no joy I'm afraid

XP still complains about missing or corrupt ntoskrnl.exe, 

I have debugging enabled during the Windows boot.  XP seems to be able to find ntkrnlpa.exe which I understand loads prior to ntoskrnl.exe, I'm stumped!!

OTOH, you were supposed to edit menu.lst after you had reinstalled Grub and booted Ubuntu from the hard drive; otherwise the changes to menu.lst don't stick.

---

### Post by harry-smith on 2007-10-25
Believe me, I never lost the faith, I knew deep down that any dual boot problem had to originate with Microsoft.  Seems I need to read up on ntoskrnl a bit, if you can point me towards any stes / forums etc discussing this issue that would be most appreciated.

Thank you for you time helping me with this issue.

Just saw your previous post am trying this now

---

### Post by harry-smith on 2007-10-25
Just went though the FIXMBR, install Grub, edit menu.lst procedure again.  Here is the order in which I performed each step.

[LIST=1]
[*]Booted into the Windows Recovery Console
[*]FIXMBR followed by FIXBOOT
[*]Booted into XP, it works
[*]Inserted the Gutsy Live CD and rebooted
[*]Re-installed Grub
[*]Booted into Ubuntu via the Grub menu
[*]Edited menu.lst as suggested
[*]Rebooted to the Grub menu
[*]Select Windows and to my surprise..... no just kidding :) still nothing but a blank screen and an error message
[/LIST]

---

### Post by Pumalite on 2007-10-25
What's the error message?

---

### Post by harry-smith on 2007-10-25
Same as before

[FONT="Courier New"]
<windows Root>\Windows\System32\ntoskrnl.exe is missing or corrupt
[/FONT]

---

### Post by Pumalite on 2007-10-25
Sorry. Google your 'missing file' error message and you'll find dozens of hits. Good luck.

---

### Post by harry-smith on 2007-10-25
yup, I think I have read most of them over the past few days :).

Oh well, while we have been posting this evening I have installed Wine and, to be honest, my applications run better under Ubuntu than they ever did through XP.

thank you again and keep up the excellent work.

---

### Post by saltfish on 2007-10-26
I was having the same problem of not being able to booting into XP Pro after installing gutsy.

To solve the problem, you have to install XP first then install gutsy. When asked to partition the disk choose the option to manually edit the partitions and be sure to create a /boot partition of at least 50M where grub can be installed. You can follow the steps previously outlined in this thread or here [http://digitalgraphy.wordpress.com/2...ows-ntxpvista/](http://digitalgraphy.wordpress.com/2...ows-ntxpvista/).

Just be sure to create a /boot partition of at least 50M for grub.

---

### Post by harry-smith on 2008-02-11
Thank you to everyone that has replied to this thread, I have finally been able to solve this annoying problem.

I have recently upgraded my motherboard from an MSI 975x Platinum PE to an Asus Striker Extreme with the Nvidia chipset.  After re-installing Ubuntu, I can now boot both Ubuntu and XP as expected from the GRUB boot menu.  Apart from the replacement motherboard and a couple of new graphics cards all other components in the box are the same, same processor, hard drives, memory etc.  This leads me to think that the problem was the previous chipset and specifically the hard drive controller.

I hope this helps any of you that may be in the same situation as myself.

---

