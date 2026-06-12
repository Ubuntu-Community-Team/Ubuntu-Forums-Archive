---
title: "[SOLVED] Clean install won't boot with raid0 -&amp;gt; luks -&amp;gt; lvm (7.10)"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by ssj3strife on 2008-03-06
Hi all,

I just did a clean install of 7.10 using the alternate iso. Here's the setup:

/boot is on /dev/sda2
/dev/md0 using /dev/sdb1 and /dev/sdc1
md0_crypt using /dev/md0
and then finally swap and / with LVM on md0_crypt

The installer goes just fine all the way until I reboot the machine, but instead of booting into the newly installed system, the system pauses for about a minute after activating md0 and then drops me to a busybox shell. 

Once in the shell, I type the following:

```
cryptsetup luksOpen /dev/md0 md0_crypt
[enter passphrase]
return
```

So what's happening is when I'm dropped to the shell, /dev/md0 is already built. I then have to manually open the encrypted partition, and then when that's unlocked it automatically detects the LVM. Afterwards, the system boots.

What can I do to avoid being dropped to the shell in the first place? I'm thinking modifying a file in /usr/share/initramfs-tools/scripts is probably the best answer, and then rebuilding the initrd image?

---

### Post by ssj3strife on 2008-03-08
Alright, I got it. What wound up happening was that I was being affected by this bug:

[http://wiki.debian.org/DebianInstaller/RAIDvsCrypto](http://wiki.debian.org/DebianInstaller/RAIDvsCrypto)

Also, I had to disable the splash screen. For some reason, even when I entered the right passphrase at the prompt, it would fail to unlock the device if it was showing the splash.

---

