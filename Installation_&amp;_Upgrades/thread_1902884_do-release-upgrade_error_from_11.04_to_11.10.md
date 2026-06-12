---
title: "do-release-upgrade error from 11.04 to 11.10"
date: 2012-01-01
forum: Installation &amp; Upgrades
---

### Post by MAFoElffen on 2012-01-01
I have an Ubuntu 11.04 Server. Original install was on this box 11.10.  Past do-release-upgrade to 11.04 went fine.  Does "apt-get" and "aptitude" updates/upgrades fine with no errors. But on do-release-upgrade to 11.10... errors out.

```

$ sudo do-release-upgrade
Traceback (most recent call last)
File "/usr/bin/do-release-upgrade", line 5, in <module>
    import apt
File "//usr/lib/python2.7/dist-packages/apt/_init_.py, line 24, in <module>
    from apt.package import Package
File "/usr/lib/python2.7/dist-packages/apt/package.py", line 27, in <module>
    import subprocess
File "/usr/lib/python2.7/subprocess.py", line 432, in <module>
    import pickle
EOFError: EOF read where object expected.

``````

Hardware:

HP NRL-LS mobo, 
      Serverworks chipset
      3.5GB ECC RAM
      Adaptec 29160 SCSI Controller
      LSI MegaRAID Series 493 Elite 1600 SCSI Controller
2 PATA's internal
11 SCSI's external
        Gateway DataStation Ultra-11
        As RAID 5...

```Another weird thing on this box... that shouldn't be related, but I should probably mention just in case- The RAID won't mount on boot (via the Adaptec nor the LSI) but would mount manually without a hitch immediately after login, from the CLI. But it does mount via both adapters if I slow down the boot...  Like I said, I don't think that's related, but who knows at this point. Argh...

Anyone know what might be corrupted or missing so I can upgrade to 11.10?

---

### Post by MAFoElffen on 2012-01-04
After a week of fighting this with versions 10.10 through 12.04 alpha 1... The install menu'ed selections and progress bars happen in tty1. All the terminal installation status and messages happen on tty4... Some the errors would start with errors installing the base system... Some trace back to a main package not being downloaded.

This was after the installer said it successfully configured network devices and gotten the time from the internet... It lied.  Using 12.04, it finally came up with a dialog saying it was missing a non-free firmware for the Network Card.  I put the unpacked tar ball on a USB drive... but it still didn't find it.

So... Threw in an Intel PCI Networkwork Card. Installed Server 10.04.3.  It brought up a dialog asking if the Broadcom NetXtreme or the Intel was the primary... I selected the Intel and it suddenly continued without any problems... After that I installed linux-firmware-nonfree... And you know, even though that is the package that the broadcom NIC should be using and should have been installed to use it- it had not been installed.

I have servers with 5 popular servers boards. This has been the only one that has comeuo with an install problem.  (Enough that I was going the reinstall MS Server 2008 back on it!)

Solved or at least found a workaround, but-- You would figure that a somewhat common and popular server board would be supported by Ubuntu Server, right? You "would" think...

Running for now, but turning in a bug report on Server Edition 10.04 through 12.04 for this...

---

