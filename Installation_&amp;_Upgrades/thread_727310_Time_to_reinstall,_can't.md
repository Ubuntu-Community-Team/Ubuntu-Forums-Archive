---
title: "Time to reinstall, can't"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by retrosteve on 2008-03-17
Ok,  I have finally succeeded in installing  GG 7.10 on a spare computer.  hardware config:  HP desktop Pentium IV, (circa 2004) with 40GB IDE drive, 250GB SCSI drive, DVD/RW (on SCSI), Belkin wireless FD57050.

I took out the extra drive (250GB) and the Belkin to do the original install from CD.   It worked.

Then I added the 250GB drive back (as slave) and the CD drive remained master on that cable.  I added the Belkin back too.

Apparently all this was a mistake.  The Belkin wifi is invisible, and one of the two NTFS partitions on the 250GB drive is also invisible.  Reading thru other posts here convinces me I should have had them all present when I installed the OS.

Well that's ok, let me try to reinstall it from scratch.

What's this?  I can't.  The thing won't boot from CD drive any more, even with BIOS boot menu asked to boot first from CD.  It tries and fails.   Though I can read the CD drive from within Ubuntu.

Ok, what's next, oh great ones?  I want to recognize all my devices, and I don't mind reinstalling.

Again, I can't find the CD drive at boot time. I could before, but not any more. CD Drive is SCSI internal.    I have a second external USB CD drive which also is not found at boot time.

Stuck.  Pls help...

---

### Post by retrosteve on 2008-03-17
Still stuck!  Help?

---

### Post by wolfen69 on 2008-03-17
try resetting your BIOS to default setup.

---

### Post by retrosteve on 2008-03-17
Never thought of that.   It worked.

Thanks very much!

---

### Post by retrosteve on 2008-03-17
> **retrosteve said:**
> Ok,  I have finally succeeded in installing  GG 7.10 on a spare computer.  hardware config:  HP desktop Pentium IV, (circa 2004) with 40GB IDE drive, 250GB SCSI drive, DVD/RW (on SCSI), Belkin wireless FD57050.

I took out the extra drive (250GB) and the Belkin to do the original install from CD.   It worked.

Then I added the 250GB drive back (as slave) and the CD drive remained master on that cable.  I added the Belkin back too.

Apparently all this was a mistake.  The Belkin wifi is invisible, and one of the two NTFS partitions on the 250GB drive is also invisible.  Reading thru other posts here convinces me I should have had them all present when I installed the OS.

Well that's ok, let me try to reinstall it from scratch.

What's this?  I can't.  The thing won't boot from CD drive any more, even with BIOS boot menu asked to boot first from CD.  It tries and fails.   Though I can read the CD drive from within Ubuntu.

Ok, what's next, oh great ones?  I want to recognize all my devices, and I don't mind reinstalling.

Again, I can't find the CD drive at boot time. I could before, but not any more. CD Drive is SCSI internal.    I have a second external USB CD drive which also is not found at boot time.

Stuck.  Pls help...

And now, I am able to boot and install from the CD once more.  I did so.

Rebooting gives error message "Cannot boot from selected partition".  

That's weird, I told it to install into and  boot from the C: Drive as before.  Getting frustrated.

---

