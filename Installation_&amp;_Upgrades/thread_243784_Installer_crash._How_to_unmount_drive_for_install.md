---
title: "Installer crash. How to unmount drive for install?"
date: 2006-08-25
forum: Installation &amp; Upgrades
---

### Post by cleentrax on 2006-08-25
The Live CD installer is crashing every time I use it on this machine.

It crashes at 97% on the "Installing system" phase:
```
Error: Unable to install GRUB in (hd0)
```

```
We're sorry; the installer crashed. Please file a bug report at https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug and a developer will attend to the problem as soon as possible. To help the developers understand what went wrong, include the following detail in your bug report, and attach the files /var/log/installer/syslog, /var/log/syslog, and /var/log/partman:

Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 264, in run
    self.progress_loop()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 538, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s; see "
RuntimeError: Install failed with exit code 1; see /var/log/installer/syslog and /var/log/syslog
```

The alternate install CD successfully completes, but upon first reboot, it freezes at GRUB, with just the word "GRUB" on the screen. This is not a grub console, but just a frozen title from the grub page.

This hard drive is visible to fdisk and to the partition tool, and seems to be functioning just fine, minus the ability to install grub. I have tried unsuccessfully to install grub with the grub console from the Live CD. 

fdisk:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/hdi1   *           1        2100    16868218+  83  Linux
/dev/hdi2            2101        2193      747022+   5  Extended
/dev/hdi5            2101        2193      746991   82  Linux swap / Solaris

```

It appears that a partition of this drive is mounted as /target. But when I try to unmount it, I get the message "/target is busy." Would that make the installer fail?

Help, please!

---

### Post by cleentrax on 2006-08-25
More info:

When I try to install grub from the grub console, and I type root (hdi,1) I get "Error 23: Error while parsing number."

From the Live CD, I can browse /target and see that it works, and there is an ubuntu install there, I just can't install grub, or unmount /target!

EDIT: Apparently it is only mounted as /target ***after*** I try a Live CD install. Before I try the install, none of my partitions are mounted. So that's not the  issue.

---

### Post by cleentrax on 2006-08-25
Well, 4 hours later, I think I'm making progress.

My ATA PCI card was actually showing up as drives HDA-HDD, so I moved my boot drive from the motherboard to the PCI card, in the HDA position.

Now Ubuntu installs without an error message, but upon reboot, I get a GRUB error 22. This message usually has to do with a Windows partition, and this drive used to have Windows on it, but it has been formatted. I guess there still may be a problem with grub in the MBR.

I have sucessfully used the grub console to rewrite grub, both to the mbr and the boot partition, with no changes in behavior.

Help, someone!

---

### Post by randell6564 on 2006-08-25
Hi!

Is your MBR Write protected?

Are you setup as LBA in your Bios?

Just try it for Kicks, see what happens!

---

### Post by cleentrax on 2006-08-27
Well, it turned out to be a hardware problem, at least partly. GRUB gets confused by my IDE PCI card. The card is supposedly OK for Linux, but GRUB won't work with it. If I take the card out, then my boot drive boots.

Now I know what the problem is, but I'm not any closer to setting up a functional RAID-5 on my home server. Arrggghh.

---

### Post by randell6564 on 2006-08-27
> **cleentrax said:**
> Well, it turned out to be a hardware problem, at least partly. GRUB gets confused by my IDE PCI card. The card is supposedly OK for Linux, but GRUB won't work with it. If I take the card out, then my boot drive boots.

Now I know what the problem is, but I'm not any closer to setting up a functional RAID-5 on my home server. Arrggghh.

Hi!  This might help you out some regarding your raid device.
[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

good Luck!

---

### Post by cleentrax on 2006-08-27
Thanks, but it's not an SATA card -- it's a 10 year old PCI ATA/100 card.

---

