---
title: "Manually Editing grub.cfg"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by benl11235 on 2009-11-30
I know that grub2 usually does this manually, however that is not an option. It's a long story.
I have to manually configure my grub.cfg file(I know its not recommended)

This is what I have:

```
menuentry "Fedora, linux 2.6.31.5-127.fc12.x86_64" {
	insmod lvm
	set root=(haven-gate)
	linux	/vmlinuz-2.6.31.5-127.fc12.x86_64 root=/dev/mapper/haven-gate ro quiet rhgb 
}
menuentry "Fedora, linux 2.6.31.5-127.fc12.x86_64 (testb)" {
	insmod lvm
	set root=(haven-gate)
	linux	/vmlinuz root=/dev/mapper/haven-gate ro single quiet rhgb
}
```
My /boot is a logical partition (gate) in logical group (haven)
My root is encrypted and is also part of a logical partition(central) in the same group
I have a number of questions

1. The root is encrypted. I believe the cryptoroot function was used in grub, what about grub2? I could really use some help in this regard.

2. The second entry is a test. Is it legal to use /vmlinuz as a shortening for the the vmlinuz. I read somewhere it would automatically boot the latest kernel

Any help with the above two questions would be greatly appreciated. Configuring grub correctly will allow access to Fedora for the firs time. Thank You

---

### Post by lemming465 on 2009-12-01
Manually configuring special grub2 entries is perfectly OK and even supported and encouraged.  Just don't edit grub.cfg by hand; instead put your entries in /etc/grub.d/40_custom, where the rebuild process will reuse them instead of overwriting them.  If you need stuff to show up at the top of the grub.cfg file, copy 40_custom to something with a lower number, such as 09_custom, before editing it.

> Is it legal to use /vmlinuz as a shortening ...
Maybe.  The paths you are specifying to grub are relative to the root filesystem you picked.  If the root has a symbolic or hard link from /vmlinuz to the kernel of your dreams, go ahead.

I'm not sure about the encryption support, sorry.

---

### Post by benl11235 on 2009-12-03
Thanks for that. Can ANYONE with an encrypted root look in to their grub.cfg files, and share what lies within? No one has been able to provide an answer. ANY help would be greatly appreciated.

---

### Post by lemming465 on 2009-12-07
I ran an encrypted Fedora 12 install onto some spare partitions to see what it would do.  Fedora 12 is still using grub1; the boot line looked like:
> kernel /vmlinuz-2.6.31.6-145.fc12.x86_64 ro root=/dev/mapper/luks-17893cb4-828e-45e2-b2d9-4eb80d708971 noiswmd LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
I think you need an Ubuntu grub2 scenario where root specifies the device+partition of the file system containing the Fedora /boot directory, which should be unencrypted, and the linux line specifies the encrypted LUKS file system.  If your fedora /etc/crypttab specifies "haven-gate" as the device mapper name out, it might be OK to use that as the target for root= on the grub2 linux ... line.  The easiest way would be to copy whatever the rest of the *kernel ...* line was out of the Fedora Grub1 menu.lst file.

---

