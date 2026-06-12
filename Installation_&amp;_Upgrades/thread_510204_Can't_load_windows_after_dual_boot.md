---
title: "Can't load windows after dual boot"
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by matthewordie on 2007-07-26
I setup the newest Ubuntu on a new partition on my HDD with a previous vista install. I deleted the partition with the ubuntu install but GRUB still wants to try and load and I can't boot into windows. Any ideas what I can do? I'm very very new to linux (if you can't tell already).

---

### Post by confused57 on 2007-07-26
> **matthewordie said:**
> I setup the newest Ubuntu on a new partition on my HDD with a previous vista install. I deleted the partition with the ubuntu install but GRUB still wants to try and load and I can't boot into windows. Any ideas what I can do? I'm very very new to linux (if you can't tell already).

If you have a Vista install DVD(not a recovery disk), you can use the bootrec /fixmbr command to restore your mbr:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

If you don't have a Vista install DVD, you might want to reinstall Ubuntu...boot into Vista and use MbrFix to restore your mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)
there are directions on the download site for restoring Vista's mbr

---

### Post by Auburn Boy on 2007-07-27
> **confused57 said:**
> If you have a Vista install DVD(not a recovery disk), you can use the bootrec /fixmbr command to restore your mbr:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

If you don't have a Vista install DVD, you might want to reinstall Ubuntu...boot into Vista and use MbrFix to restore your mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)
there are directions on the download site for restoring Vista's mbr

Greetings,
 
 Since this is a new thread, and it addresses my issue also, I'll ask this:

Is there a similar recovery method for a Windows XP system?

I installed Ubuntu on an HD where my XP install resides, and now I can't boot.  Ubuntu loaded a partition that crosses the 1024 boundary, and GRUB just {blinks} by then I get a reboot.  Rinse, lather, repeat..,

Will fixing the MBR allow an XP boot?  If so, what's the best method to accomplish this?
 
 Thanks,

---

### Post by merlinus on 2007-07-27
IIRC, you can boot from your xp install cd, and choose recovery mode.

That should offer an option to fix the mbr.

-merlin

---

### Post by Auburn Boy on 2007-07-27
> **merlinus said:**
> IIRC, you can boot from your xp install cd, and choose recovery mode.

That should offer an option to fix the mbr.

-merlin

Hi,

Thanks!  I just tried that, the recovery console is installed, but I don't have the password for it.  Grrrr!! :mad:  I'm going to try to "break" the password later..,

I copied NTldr,  NTDETECT, and BOOT.INI to a floppy.  That gets me booted into XP.  :)

Now I just have to figure out how to/what to fix.

Does Ubuntu NOT like to boot on a partition that spans the 1024 cylinder limit?

 So much to learn, so little time..,

 Neil

---

### Post by Auburn Boy on 2007-07-27
> **matthewordie said:**
> I setup the newest Ubuntu on a new partition on my HDD with a previous vista install. I deleted the partition with the ubuntu install but GRUB still wants to try and load and I can't boot into windows. Any ideas what I can do? I'm very very new to linux (if you can't tell already).

I found a fix to let you boot into XP from a floppy..,  I think the same works for Vista.  See my most recent prior post and give that a try..,

Good Luck! 

I'll try to keep up with your progress.

---

