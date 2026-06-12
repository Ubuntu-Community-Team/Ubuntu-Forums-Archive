---
title: "Hardware Driver Activate Fails with permission error"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by jhbmac on 2010-01-26
Using 9.10 64bit
Select System->Administration->Hardware Drivers
Receive list box of available drivers
Select desired driver from list
Press Activate button
Receive error popup containing the following text:

You are not authorized to perform this action.

I am not prompted for a password as I expected.
The userid logged in is the first/only userid created during installation
According to /etc/group the logged in user id is a member of adm and admin
According to /etc/sudoers %admin ALL=(ALL) ALL

I figure I am doing something wrong, but since I am not getting prompted for a password maybe the command is not correctly being executed under sudo.

Anybody got any ideas?

---

### Post by audiomick on 2010-01-26
Hi.
I haven't installed harware drivers for a while, but from memory, I think it should ask for a password. Your description of your actions sounds right; I don't think you are doing anything wrong.

---

### Post by DizzyCoder on 2010-01-27
I can confirm this behaviour... backtrack for a second here:

I had Desktop 64 distro installed just fine, added the driver, been using it okey-dokey.

Today I installed x86 Alternate Installer (for encrypted LVM) and I have the same issue presented above.

Straight-forward install, not much different than any of the other ubuntu installs I've done on this same box -- different HDD though (irrelevant!?)

---

### Post by DizzyCoder on 2010-01-27
Umm, soooo... I reinstalled.  Now it works.  The only difference was that I manually partitioned the drive so I could have an 'unsafe' NTFS partition along side the encrypted LVM  (unreleated!?)

Quirky.  Flukey.  Kooky.

---

### Post by audiomick on 2010-01-27
> **DizzyCoder said:**
> Umm, soooo... I reinstalled.  Now it works.  The only difference was that I manually partitioned the drive so I could have an 'unsafe' NTFS partition along side the encrypted LVM  (unreleated!?)

Quirky.  Flukey.  Kooky.

Dodgy install CD maybe? Didn't quite make it the first time, did the second?

---

