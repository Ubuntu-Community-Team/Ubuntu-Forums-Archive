---
title: "Old BIOS"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by astro4travel on 2007-10-04
Hello everyone. I'm new to the forum so here goes. I recently installed Xubuntu via download cd to my older "NEC ready" (1998) 300mh. computer. It used to have Windows 98 on it. Well, when I boot up I receive the message, " ACPI=force is required to enable ACPI. BIOS age (1998) fails "2000" cutoff." The Xubuntu started and booted anyway, but it will not shut the computer down when I choose to shut down with the "shut down menu" in Xubuntu.
Not really sure what to do from here. Any help or suggestions would be helpful. Thank you in advance. Michael

---

### Post by astro4travel on 2007-10-04
I didn't add the smiley faces. It should read (1998). Thanks

---

### Post by Soybean on 2007-10-04
Heh... under the box for posting (unless you're using "quick reply") is a checkbox that says "Disable smilies in text." 8) is that smiley face with the glasses, so (1998) gets parsed as "(199smiley"

As for your problem... it *sounds* like you just need to add the kernel option "acpi=force". ACPI is rarely that simple, but it's worth a shot.

You can add kernel options either by editing the file /boot/grub/menu.lst (permanent change), or by editing the grub menu while you're booting (one time change -- good for testing to see if it's going to work).

There's documentation that covers it all ([https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)), but basically all you need to do to test this is turn on your computer, press "e" when the grub menu comes up, add "acpi=force" to the end of the kernel line, and then continue booting. If everything works properly, then edit /boot/grub/menu.lst to add the option permanently, as described in that link.

---

### Post by astro4travel on 2007-10-05
Problem solved. Dictched Xbuntu. Installed Debian. Shuts down fine now.

---

### Post by jimmywu013 on 2007-10-18
I have the same thing - except my BIOS age is 1999.  Does this mean acpi is not supported?
I have to manually shut-down my computer by pressing the power button after it gets to the System halted message, and neither suspend nor hibernate works properly (both result in a reboot) so I don't think acpi is running.  In that case, should I disable acpi with a kernel boot option (noacpi acpi=off) to save system resources while running, since it doesn't seem to be doing anything?

EDIT: basically my question is in my case, should I use acpi=force or acpi=off noacpi?

Thanks,

Jimmy

---

### Post by DonQuichote on 2007-10-18
In this thread, it was explained clearly:
[http://ubuntuforums.org/archive/index.php/t-22041.html](http://ubuntuforums.org/archive/index.php/t-22041.html)

For my laptop (HP Omnibook XE3), I had the same problem, plus the BIOS trying to do a memory backup when my battery was low. Especially the backup was a real problem, as the restore was always corrupt. So after 10 minutes backup-and restore, you'd still lost all your data (if you were lucky. Otherwise you'd loose the integrity of any ext2 partitions also).

The above threat solved both my problems.

Caveat: if your BIOS does a good job in a low-battery situation, the above action can disable that also. But it is very simple to remove the boot option again.

Good luck.

---

### Post by Sef on 2007-10-18
> I didn't add the smiley faces. It should read (1998). Thanks

You can click on disable smileys in text.  It is under Additional Options.  If you already have saved it, then Edit > Go Advanced to find it.

---

### Post by UKTonyK on 2007-10-19
COmpletely new to this, I mean completely.

My BIOS is an IBM T20 from 2004 ( according to the IBM site) but I still get the old bios error when trying to boot up from the Live CD of Gutsy Gibbon.


Ignore that, the site says 2004, but I think that is when the doc was last edited, the BIOS is in fact from 21 Dec 1999.

---

