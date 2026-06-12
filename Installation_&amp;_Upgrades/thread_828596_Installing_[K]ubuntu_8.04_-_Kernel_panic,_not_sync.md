---
title: "Installing [K]ubuntu 8.04 - Kernel panic, not syncing (Unable to mount root fs) error"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by TerranRich on 2008-06-13
Hey all, Linux newbie here. Windows defector, and all...

So whether I'm installing Ubuntu 8.04 or Kubuntu 8.40, I get the same problems. If I just try to run the Live CD, or if I try to install [K]ubuntu, it halts with the following errors, every time:

ACPI: EC: acpi_ec_wait timeout, status = 0, expect_error = 1
ACPI: EC: read timeout, command = 128

If I press F6 and manually enter in "noapic nolapic" like the Help menu suggests, it gives the following error:

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(104,1)

I wrote it down correctly. Both ISOs do it. The Ubuntu is the Live CD obtained from Ubuntu.com, and Kubuntu is a downloaded ISO burned to a CD. I downloaded the ISO several times, and burned each several times, and still the same error.

Please be gentle and keep in mind that I'm new to all this. What can I do to help make it work? I have an Intel T2250 1.73GHz CPU with 1 GB of RAM, with Windows XP installed. I was hoping to format the hard drive with the Live CD before installing [K]ubuntu (I'm assuming that's possible), but if there is another easier way, by all means, let me know.

Thanks!

---

### Post by DynamicStu on 2008-08-30
I'm getting a similar error from the CD running Alternate installer on a PowerPC machine (a Hardy Ports release). I hope your problem was solved!

---

### Post by gatenby_jp on 2008-08-31
So you are not able to run Live CD without installing?

Try going in to bios and turn off all power management features ... particularly acpi and apic ... then try again.

If it still fails see if you can run chkdsk /p from your windows install disk ... boot on the xp cd at first screen select r for repair ... then type chkdsk /p

Now try your linux again

---

