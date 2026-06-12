---
title: "Failed Upgrade to 10.04"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by Kevpilot on 2010-06-03
Greetings all-

My neighbor suffered a failed upgrade going from 9.10 to 10.04 on his HP laptop.  I can't get a clear story but it sounds like everything downloaded properly but the failure occurred during installation.  It got to about 95% completion and it stopped.  He rebooted and now the laptop fails (command line) with a GRUB error.

Is there any way to re-start the installation of the OS from the bootable 10.04 disk I made?  He wants to preserve the apps and especially the data on his drive.  I was able to boot up from the Lucid CD and even find a file by name he had created on the hard drive.  (That fact kind of worried me, but that's another issue.)

Many thanks

Kev

---

### Post by dino99 on 2010-06-03
follow this example

[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

---

### Post by Kevpilot on 2010-06-03
Many thanks for your super fast reply!  I, too, am new to Linux though I am an old DOS hand.  

Just to verify that I have, in fact, asked the right question: How do I restart a failed upgrade from 9.10 => 10.04 using the LiveCD disk for 10.04?

Here's the sequence of events:

[LIST=1]
[*]My neighbor (John)'s laptop crashed while running the upgrade from 9.10 to 10.04.
[*]The upgrade appears to have downloaded properly
[*]The installation failed at about 95% (so says John, I was not there as he executed.)
[*]When the installation failed, he rebooted the laptop.
[*]Now, it POSTs fine and begins the OS load.
[*]The error message is: 0.693343 Kernel Panic - Not Syncing: VFS: Unable to mount root FS on unknown (block 0,0)
[*]Rebooting to generic mode-
[*]Ubuntu presents a table with many Linux choices both with and without (Recovery)
[*]None of those choices work with the failure AppArmor failed to load.
[*]Then it gets to recovery menu.
[*]No joy.
[*]Error message: Cannot open file / boot / grub / grubenv  (return)
[*]Next Message: Clock Source TSC unstable (Delta=-68758257NS)
[/LIST]
I found this very frustrating.  Next up.

[LIST=1]
[*]I made an 10.04 ISO disk with the bootable LiveCD.
[*]When we boot up in LiveCD mode, I can even get to the hard drive's file system
[*]Using the search tool, I was able to find at least one data file by name.
[*]So the data still exists.
[/LIST]
My big question: Can I preserve the data and apps already installed AND restart the update process from my 10.04 CD?

So MANY MANY thanks!

Kev

---

