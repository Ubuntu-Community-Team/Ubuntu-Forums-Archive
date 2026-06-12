---
title: "lubuntu installs, but mouse does not work"
date: 2012-08-25
forum: Installation &amp; Upgrades
---

### Post by silverrope on 2012-08-25
I have a rather old IBM S50 ThinkCentre desktop. Initially I installed Ubuntu 12.04, but I found the performance to be rather poor. Having tried Lubuntu 12.04 on a separate old laptop and finding it quite good in performance, I decided to try it out on the desktop. I installed Lubuntu using the alternate installation CD. Everything went fine just like in the laptop installation, except after booting, the PS2 mouse did not work. I reinstalled it again using an IBM USB mouse. Still doesn't work. By the way the PS2 mouse works fine with Ubuntu 12.04.

Does anyone know what I can do to debug this? I can logon, but without a mouse I'm not sure how I can get around the LXDE desktop.

---

### Post by silverrope on 2012-08-30
Ah well, no help from the community again. So I had to find my own solution. I went back to Ubuntu 12.04 in which the PS/2 mouse worked. Then I installed lubuntu-desktop and removed everything that was not in pure lubuntu (via psychocats documentation). So this is a workaround.

I think lubuntu is great for these old machines. But having a non-working ISO disk installation doesn't really promote the OS. As usual Linux ain't ready for prime time...

---

### Post by MG&amp;TL on 2012-08-30
> **silverrope said:**
> Ah well, no help from the community again. So I had to find my own solution. I went back to Ubuntu 12.04 in which the PS/2 mouse worked. Then I installed lubuntu-desktop and removed everything that was not in pure lubuntu (via psychocats documentation). So this is a workaround.

I think lubuntu is great for these old machines. But having a non-working ISO disk installation doesn't really promote the OS. As usual Linux ain't ready for prime time...

Sorry nobody helped in time, you're around these forums enough to know that they're generally very helpful. I have a PS/2 mouse and it works great under Lubuntu. Bearing in mind Lubuntu is a respin of Ubuntu, nothing different under the hood, it might be worth checksumming the ISO.

---

### Post by Githlar on 2012-09-19
It's worth noting that I am having the same problem with a LiveCD version of Lubuntu in Qemu. Granted, this isn't the ISO version, it's kind of a re-hash for my own reason. I started with ubuntu-core chroot environment. However, I installed all packages listed in filesystem.manifest - nothing more, nothing less. The install.manifest (minus the version numbers) md5 from the CD matches that of what I generate out of my chroot environment.

So, it *should* be exactly the same. Perhaps they did something to the squashfs filesystem on the CD that isn't done when I install it my way. I've been looking by comparing hashes from the same files on both installations, but no luck so far. Nothing obvious.

Then again, it could just be Qemu.

---

### Post by Githlar on 2012-09-19
I figured out my problem with the mouse, I was using a single initramfs from the Ubuntu LiveCd to boot all flavors.

My kernel versions for each were as follows (these are from the 12.04 LiveCDs):
Ubuntu: 3.2.0-29-generic-pae
Kubuntu: 3.2.0-29-generic-pae
Xubuntu: 3.2.0-29-generic
Lubuntu: 3.2.0-23-generic

Xubuntu was able to load the PAE modules with no immediate side effects (even though it was not a PAE kernel). But, it's also the same kernel version.

Lubuntu, however is far behind the other kernels from the same release.

When booting Lubuntu with the Ubuntu intiramfs, since the modules in the initramfs were build for 3.2.0-29-generic-pae they were most likely not loading into the kernel.

I remedied my mouse by pulling the initramfs off the Lubuntu LiveCD (which has the correct modules for that version), modifying it to my needs and then booting from it instead.


In your case, however, yours is an installed system. I'm sure by now you've given up on it, but if you have the problem with an installed system in the future, try this:
```
sudo update-initramfs -u
```

---

