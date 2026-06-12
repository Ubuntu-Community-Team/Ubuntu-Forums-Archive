---
title: "Compaq Deskpro Install Problems"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by therian on 2008-08-12
I have a Compaq Deskpro EN P3 733 mhz
with 384 meg of ram, and 40 G Western Digital hard drive
(set as master on primary ide/DVD-cdrom NEC 3550 is slave)

It won't load linux (ubuntu or SuSE) onto the hard drive for love or money.

I used a win98SE floppy and fdisk'd the hard drive.  Created Primary Dos Partition, the whole disc. Next I did an fdisk /mbr to put a boot block out there. When I boot to the hard drive, it tells me there is no os.  Which if it tells me that much, I know the MBR is there, and it's working.  Here's the problem.

I've played with the APIC (Advanced Programmable Interrupt Controller) settings.  Disabling it, would have forced the machine into legacy mode.  

Anyway I don't think that's the problem.  Ubuntu just goes into a reboot loop.  It comes up, looks around and reboots.  APIC or NOAPIC.

SuSE otoh, gets far enough along to tell me it can't find the hard drive?  Huh?  I can alway get that message there is no operating system on the hard drive - so I know the MBR is there.  I don't want to
install "over the top" of windows, I want to make windows go away and install it 100% linux.  But everything I've tried fails.

One thing I DID do, is I update the BIOS as well.  Well.  I had a Version 2 bios, it now has a version 3 bios (latest and greatest).  Umm the latest BIOS is still over 6 years old!

What's the trick?  Is this machine so old, that windows is all it will ever run?  If so, maybe I ought to just donate to some school.  It DID have WINDOWS XP running on it, when I got it.  And that seemed fine.

I also ran the built in disc diagnostics, and that ran clean.  

Wayno G.

---

### Post by Kevbert on 2008-08-12
You're right on the limit for memory for a Ubuntu standard install.  With Suse I believe you need more.  You could try Xubuntu (alternate CD) install, but even that may run slowly.  The alternate CD is a text based installer program.  If you want to try the linux platform you could try Puppy, Damn Small Linux or Slax.  These will run better based on your PC specs.

---

### Post by therian on 2008-08-12
Well --

My problem at the moment is not memory, it can't find the hard drive, for love or money.  So we need to solve that issue first, then address the memory.

Wayno

---

### Post by therian on 2008-08-12
This says I'm okay ---

[http://www.easy-ubuntu-linux.com/ubuntu-system-requirements.html](http://www.easy-ubuntu-linux.com/ubuntu-system-requirements.html)

Before installing Ubuntu, you should also check your computer against the hardware requirements. The system requirements for Ubuntu are as follows:

    * 700 MHz or better processor
    * 3GB of available disk space
    * 256MB of memory (RAM)
    * CD-ROM drive
    * Ethernet interface
    * VGA graphics interface 

So memory is not the issue -- it's hard drive.

Wayno

---

### Post by therian on 2008-08-12
I tried the text installer of ubuntu as suggested, and sure enough, it also says it can't find the disc drive.  So that's the problem.

Wayno

---

### Post by therian on 2008-08-13
Eww -- something I posted earlier sounded fishy.  So I said -- hey I'll just disable IDE1 since I am not using it, maybe that's the problem.

Ahh.   What I discovered might be interesting.

IDE0 (primary) Contains the western digital 40G drive set as master.  
IDE1 (seconary) Contains the NEC 3550 DVD/Burner set as master.

Now that works obviously for windows -- and the bios seems to be happy with it, but Linux can find the hard drive.  It sees the cdrom no problem --- yes i just checked the hard drive - -their is a pin set up as master on ide0 for the hard drive.  And their is a pin in the cdrom set up as master on ide1.  Like I said the Bios is seeing each drive fine, and it works great in windows.  Just ubuntu (text installer), and Suse 10.3 can't seem to find the hard drive.

Wayno

---

### Post by therian on 2008-08-15
This turned out to be the problem -- Good call!

I was able to install without a problem, and the system boots immediately, instead of waiting 30 seconds.


Wayno

---

older western digital drive... they had a quirk in which if they were the
ONLY drive on a cable, you really should remove the jumper entirely,
otherwise it wouldn't be found properly.

The DVD is fine, it's on it's own IDE bus and won't affect, or be affected by this.

Oddly enough, it might have worked if both were on the same cable... such was the WD jumper select issues.

Loni
--
L R Nix
[email]lornix@lornix.com[/email]

---

