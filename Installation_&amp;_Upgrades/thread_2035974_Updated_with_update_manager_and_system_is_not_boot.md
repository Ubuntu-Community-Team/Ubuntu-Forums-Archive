---
title: "Updated with update manager and system is not booting now"
date: 2012-07-31
forum: Installation &amp; Upgrades
---

### Post by markskayff on 2012-07-31
Ok, my first post in ubuntuforums.

Yesterday I did an update for my Ubuntu 12.04 'Precise Pangolin'. I've noticed also that a new kernel was added to boot. The generic-page-3.something.27.

The issue is that my system is not booting now. It just feezes at the splash screen. The mouse pointer loads, and after a few seconds everything freezes up.

I tried to access the GRUB menu by pressing Shift and could. Then selected and entered to recovery mode. At recovery mode the system loads with no support for the graphical rendering. 

I have deleted the last kernel from the system and now the generic-pae 3.something.25 is the highest version. But still the system is freezing when botting.

Has anyone experienced something like this. Any solution to this issue?

I'd appreciate your responses.

Mark.

---

### Post by jenks on 2012-08-02
I have had a similar but not identical experience. Yesterday I updated an old 12.04 system and a relatively fresh 12.04 system with aptitude upgrade, noting the new .27 version kernel installed in each. By "old" I just mean it started out as 8.04 or something and has been upgraded to 12.04 over the years since, while the other system was installed around May. I rebooted the old system without incident, but this morning when I went to reboot the recent system, I get:

error: Cannot read the linux header.
error: You need to load the kernel first.
Press any key to continue...

and then it returns to the grub menu. Kernel .26 gives the same error, though I normally boot after each kernel upgrade and don't remember a problem booting last time. Kernel .25 is able to boot successfully.

---

### Post by robtygart on 2012-08-02
> **markskayff said:**
> Ok, my first post in ubuntuforums.

The issue is that my system is not booting now. It just feezes at the splash screen. The mouse pointer loads, and after a few seconds everything freezes up.


Mark.

Can you make it to the login screen? If so, try loging in under fail safe mode? 

If it loads, open your terminal and type 

```
sudo apt-get update
```

then
```
sudo apt-get upgrade
```

Questin: Did you download any graphic drivers? If yes and assuming you can log in under fail safe mode type this and paste it back here.

```
-nnk | grep -iA2 vga
```

---

### Post by jenks on 2012-08-02
I tried upgrading to the latest packages again on the recent system, but the six non-kernel packages upgraded had no effect. I also ran:

sudo dpkg-reconfigure grub-pc

keeping the suggested defaults, but still can only boot to the 3.2.0-25 kernel.

Other differences between my working and problematic system are that the former is dual boot while the latter is single boot, and the former is on hardware only a few years old while the latter is a pentium III.

EDIT:

I found a thread of a very similar problem from May:

[http://ubuntuforums.org/showthread.php?t=1767541](http://ubuntuforums.org/showthread.php?t=1767541)

The solution there was to move the /boot directory into its own partition near the beginning of the disk to overcome the limitation of the BIOS in being unable to read past 128 GB on that old system. Since I too am running an old system with a large (300 GB) drive, I will try moving the drive to a more recent system and see if that resolves the booting problem.

---

### Post by markskayff on 2012-08-02
Hi RobtyGart. Thanks for your input.

I´ll be trying that. 

Yes, indeed I entered GRUB by pressing SHIFT and accessed through fail safe mode. Then the system could pass the boot and loaded. I then added "nomodeset" next to "quite splash" at the etc/default/grub file and updated grub and it seems to work again, but with no graphic backup when booting (some odd symbols and a gross display shows).

It looks like´s something with the video system. 

I´m always reluctact to update a system that´s running ok. But the other day the update window appeared for the 20th time and showed some 150MB of updates and I say, well maybe it´s time. And for what? To get a non working system. 

I´ll check what you say here, cause I want the good and smooth black, purple, screen with good graphics when the system is booting.

Otherwise I´ll be doing a clean install with the Kernel 3.something..23 which was the first for 12.04 I´ve seen and working good.

---

### Post by markskayff on 2012-08-02
> Questin: Did you download any graphic drivers? If yes and assuming you can log in under fail safe mode type this and paste it back here.

```
-nnk | grep -iA2 vga
```


In regards this, no I did not download any graphical driver. I´ll connect later with my ubuntu laptop and check the output for the nnk command.

---

### Post by markskayff on 2012-08-02
Hi RobtyGart.

You know, it worked. I did:

sudo apt-get update and then

sudo apt-get upgrade

then removed the nomodoset next to quite splash in the grub file ... rebooted and everything back to normal.

I wonder what was the effect of the apt-get update and next into my system ... but finally worked!

Thanks man for you input. You have one medal from me. :)

---

