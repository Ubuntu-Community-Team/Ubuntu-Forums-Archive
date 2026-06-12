---
title: "Stuck after grub"
date: 2020-06-22
forum: Installation &amp; Upgrades
---

### Post by adi90x on 2020-06-22
Hello,

I have a very strange situation, one of my server is now stuck in grub. 
I.e : I can not go after grub.
At the moment, I have try :

- Older kernel / Recovery kernel => Load initial ramdisk message, then nothing happen.
- No splash, quiet option => nothing write down on screen 
- adding loglevel=7 same result : nothing

What is really strange is that I have also the exact same situation using LiveUSB ( I have try several distro and several version)
It get to grub screen and then what ever I select endup on a black screen without any log message on screen... 

Any idea of what I can try now ?

Regards, 
Adrien

---

### Post by TheFu on 2020-06-22
I patched a 20.04 system on Saturday morning. The patch failed to complete.  My logs of the patching end with these 3 lines:
```
Processing triggers for dbus (1.12.16-2ubuntu2.1) ...
Processing triggers for initramfs-tools (0.136ubuntu6.1) ...
update-initramfs: Generating /boot/initrd.img-5.4.0-37-generic
I: The initramfs will attempt to resume from /dev/dm-1
I: (/dev/mapper/vgubuntu--mate-swap_1)
I: Set the RESUME variable to override this.
```

On other non-20.04 systems, the last few lines in the log were:

```
Found initrd image: /boot/initrd.img-4.15.0-65-generic
done
Processing triggers for initramfs-tools (0.122ubuntu8.16) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-106-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.

```

Both of these systems use LVM. One finished fine. The other just stopped. No initrd was created. No kernels were left in /boot/.  Because I patch a number of systems, I didn't notice that one of them failed, but enough needed to be rebooted that I just rebooted them all. All but one of them booted fine.  

The one that failed to boot only showed a grub-rescue screen.  No valid file systems could be found.  I did some troubleshooting and took some corrective measures from a Try Ubuntu flash disk boot, but wasn't able to get either kernels or initrd to be created.  After 30 minutes of screwing around with that (chroot + bind mounts from the Try Ubuntu environment), I just wiped the machine and restored from backups made early in the morning (automatic, daily, versioned, backups are a good thing). Patching again, didn't reproduce the issue.  The /boot/ looks fine again:
```
$ ls -F /boot/
config-5.4.0-33-generic      memtest86+.elf
config-5.4.0-37-generic      memtest86+_multiboot.bin
efi/                         System.map-5.4.0-33-generic
grub/                        System.map-5.4.0-37-generic
initrd.img@                  vmlinuz@
initrd.img-5.4.0-33-generic  vmlinuz-5.4.0-33-generic
initrd.img-5.4.0-37-generic  vmlinuz-5.4.0-37-generic
initrd.img.old@              vmlinuz.old@
memtest86+.bin
```

Another person on the #Ubuntu IRC channel had a similar problem. Nobody had an answer that I saw there. A question for more data was asked, but no response came.  That usually means they are tired or that data request showed the problem.

Does this sound familiar for your situation?  If so, perhaps your logs of the issue can shed light?  If not, then I'll delete this post and get out of the way for others to try and help.

---

