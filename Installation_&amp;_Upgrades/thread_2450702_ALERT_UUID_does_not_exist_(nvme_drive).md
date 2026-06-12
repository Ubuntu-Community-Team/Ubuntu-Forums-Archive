---
title: "ALERT UUID does not exist (nvme drive)"
date: 2020-09-18
forum: Installation &amp; Upgrades
---

### Post by bjlockie on 2020-09-18
After I upgraded packages I couldn't boot.
I fixed the initial problem of not being able to unpack the initramfs (I changed it to gzip).
I documented those problems here:
[https://discourse.lubuntu.me/t/initramfs-unpacking-failed/1569/6](https://discourse.lubuntu.me/t/initramfs-unpacking-failed/1569/6)

Now I have grub running but it says it can't find my nvme boot drive is not found and it goes to an initramfs prompt (busybox shell).
Here is the grub entry:
[ATTACH=CONFIG]286986[/ATTACH]

I suspect the nvme drive is seen but it can't see the GPT? partitions:
[ATTACH=CONFIG]286987[/ATTACH]

---

### Post by oldfred on 2020-09-18
It seems like the updates did not fully complete.
So you need to update initramfs.

Do you have an old working kernel you can boot from grub with?
And update all the kernels from there?
[https://ubuntuforums.org/showthread.php?t=2255888](https://ubuntuforums.org/showthread.php?t=2255888)

Full chroot & update initramfs & grub, but if UEFI install, you also need to mount ESP
[https://askubuntu.com/questions/516217/alert-dev-disk-by-uuid-xxxxxxxxx-does-not-exist-dropping-to-a-shell](https://askubuntu.com/questions/516217/alert-dev-disk-by-uuid-xxxxxxxxx-does-not-exist-dropping-to-a-shell)
 chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
UEFI chroot, must include ESP - efi system partition
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)

---

### Post by bjlockie on 2020-09-20
I was able to boot an old kernel.
Can I copy the working initramfs over the non working one?

---

### Post by oldfred on 2020-09-20
Do the updates & see if the now complete.

sudo update-initramfs -u
sudo update-grub

---

