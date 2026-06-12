---
title: "Cloned disk won't boot"
date: 2010-09-21
forum: Installation &amp; Upgrades
---

### Post by stevecoh1 on 2010-09-21
My hard drive has been getting flaky.  Things take a long time to load and I believe it is disk related.  Whether I'm right or wrong, I wanted to clone my system to a new hard drive.  Old HD = 320 GB, new one = 500GB.  

I used Clonezilla to clone the old drive to the new one.  It very smartly did all the copying, reporting no errors.  I turned the system off, disconnected the old drive and tried to boot the new one.

The GRUB menu appeared, just as on the old drive.  But the OS would not load!  It times out about 15 seconds later, nothing happens then loads into an error console, which I haven't a clue what to do with.  The clues it provides are not very helpful.

System is Ubuntu 10.04

I suspect something is wrong with my grub config on the clone but good luck trying to understand that mess.  I love all the GRUB documentation, bless the hearts of the geeks who wrote it, but man, it doesn't tell me what I need to know!  Like the search command.  It "searches for devices", but why, what is it looking for, what does it need to find?  If my configuration is incorrect, what do I change it to?  Not a single example exists in the documentation of the usage of the different options and why I might want to use them.

Why would the clone (which I presume to be identical to the old drive's) not boot?

Can anyone help?

Thanks in advance

---

### Post by stevecoh1 on 2010-09-21
OK, solved it myself.

There were all these suggestions about update-grub, grub-install, etc., booting from live disks, but none of them worked.  Duh, my root partition wasn't fully there.  Somehow Clonezilla didn't get my partitions right - the root partition was never made into a file system.  Reran Clonezilla and turned on manual partition editing, and just reentered everything I'd had before and this time Clonezilla did the complete job and my new drive was bootable.

Possibly a Clonezilla bug as my setup was a bit unusual:
/dev/sda1 - Windows
/dev/sda2 - ext4 /boot
/dev/sda3 - extended
/dev/sda5 - swap within /dev/sda3
/dev/sda6 - ext4 /

But anyway, it's all good now.

---

### Post by drs305 on 2010-09-21
Congrats on solving this issue yourself.

I'll take a look at the "search" references and see if I can shed some more light on that function - there isn't much documentation on it from the developers I'm afraid. 

You can mark this thread SOLVED via the Thread Tools link at the top right of the first post if you don't need any more assistance.

---

