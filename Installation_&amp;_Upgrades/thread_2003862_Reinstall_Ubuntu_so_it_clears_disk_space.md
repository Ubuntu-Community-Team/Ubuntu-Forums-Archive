---
title: "Reinstall Ubuntu so it clears disk space?"
date: 2012-06-14
forum: Installation &amp; Upgrades
---

### Post by lpbryan on 2012-06-14
Note: I wasn't sure if I should post this here or in Absolute Beginner talk, because beginner I am... please keep that in mind! :)

I have a little Acer AspireOne netbook that has a hard drive of a mere 8GB. A year and a half ago I wiped out Windows and installed Ubuntu, and it was fine - there was still plenty of space. 
The other day I went to upgrade, and it told me I had enough free space to do so, but then about 3/4 through the process it told me it couldn't finish because there was not enough space.

Disk usage analysis tells me 6GB are used up and only 2GB free. I can't figure out why this is, because I've already deleted all the files I ever saved to the thing (not many, since I rely on an external), I've removed lots of applications, cleared the cache from Firefox, and used Computer Janitor to deal with the files I know nothing about. All this and still only 2GB! I can't imagine Ubuntu itself takes up 6GB... does it?

When I wanted to upgrade to Ubuntu 11 I created a USB boot disk and reinstalled the whole system, thinking it would delete whatever was there and free up space... but it didn't.

SO... can someone tell me how I can install Ubuntu 12.04 so it clears up more space? I have no other OS installed on the machine, only Ubuntu.

THANK YOU!!

---

### Post by critin on 2012-06-15
Upgrading adds packages, takes away some and adds others.  If you have backed-up everything you want and don't mind adding things you have installed, I would advise installing fresh.  Install it right over the current version,  (which works fine for me) or formatting the disk which takes everything off and installing.
 I don't upgrade because the disk can collect a lot a stuff over time--I install fresh every time.

With 8 GB there's not much room for extras, and the system needs extra room to run its programs.

---

### Post by darkod on 2012-06-15
> **lpbryan said:**
> 
When I wanted to upgrade to Ubuntu 11 I created a USB boot disk and reinstalled the whole system, thinking it would delete whatever was there and free up space... but it didn't.
  

This was your wrong assumption. You can't expect it to delete your existing installation because you might lose your data if that's not what you want.

That's why it always installs a new installation keeping the old one too, thus taking more space on the hdd. If you want it to overwrite the existing installation, you will have to use the manual method and tell it which partition(s) to install onto.

Having said that, the latest 12.04 LTS has an option to install over an existing installation I believe. But since right now you seem to have two installations, you better delete all of them and install again.

If you don't have any data you would want to keep, you can boot with the 12.04 usb in live mode, open Gparted and delete all partitions that you don't need. If you are not sure what to delete, post a screenshot of Gparted and we can have a look.

Note that in live mode usually the swap partition will be used so it will have a key symbol next to it (locked), so you can't delete it. You need to do right-click on it, and select Swapoff. That will remove the key symbol and you can manipulate the partition.

Once you have all partitions deleted that you want to delete, you can make a new clean install of 12.04 LTS either with one of the auto methods, or manually.

---

