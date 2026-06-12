---
title: "Interrupted Ubuntu install and now I have a 120gb dead partition"
date: 2016-06-08
forum: Installation &amp; Upgrades
---

### Post by coryhensarling on 2016-06-08
So I was installing Ubuntu onto my old (like really old) Acer from a few years back. Everything was going fine, if not a little slow, when I decided to take the dog for a walk. I closed the lid (that was the mistake, but how and why would that cause problems?) and when I came back the installation had been interrupted and I only had a black command looking screen that kept saying something like (I can't remember the exact wording) "drive not found" and "could not initiate". I waited for around 5 maybe 10 minutes  hoping it was just being slow, but it wasn't. I rebooted. Whoops. 

Here's the biggest whoops, I had partitioned 120 gigs to Ubuntu but now I can't get the old install usb to work nor can I get windows 7's disk manager to do anything with the partition so I can start over. On each boot Windows 7 tells me that it needs to check the drives, and I say ok, and it says the disks are ok, but they aren't ok and now I'm not ok. 

I may be freaking out because I'm new to all of this and I haven't spent much time messing with it since the boo boo, but I was wondering if anyone might know what happened to save me some time and headache?

---

### Post by oldfred on 2016-06-09
If really old system, it may not run Ubuntu anyway. 
Most old systems need a lighter weight gui as Unity needs newer video hardware.
My 2006 laptop would barely run Ubuntu, so I installed fallback.
Most install Lubuntu or Xubuntu.

We cannot tell what you did. 
But often interruption of process at minimum needs chkdsk for NTFS Windows or fsck for Linux ext4 formatted partitions.
And if file repair does not work then re-install and restore data from your backup is often the only recourse.

You do need to get a live installer booting to see what is where.
       May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Impavidus on 2016-06-09
To me "really old" does not equate to "from a few years back". Is that 3 years, 7 years, 12 years? Some hardware specs (RAM, CPU, graphics) may be useful. Closing the lid may have forced the laptop into sleep mode, interrupting installation and without the software necessary for wake-up installed, this caused problems. Installation should take about 20 to 40 minutes.

You're lucky you can still boot Windows. I don't know why Windows' disk checks don't work, but I read that you may have to run them several times before everything is all-right. So have you rebooted Windows several times?

---

### Post by X-RED_Tech on 2016-06-09
... And your partition isn't dead...

Windows not being able to read or work with it is normal and expected but you can, from Windows, delete it and end up with unallocated space and just start over. Or just boot a Ubuntu live session, open Gparted and partition in advance before installing Ubuntu again, this time making sure you don't suspend the machine while installing, I mean don't close the lid (IMO, a person who doesn't know this isn't what I would call "qualified" to manage the installation of operating systems but if don't have anybody else we'll try to help you).
You don't need Windows or any other previously installed OS to manage disk and partitions. You can start over and do everything from the Ubuntu installer and/or live session.
Your 'problem' should be ridiculously simple to solve so, first of all, calm down!

---

