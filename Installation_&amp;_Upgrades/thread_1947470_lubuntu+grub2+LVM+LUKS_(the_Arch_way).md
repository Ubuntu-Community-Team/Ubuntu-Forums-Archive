---
title: "lubuntu+grub2+LVM+LUKS (the Arch way)"
date: 2012-03-26
forum: Installation &amp; Upgrades
---

### Post by manutenfruits on 2012-03-26
Hi!

I am trying to install lubuntu 12.04 beta on my computer together with Windows 7 (unrelated) and an existing encrypted Arch installation.

I want to be able to install and boot lubuntu the same way Arch does: there's an unencrypted logical volume for boot (only GRUB2 can boot from lvm AFAIK), asks me for a key to decrypt the arch volume (encryption is done per LV, not PV), and I don't need anything else at all (there's a separated /home that is mounted using crypttab, but that shouldn't matter).

Now the problem is that I see a lot of tutorials on how to do this, but none seem to work for me. Some of them use a small root or home partition that is later changed by the actual encrypted one (why would I need this?). The ubuntu documentation redirects me to the Arch wiki, but there is also some problems, because in arch in order to decrypt I need an argument on the kernel line of grub2, while I don't for lubuntu. 

I managed to install it using the alternate CD and following the installer GUI, but now it won't boot. I am sharing the /boot with arch and is running off of arch's grub2, I edited the arguments and I get to the password screen, but then I have a kernel panic because it can't find /root/dev/console. Then I get lost. I mounted the volume under arch and I have discovered that all the directories are under /@/ instead of /. I know it has something to do with symlinks, which I don't totally understand. Anyway, /dev is not under /root, so I don't get that either.

Sorry for the long post!
Thanks!

---

