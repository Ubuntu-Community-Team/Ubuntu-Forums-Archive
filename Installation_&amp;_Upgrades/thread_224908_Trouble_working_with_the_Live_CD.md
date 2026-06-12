---
title: "Trouble working with the Live CD"
date: 2006-07-28
forum: Installation &amp; Upgrades
---

### Post by Prestel on 2006-07-28
System Specs:

Ubuntu version: Dapper Drake Desktop CD 6.06
CPU:  [AMD Athlon 64 3400+](http://www.newegg.com/product/Product.asp?item=N82E16819103010)
Mobo: [Gigabyte GA-K8VM800M Socket 754 VIA K8M800](http://www.newegg.com/product/Product.asp?item=N82E16813128262)
+On-board video: S3 Graphics UniChrome Pro IGP
RAM: 1GB Corsair ValueSelect DDR400
HDD: 250GB Western Digital
BIOS: Forgot to check before posting
Keyboard/Mouse: Both USB, but plugged in with PS/2 adapters.

===========================================

*The goal:*
Bear with me while I get to the point, please. Apparently, Windows XP pre Service-Pack 1 or 2 will not recognize that a hard drive has more than ~130GB. (See [here](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=928&p_sid=CrhENCdi&p_lva=936&p_sp=cF9zcmNoPSZwX3NvcnRfYnk9JnBfZ3JpZHNvcnQ9JnBfcm93X2NudD04NjYmcF9wcm9kcz0mcF9jYXRzPSZwX3B2PSZwX2N2PSZwX3BhZ2U9MQ%2A%2A&p_li=#)). I went ahead and formatted by 250 drive to the max 130 I could and installed windows. After upgrading to Service Pack 2, I could see that the last 114GB or so was there, but unformatted and unpartitioned. Since the windows built-in tools are a pain in the *** to use, I turned to Ubuntu's Live CD and more specifically the Gnome Partition Editor, to resize the partition. **I intend to use GPE to resize the primary partition down to 10GB and create a 2nd, logical partition for use on the rest of the drive, using NTFS formatting.**

*The problem:*
First, the Live CD refused to boot. I got the classic maroonish splash screen with a mouse cursor, at which point the DVD-Rom drive spun down to a stop and we went no further. Well crap, it doesn't like my hardware, I guess. So, I kicked out of the GUIed boot menu into the text-based terminal and booted with this command:

```
live acpi=off noapic nolapic
```

Now this worked (slowly, see below), but my first set of questions are: **What does this do? Do I have to do this because my hardware isn't supported? Is my hardware supported** I checked the [Compatability Lists](https://wiki.ubuntu.com/HardwareSupport) to discover that they don't list my specific motherboard or my specific integrated graphics chipset. Does that mean I shouldn't expect ubuntu to work at all, or does "supported" mean something closer to "we tested with this hardware and know it works" ?

Anyway, the command seemed not to work at first... still hit the maroon screen with the mouse cursor only, but the DVD-ROM didn't spin down so I remained hopeful. Over the next 10-15 minutes, the splash screen appeared, filled with the load icons, one by one, and then gnome desktop loaded in at a frighteningly slow pace. I consider this the second problem problem, and perhaps it's just ignorance on my part. Should it really take that long to load into the desktop? If I'm incorrect here that's fine.

Problem number two arose after loading GnomePartitionEditor. I got into it just fine, setup the partitions just the way I wanted (~10GB primary, then extended w/ a logical part. covering the rest of the disk space), and clicked apply. GPE opened a new window, which I assume was to indicate status, but didn't paint anything into it in the couple of minutes I waited. 

Now comes the point where you may not be able to help... but I come back later in the day to find the computer at a crash screen (whole screen is just lines of text). At the bottom I see "kernel panic."

Being hasty, I didn't write down everything it said, instead quickly rebooting back into the Live CD to open GPE (after waiting 10 minutes for the load). GPE apparently thinks it finished its work. It shows the 2 partitions exactly as I wanted them, and says they're both formatted properly. I do a rescan and get the same results.

I can be certain that no one used the computer and that I initiated no process aside from GPE. I do know that when idle, the LiveCD kicks off some screen saver. Could be graphics related? If GPE actually completed successfully (is there a way to verify that it finished the formatting, or that the partitions are not corrupted?), is there another likely cause for the kernel panic? Could this be Ubuntu not getting along with the hardware?

============================================

So to recap:

1) Given the commands I had to put in to boot with the Live CD (haven't installed Ubuntu), does Ubuntu hate my hardware? Anything I can do about this? Should I expect to have problems when I install Ubuntu on my 2nd hdd?

2) Should the LiveCD really be that slow? (10-15minutes to load into the desktop. long delay on menus and painting of windows)

3) This crash... despite the very little information I could provide... could it be related to hardware?

Apologies for being so verbose. I aimed to be as thorough as I could at this point.

---

### Post by tseliot on 2006-07-28
> **Prestel said:**
> So to recap:

1) Given the commands I had to put in to boot with the Live CD (haven't installed Ubuntu), does Ubuntu hate my hardware? Anything I can do about this? Should I expect to have problems when I install Ubuntu on my 2nd hdd?
It is likely that Ubuntu's kernel doesn't support your hardware (i.e. your motherboard).

If the livecd doesn't work fine I wouldn't suggest you to install Ubuntu (yet).

> **Prestel said:**
> 2) Should the LiveCD really be that slow? (10-15minutes to load into the desktop. long delay on menus and painting of windows)
No, it shouldn't

> **Prestel said:**
> 3) This crash... despite the very little information I could provide... could it be related to hardware?
Try booting the Livecd in Safe mode

---

