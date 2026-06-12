---
title: "Upgrade 9.10 to 10.04 LTS and getting not further than bootscreen"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by pluim003 on 2010-04-30
Hi, I did a nightly upgrade on an old laptop. Everything went well up till the reboot-part. I rebooted. Get a flashing cursor for a few seconds and then the bootscreen with 5 dots who go on and off. And that's it.
It's on a Qnote-laptop with only Ubuntu installed.
Thought that an upgrade would be convenient but I'm afraid that I have to burn a CD and do a complete fresh installation.
Or has anyone other suggestions?

---

### Post by kansasnoob on 2010-04-30
I'd try booting into recovery mode. Since Ubuntu is the only OS you won't see a boot menu by default. In order to see the boot menu you must press and hold the Shift key right after the System/BIOS screen passes.

Running recovery mode may produce some error messages that can be helpful. After recovery mode runs you'll see a list of options:

Resume
Clean
Dpkg
FailsafeX
Grub
netroot
root

Without seeing the results of the recovery mode text my best guess would be to try "dpkg" first and see if that provides any clues.

If it seems to be a problem with X you could try failsafeX. It's all a bit of a guessing game :(

---

### Post by pluim003 on 2010-04-30
Thanx, that gave a bit of a clue.
fsck is asking for a password for /dev/sda1. Will dig into this further as it's not getting anywhere now.

---

### Post by kansasnoob on 2010-04-30
> **pluim003 said:**
> Thanx, that gave a bit of a clue.
fsck is asking for a password for /dev/sda1. Will dig into this further as it's not getting anywhere now.

That's one I've not seen before :confused:

---

### Post by pluim003 on 2010-04-30
I chose the previous version and got the same

fsck from util-linux-ng 2.17.2
/dev/sda1: clean xxxx/xxxx files, yyyy/zzzz blocks
Password: Password: Password:

And completely stuck. There is not much valuable stuff on the laptop so I could do a clean install from CD, or put the installation besides the previous one. Only valuable stuff is the squid-configuration. ;-)

---

### Post by pluim003 on 2010-04-30
Well, after a few hours there were new messages: unable to start queue, no space left on device. Did a complete fresh install, which took only approx. 20 minutes and now everything is running fine again. Only missing some games, and I have to (re)configure Squid for internetaccess of our kids, who mainly use this laptop.

---

