---
title: "Ubuntu won't boot without install USB stick!"
date: 2012-09-12
forum: Installation &amp; Upgrades
---

### Post by guybowden on 2012-09-12
Hi - I've just installed Ubuntu 12.04 as a dual boot system with OSX. I thought it was all going well - i could choose either syste from the boot menu and boot into them. Until I removed the install USB stick - when it just says "Loading Operating System..... Read Error"

Reading through the forums, I've tried to ```
sudo grub-install /dev/sda
```

But got this response:

```

/usr/sbin/grub-setup: warn: This GPT partition label has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.

```

So I then installed Boot Repair, but that says

```
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.
```

So I don't know what to do next... creating a BootInfo crashes..

I then tried again, ticking Separate /boot/efi partition, but that just warned me about OSX:

```
MacOS detected. You may want to retry after deactivating the [Separate /boot/efi partition:] option.
Do you want to continue?
```

I didn't press continue as I didn't want to bork my OSX system!

So I created a RESULTS.txt file from using Bootinfoscript to see if anyone could help out at all...



My system:

1x 120gb drive with two partitions, one for OSX, and one for Ubuntu
2x 1TB drive for my data
1x 1GB USB stick I used to install Ubuntu from and now need to keep in there for booting up.

I can provide anything else needed to sort this out! Cheers,

Guy

---

