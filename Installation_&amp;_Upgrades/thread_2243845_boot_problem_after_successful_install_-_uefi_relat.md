---
title: "boot problem after successful install - uefi related?"
date: 2014-09-11
forum: Installation &amp; Upgrades
---

### Post by jameswdunham on 2014-09-11
I did a clean install of Trusty a few days ago and wasn't having any problems. Now I'm booting to a blank screen, and I haven't been able to solve it using suggestions from other threads.

Here's what I've figured out: Choosing Options in GRUB and going to the 2nd row "Ubuntu, with Linux 3.13.0-35-generic (recovery mode)" I get this error: "Gave up waiting for root device ... ALERT! /dev/disk/by-uuid [etc] does not exist" ... But this isn't actually true (see below).

If instead I choose the 3rd row, "Ubuntu, with Linux 3.13.0-24-generic," I boot into Ubuntu successfully. What's odd is that hitting "e" and examining the boot options for each row (kernel version ?), the UUIDs are the same, and the only difference (other than the -24 vs. -35 kernel numbers) is that in the version that boots to a blank screen, there's an extra ".efi.signed" in this line like "linux  /voot/vmlinuz-3.13.0-35-generic-efi.signed root= [...]" Running sudo blkid after booting with the older kernel confirms that the UUID is correct. I do have an UEFI board, and the selected boot device is just called "ubuntu".

How can I repair this? Removing the "-efi.signed" part of the line doesn't work. I've also tried the boot-repair tool with the default options with no success. 

Thanks for any help!

---

### Post by oldfred on 2014-09-11
Please install Boot-Repair and just run the Bootinfo report. Post link to report so we can see all the details of configuration.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

The .signed kernel versions are for UEFI secure boot. I thought they worked with or without secure boot.
Do you have secure boot off or did you have it on when you did updates? Or why is older kernel not secure boot and new is? Or did update just give you incorrect kernels, or ones that did not correctly install. 

Error may be from missing initramfs? I have this in my notes:


  SOLUTION: ! /dev/disk/by-uuid/ ...<your UUID>.... does not exist 
[http://ubuntuforums.org/showthread.php?t=1127779](http://ubuntuforums.org/showthread.php?t=1127779)
[http://ubuntuforums.org/showthread.php?t=1565714](http://ubuntuforums.org/showthread.php?t=1565714)
"If the &#8220;apt-get upgrade&#8221; does not successfully complete then a flag is set and update-initramfs does not get to run, hence grub gets all messed up. You should be able to boot using the old kernel and then run the sudo update-initramfs &#8211;u -k command. Then run sudo dpkg &#8211;reconfigure. That should clear the upgrade flags and fix any broken packages."

---

### Post by jameswdunham on 2014-09-11
Thanks for your help. I tried a number of things from these links, and I think the solution was in post #26 of [this thread]("http://ubuntuforums.org/showthread.php?t=1127779&page=3"):

```
sudo dpkg-reconfigure udev
```

---

