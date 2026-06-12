---
title: "formatting vista partition to increase storage"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by Sylver06 on 2009-12-01
Hi, so the way i have my laptop set up is with my vista partition containing 30 gigs or /dev/sda1 ntfs, a 14.65 gig partition or /dev/sda2 extended with a 700mb linux swap for Ubuntu 9.04, and finally a 180 gig partition or /dev/sda3 ntfs for my data storage.

Is it as easy to use G Parted to remove my vista partition (which has now totally crashed, only needed it for comparability) and allocate that to either my home directory or my data partition? And if so, could I also remove it to say temporarily install xp then I would remove that when I'm done? 

This should be basic, but I have nothing to backup anything on and I'm not crazy about reformatting everything then do a fresh install again and only need windows till I'm done school for compatibility with certain programs that don't run well in wine.

---

### Post by phillw on 2009-12-02
> **Sylver06 said:**
> Hi, so the way i have my laptop set up is with my vista partition containing 30 gigs or /dev/sda1 ntfs, a 14.65 gig partition or /dev/sda2 extended with a 700mb linux swap for Ubuntu 9.04, and finally a 180 gig partition or /dev/sda3 ntfs for my data storage.

Is it as easy to use G Parted to remove my vista partition (which has now totally crashed, only needed it for comparability) and allocate that to either my home directory or my data partition? And if so, could I also remove it to say temporarily install xp then I would remove that when I'm done? 

This should be basic, but I have nothing to backup anything on and I'm not crazy about reformatting everything then do a fresh install again and only need windows till I'm done school for compatibility with certain programs that don't run well in wine.


Your sda2 is your ubuntu install ?

If so, get GP to format sda1 to FAT32 ready for XP - Let XP re-set it to NTFS during the installation - Don't forget to get AntiVirus programme onto the new XP area BEFORE you connect to the internet !!!  AVG8 has been reported as having 'an issue' with XP, so go for something like Avast (Free for home user - they email you the pass-code) etc.

Then, put XP onto sda1 - it will almost certainly over-write your Grub. Heading over to [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  covers getting grub 'back in charge' for you. - It might be a good idea to print that page off. 

A more "hold your hand" of installing XP AFTER Ubuntu can be found here -->  [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

As you're using 9.04, you are still on Grub legacy - so the instructions for rebuilding Grub from that site should work - but the thread I posted DOES  work !!

Regards,

Phill.

---

### Post by Sylver06 on 2009-12-02
Alright, now when i format sda1 to FAT32, how to I setup XP to install on that partition?

---

### Post by darkod on 2009-12-02
When you boot up with XP installation disc it will ask you where to install. That partition is already NTFS so it will be able to see it. Just instruct XP to use that partition and to format it as NTFS (quick format) and that's it. You don't even have to do anything with Gparted in advance because the XP will see your NTFS sda1.

---

### Post by phillw on 2009-12-02
> **darkod said:**
> When you boot up with XP installation disc it will ask you where to install. That partition is already NTFS so it will be able to see it. Just instruct XP to use that partition and to format it as NTFS (quick format) and that's it. You don't even have to do anything with Gparted in advance because the XP will see your NTFS sda1.


Unless, of course, there is a vestige of Vista left on it - in which case XP will squeal like a pig & refuse to instal - hence me saying to knoc it back to Fat32

Regards,

Phill.

---

### Post by darkod on 2009-12-02
I have never tried to put XP over Vista (I usually replace older win with newer) but I thought if you tell it to format it won't complain. There will probably be a warning that there is an OS on the partition that you will wipe out, but other than that it shouldn't complain. :) The key word is shouldn't. :)

---

### Post by phillw on 2009-12-02
> **darkod said:**
> I have never tried to put XP over Vista (I usually replace older win with newer) but I thought if you tell it to format it won't complain. There will probably be a warning that there is an OS on the partition that you will wipe out, but other than that it shouldn't complain. :) The key word is shouldn't. :)


lol - I've had problems trying to go 'backwards' with win installs - it says there is a newer OS installed and sulks, then you have the choice of 'exit' ... or ... 'exit' .... ;-)

That's why I reformat - only takes a couple of moments :-)

Phill.

---

### Post by Sylver06 on 2009-12-02
Alright, so if newer to older could cause problems, then should i go with windows 7 instead? I can get a student copy for very little

---

