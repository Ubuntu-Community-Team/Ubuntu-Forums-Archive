---
title: "fakeraid manual install, fails at update-grub"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by bertram_wooster on 2007-04-23
Ok, I found this help page on how to install onto my fakeraid.

[https://wiki.ubuntu.com/FakeRaidEdgy](https://wiki.ubuntu.com/FakeRaidEdgy)

which has taken me through the process of getting the install to recognise my raid array - and I would recommend it to anyone wishing to install ubuntu onto the same raid array as another os.

Everything ran smoothly until:

**3. Configuring the Bootloader's menu.lst**

Whereupon I ran the command:

# update-grub

Which failed with the following message:

[: 25: ==: unexpected operator
exec: 25: -a: not found

###############################

**I don't know if this bit is important but**:

Doing a quick google I found that 25 is the error for

So using a bit of creative interpretation, I tried running the command:

# grub-install --recheck /dev/mapper/isw_ccddgdghai

but got the following response:

Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature 
/dev/mapper/isw_ccddgdghai does not have any corresponding BIOS drive.

################################

Can anyone give me some advice, as to how to get update-grub to run or how I could bypass this and set up the menu.lst file manually.

Cheers,
Bertie

---

### Post by jewishj on 2007-05-18
> **bertram_wooster said:**
> Ok, I found this help page on how to install onto my fakeraid.

[https://wiki.ubuntu.com/FakeRaidEdgy](https://wiki.ubuntu.com/FakeRaidEdgy)

which has taken me through the process of getting the install to recognise my raid array - and I would recommend it to anyone wishing to install ubuntu onto the same raid array as another os.

Everything ran smoothly until:

**3. Configuring the Bootloader's menu.lst**

Whereupon I ran the command:

# update-grub

Which failed with the following message:

[: 25: ==: unexpected operator
exec: 25: -a: not found

###############################

**I don't know if this bit is important but**:

Doing a quick google I found that 25 is the error for

So using a bit of creative interpretation, I tried running the command:

# grub-install --recheck /dev/mapper/isw_ccddgdghai

but got the following response:

Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature 
/dev/mapper/isw_ccddgdghai does not have any corresponding BIOS drive.

################################

Can anyone give me some advice, as to how to get update-grub to run or how I could bypass this and set up the menu.lst file manually.

Cheers,
Bertie

I had the same problem (among others) getting my nvraid working.  I ended up having to use that wiki along with another to get it working - I posted on another thread the exact step-by-step I did.  That thread is here: [http://ubuntuforums.org/showthread.php?t=421405](http://ubuntuforums.org/showthread.php?t=421405)

Hope that helps

---

