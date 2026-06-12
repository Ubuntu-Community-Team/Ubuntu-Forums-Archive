---
title: "Installing 8.10 on Existing RAID 0 Setup (Not Fake RAID)"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by FliGi7 on 2008-11-10
I'm currently trying to figure out how to install Intrepid on my RAID 0 setup of two drives. When I go through the install, it detects my storage drive (unrelated to the RAID) and two separate drives (RAID drives). How do I get it to figure out the RAID setup for this so I can install Ubuntu AND the bootloader onto the RAID drives? I'm at a loss.

---

### Post by FliGi7 on 2008-11-11
Nobody?

---

### Post by psusi on 2008-11-12
You can not boot from a software raid other than raid1, since the BIOS doesn't understand raid.

---

### Post by FliGi7 on 2008-11-12
So how does the BIOS know to boot from my XP RAID partition then if it doesn't understand RAID?

---

### Post by psusi on 2008-11-12
> **FliGi7 said:**
> So how does the BIOS know to boot from my XP RAID partition then if it doesn't understand RAID?

It doesn't if it isn't a raid1.  If it is a mirror then the bios just sees one half of the mirror, which is enough.

---

### Post by FliGi7 on 2008-11-13
The BIOS has no idea of my RAID 0 array, but it is available as an option to boot from in the list of hard drives(of which I do). I don't quite get how that makes sense. 

The BIOS knows I have RAID 0. I can select to boot from it and I do. So, why doesn't Ubuntu realize this?

---

### Post by psusi on 2008-11-13
> **FliGi7 said:**
> The BIOS has no idea of my RAID 0 array, but it is available as an option to boot from in the list of hard drives(of which I do). I don't quite get how that makes sense. 

The BIOS knows I have RAID 0. I can select to boot from it and I do. So, why doesn't Ubuntu realize this?

Because contrary to what you wrote in the subject, you DO have a fakeraid.  The alternate Intrepid install cd supposedly will install just fine.  I used the desktop cd, which crashed at the end trying to install grub, which I had to manually futz with to get working.

---

### Post by FliGi7 on 2008-11-13
Ah, so what is considered non-fake? An add-on RAID controller card or something?

Why did it end up crashing? I've heard reports that grub won't install/run correctly from a RAID array.

---

### Post by psusi on 2008-11-13
> **FliGi7 said:**
> Ah, so what is considered non-fake? An add-on RAID controller card or something?

Why did it end up crashing? I've heard reports that grub won't install/run correctly from a RAID array.

You might want to take a look at [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto).  The howto part doesn't apply to Intrepid, but the introduction should give you some background.

The short answer is a fake raid is just a regular non raid ide or sata controller that has advanced bios that handles the software raid, and a windows driver to do the same.  Real hardware raid controllers handle all the raid functions in hardware and the OS has no idea there are actually multiple disks.

Grub gets a bit confused with fakeraids because it needs to know the kernel device name of the disk so it can open it and install itself, and it needs to know what the bios identifies the disk as, so that it can configure it's installed parts to know where to load the rest of the system from, using the bios at boot time.  Normally grub assumes that the boot disk, which it calls (hd0), is /dev/sda, but if you have a fakeraid, that's just one of the disks in the raid and you don't want to directly access it.  Instead you use a device in /dev/mapper that represents the raid array as a whole as the boot disk.

---

### Post by FliGi7 on 2008-11-13
Geez. Why do they have to  make it so hard to install the thing on a friggin RAID 0. It really should not be this complicated. Wow. 

I guess I'll just either do a separate drive or use the Wubi installer. Thanks for the heads up and all the help.

---

### Post by psusi on 2008-11-13
> **FliGi7 said:**
> Geez. Why do they have to  make it so hard to install the thing on a friggin RAID 0. It really should not be this complicated. Wow. 

I guess I'll just either do a separate drive or use the Wubi installer. Thanks for the heads up and all the help.

Like I said, it's straightforward in Intrepid with the alternate install cd.  Don't even try Wubi, I would bet it wont work at best, and is likely to go horribly wrong.

---

### Post by FliGi7 on 2008-11-14
I thought your post said Grub would still have trouble loading onto my RAID array. Thus, it's pointless to do the whole install onto my RAID partition if it's going to be a PITA to get grub to work properly.

---

### Post by Liviu-Theodor on 2008-11-14
I don't know if still works in 8.10, but I found some instructions for 7.10.
Try here: [http://wiki.auzigog.com/My_Ubuntu_(7.10)_Installation#Installation_on_RAID_0]("http://wiki.auzigog.com/My_Ubuntu_(7.10)_Installation#Installation_on_RAID_0").

---

### Post by psusi on 2008-11-14
I said if you use the livecd to install grub will need some fiddling to get going.  Normal out of the box install works fine with the alternate cd.

---

### Post by FliGi7 on 2008-11-14
Oh ok. I really appreciate all the help. I will get going on this soon. Thanks!

---

