---
title: "Dual Boot w/ XP; error 13 invalid executable"
date: 2009-03-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by toussaab on 2009-03-25
Hello,

I just updated my system to Jaunty 64 Ubuntu.  It was running Kubuntu 64 8.04 with KDE 3.5.10 and XP Pro x64.  Due to constant network issues with KDE 3 and 4, I switched to Ubuntu Jaunty and my network (Samba) issues are resolved.

I did an install of Jaunty 64-bit on top of the existing Kubuntu, with a 250MB /boot partition as ext3, 10GB root partition that was ext3 and is now ext4, and the /home partition was left alone and the user account imported during the installation.  The Jaunty itself is working great.

However, I cannot boot into Windows now.  GRUB gives "error 13: invalid executable format" when trying to load XP.  The stupid XP has a bug where the recovery console (from the disk) can't accept the true admin password, so I cannot run a fixmbr to restore access to the Windows side.  So, I have to solve this puzzle from GRUB.

The boot drive is a 300GB PATA drive with many partitions.  BIOS sees this as the first drive, but from Intrepid on, this is now sdd as there are 3 other SATA drives also.  I've attached the fdisk for the boot drive and the menu.lst file from GRUB.

It's tax time for me, there isn't a WINE package for Jaunty yet, and I need some pointers to get this resolved!

Thanks in advance for any assistance on this issue.

---

### Post by Reiger on 2009-03-25
There is a wine. Old, sure. But tax software usually doesn't demand the latest and greatest anyways. :shrug:

(Alternatively if you must have the latest wine, you could try building from source...)

---

### Post by Bakon Jarser on 2009-03-25
Also, the intrepid wine repository works fine in jaunty.  You could probably get windows to boot with a super grub disk.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

You could also install windows in a virtual machine.  I've also seen HowTo's about booting your existing windows partition in a virtual machine.

---

### Post by junior aspirin on 2009-03-25
it's a grub issue looking at the wrong partition... or something along those lines. I had it before.

a quick google brings up this:
[http://ubuntuforums.org/showthread.php?t=282545](http://ubuntuforums.org/showthread.php?t=282545)

---

### Post by toussaab on 2009-03-25
RESOLVED!

I changed (hd3,0) to (hd0,0) in the /boot/grub/menu.lst file, and that worked.

Looks like there is a discrepancy [still] between GRUB and the way Ubuntu maps the drives.  When I upgraded another machine from Hardy to Intrepid (Kubuntu), it was an epic fail as all the drive mappings were screwed up in Intrepid and I got the famous read only filesystem issue.

on to the next problems...

Thanks!

---

### Post by Bakon Jarser on 2009-03-25
> **toussaab said:**
> RESOLVED!

I changed (hd3,0) to (hd0,0) in the /boot/grub/menu.lst file, and that worked.

Looks like there is a discrepancy [still] between GRUB and the way Ubuntu maps the drives.  When I upgraded another machine from Hardy to Intrepid (Kubuntu), it was an epic fail as all the drive mappings were screwed up in Intrepid and I got the famous read only filesystem issue.

on to the next problems...

Thanks!

From my experience this seems to be a problem with the order that the bios boots the drives.

---

### Post by kevpan815 on 2009-03-26
Mainstream Support 4 XP Ends On 04/14/2009, Just 2 Let You Know.

---

### Post by Bakon Jarser on 2009-03-26
> **kevpan815 said:**
> Mainstream Support 4 XP Ends On 04/14/2009, Just 2 Let You Know.

They'll extend that.  They can't afford to let xp die.

---

