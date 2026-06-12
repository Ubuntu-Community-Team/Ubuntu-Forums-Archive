---
title: "ubuntu, winXP and win7 triple boot"
date: 2012-07-05
forum: Installation &amp; Upgrades
---

### Post by napsy on 2012-07-05
Hello.

I have three systems installed on my laptop. When I installed Windows7, it detected a previous XP installation and created a choice weather to boot to XP or win7 on startup. Now, I installed Ubuntu and the installer detected only Windows XP.

When booting, I now have two grub choices, Ubuntu or Windows XP. If I select XP, it loads the windows7 boot manager and I have to choose between two systems again.

So, here's my question: Is it possible to configure grub to boot all three systems from there and skipping the Windows boot manager? Both Windows systems are installed on the same disk but on a different partition.

Please help.

---

### Post by dino99 on 2012-07-05
if the system is using a bios:

i suppose you only have ond hdd (sdd) inside. So via synaptic, while running ubuntu, purge grub-pc, then reinstall it on /dev/sda

question: is it with a bios or an uefi ?

in case of uefi:

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by darkod on 2012-07-05
> **dino99 said:**
> if the system is using a bios:

i suppose you only have ond hdd (sdd) inside. So via synaptic, while running ubuntu, purge grub-pc, then reinstall it on /dev/sda

question: is it with a bios or an uefi ?

in case of uefi:

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

Please pay more attention to the question/problem. The OP already has grub2 on the MBR. Doing that procedure can't help him, only make problems if something goes wrong.

To the OP: This doesn't depend on grub2. When you install two versions of windows, it is windows that combined the boot files of both systems onto the same place/partition, and creates a menu with two choices.

Grub2 detects boot files and creates entries in its boot menu. Since it can detect only one, combined set of windows boot files, it makes only one entry in the boot menu. With that entry you call the windows bootloader which has the two choices.

You could possibly solve this, but it depends if you think it's worth it. Basically, you will need to move the boot flag onto the other windows system partition, try the boot repair process which should put a new set of boot files there.

Once you have separate boot files on the two windows partition, you will need to boot your ubuntu and run:
sudo update-grub

to update the boot menu.

---

