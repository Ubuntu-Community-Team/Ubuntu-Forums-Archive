---
title: "Please Help!! Ubuntu install to USB has corrupted Windows HD"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by dannyf on 2010-01-30
Please help. I tried to install ubuntu purely onto a USB stick but it has corrupted my Win XP hard drive. I think I should have taken the boot choice option. Without the USB stick, when I tried to boot from HD it reported GRUB not found. I have used Windows install CD recovery console to fixboot and fixmbr but now when I boot from HD it says NTLDR not is missing. Now this is all made much worse in that the HD is scrambled with McAfee Endpoint Encryption. So now from the Win recovery consol if I type 'DIR' I just see loads of garbage.

So my question is this, will the Ubuntu install to USB have mucked up the whole disk or just the boot sector - so is my file system still there & just needs the McAfee Endpoint sorting out?

Thanks in advance!
Danny

---

### Post by quixote on 2010-02-01
Unless you told the Ubuntu install disk to format your Windows drive, it won't touch that.  And I suspect you did NOT tell it to do that ;).

What's happened is that the bootloader (grub) lost its tiny mind.  You've put the Windows bootloader back on, so now your system is just as if it had only Windows on it.  McAfee has got to have some way of recovering after a hard drive issue, so as you say, as far as that goes it's just a matter of sorting that out with McAfee.

If you'd later like to access your Ubuntu on USB again, the simplest thing might be to just change your boot order in the BIOS.  When your computer starts booting, there's a brief message saying "press [something] for setup."  Press it in the couple of seconds they give you, go to the boot tab, and move the USB up above the HD in the boot order.  (Best is probably CD > USB > HD)  Then you have to shutdown Ubuntu, and remove the USB if you want to boot into Windows.

---

