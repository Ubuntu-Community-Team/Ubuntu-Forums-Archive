---
title: "Kernel update issue   HDE: lost interrupt"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by iitywygms on 2007-06-01
I did the update a few days ago, to -16. Cannot boot into it. When I use recovery mode the boot process stops and display HDE: lost interrupt.  I have searched the last few days and see quite a few issues with this latest update but none seem to match mine.  Usually after updates I see a fix but not this time.
Not sure what information is needed to fix this so I will just ask, Help!

---

### Post by iitywygms on 2007-06-02
Bump

---

### Post by iitywygms on 2007-06-02
Anybody?

---

### Post by flashkot on 2007-06-02
Same problem, and don't know what to do...

---

### Post by ChuckADD2 on 2007-06-05
Same problem -- upgrading from edgy to feisty -- cycles on:

hde: dma_timer_expiry: dma status == 0x24
hde: DMA interrupt recovery
hde: lost interrupt
hde: dma_timer_expiry: dma status == 0x24
hde: DMA interrupt recovery
hde: lost interrupt
...etc

Very frustrating. Any ideas?

---

### Post by iitywygms on 2007-06-05
One more time. HELP!

---

### Post by SFCampbell on 2007-06-10
I had the same issue after auto-updating to the .16 kernel, and since that time I had chosen to boot the .15 kernel from Grub (which still worked) instead.  I then read from this forum entry ([http://ubuntuforums.org/showthread.php?t=468313]("http://ubuntuforums.org/showthread.php?t=468313")) that a more recent update to the kernel .16.29 resolved the issue.  However, the update only appeared when booting to the .16 kernel.  

After attempting multiple times to boot into recovery mode of the .16 kernel (3 times when I tried) it finally reached a root command prompt.  Run "apt-get update" a few times and "apt-get upgrade" from this prompt  and it will download the latest kernel image.  Use the "shutdown -r now" command to reboot and the latest revision of the .16 kernel should then boot successfully from Grub.

Campbell

---

### Post by jdurand on 2007-09-13
I've also been seeing hda: lost interrupt, anywhere from maybe twice a day to once every couple of days.  No other error messages.  The system has been running for a couple of weeks.

There are two SATA hard disks set up as RAID-1 in hardware (using the motherboard controller).  The motherboard bios says the RAID volume is fine.

System:
Ubuntu Feisty
ASUS PvD2-MX SE motherboard
Intel dual core E2160
1GB DRAM
two WDC WD1600JS-22N drives

Other than the hda errors, it seems to working quite nicely.  I'm slowly moving our server over to it, so far this system is handling web and local DNS for several low-volume domains along with Samba (common files for our Windows machines).  The mail server is still on the old Mac, so it's not super busy.

---
update
Yesterday I received two of those lost interrupts with an ide-cd: error in the middle (I wasn't using the CD and there's nothing in it):
Sep 14 10:49:51 Gandalf2 kernel: [264474.759331] hda: lost interrupt
Sep 14 11:08:06 Gandalf2 kernel: [265568.799078] ide-cd: cmd 0x1e timed out
Sep 14 11:08:06 Gandalf2 kernel: [265568.799086] hda: lost interrupt

And today I had three:
Sep 15 10:20:41 Gandalf2 kernel: [348994.329253] hda: lost interrupt
Sep 15 10:36:25 Gandalf2 -- MARK --
Sep 15 10:56:25 Gandalf2 -- MARK --
Sep 15 11:13:35 Gandalf2 kernel: [352163.812180] hda: lost interrupt
Sep 15 11:27:53 Gandalf2 kernel: [353019.729014] hda: lost interrupt

Does ANYONE have any idea of what's up?

---

### Post by jdurand on 2007-09-16
Ok, getting this figured out.

I'm moving from OS X, so my understanding of *nix has been a bit corrupted (started on a Sun, then a Mac, now Ubuntu).

hda: is my DVDROM.  Why it's getting errors while sitting there doing nothing is a good question, but at least it's not my hard disk.  I'll check the cable on it.

sda: is my RAID volume and seems to be working perfectly.

sdc: is a USB drive I currently have plugged in.

Makes much more sense now.

---

