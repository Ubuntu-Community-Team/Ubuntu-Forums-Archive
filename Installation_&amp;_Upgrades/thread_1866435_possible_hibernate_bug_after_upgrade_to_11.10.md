---
title: "possible hibernate bug after upgrade to 11.10"
date: 2011-10-21
forum: Installation &amp; Upgrades
---

### Post by mado89 on 2011-10-21
Hi,
i've recently upgraded to 11.10 (from 11.04).
Now hibernate is not working.
I'm running 64bit version on an Lenovo T420.
When i press the hibernate key its going to suspend (before on 11.04 it went to hibernate)
When i hibernate via the menu, booting fails.
Please help me with collecting data for filing a bug report!
thanks

---

### Post by 2F4U on 2011-10-21
Your first source of information are probably
- dmesg output
- /var/log/pm-powersave.log
- /var/log/pm-suspend.log

---

### Post by JohnDoe365 on 2011-10-22
Had the same problem, solved it for me:

The problem was that the installer wrote a wrong UUID for the swap partition into /etc/fstab.

check if you system has a working swap area using the

free

command line commando. The last line should be the available swap space. If this is 0 chances are good, that the installer wrote a wrong UUID into /etc/fstab.

Start parted to get the UUID of your swap space and correct the entry in /etc/fstab.

BTW: I got hibernate back, but it's comming back with a normal boot all the time.

EDIT: Hibernation now works for me after I corrected the UUID of the swap partition in
/etc/initramfs-tools/conf.d/resume
according to [https://help.ubuntu.com/community/UsingUUID#Grub](https://help.ubuntu.com/community/UsingUUID#Grub)

---

### Post by dneff87 on 2011-10-24
Hi,

For what it's worth I was having a (potentially unique) problem with hibernate after 11.10 upgrade. Basically, when I tried to hibernate it would say something like "PM: not enough memory" and "PM: error -12 creating hibernation image".

Finally got a chance to take a look at things. Turned out the update scripts for whatever reason messed with my partitions and created a new swap space of 3.0GB to use for my hibernation images etc. Well, I have 3GB of ram, and while that is supposed to be the MINIMUM size of your swap space, I'd been using a 6.0GB swap (RECOMMENDED) all along. TL;DR - The update scripts created an extraneous undersized swap space and switched me over to that (while preserving my original swap too), which broke my hibernation.

I am FAR from a linux Jedi, but can usually figure things out with the help of google and our lovely community. Anyway, after reassigning swap to the original 6GB partition, everything is back to normal.

For everyone else with hibernate issues, it might be worth checking if your partitions got messed up in some way too (whether or not it was this specific way, or your symptoms are anything like mine).

Good luck!

---

