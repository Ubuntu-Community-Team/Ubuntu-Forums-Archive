---
title: "&quot;udev unconfigured&quot; problem causing refusal to boot"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by rikjwells on 2010-09-02
[FONT="Arial"]I have just attempted to apply the updates to my installed packages and add some others including what I hope are unrelated packages such as:[/FONT]

[FONT="Courier New"][B]tidy
python-webkit-dev[/B][/FONT]

[FONT="Arial"]A reboot was required after which I get the following message:[/FONT]

[FONT="Courier New"]**udevadm trigger is not permitted while udev is unconfigured.**[/FONT]

[FONT="Arial"]Subsequently, after waiting, the root device is not resolved and I get "dropped" to BusyBox.  I can successfully mount the 4 existing partitions from here, but BusyBox doesn't really offer the tools to do much, I believe, so I reboot with the USB pendrive live installation of Xubuntu and mount the partitions and attempt to recover the installation something like this in a terminal:[/FONT]

[FONT="Courier New"][B]sudo bash
mkdir -p /mnt/host
mount /dev/sda5 /mnt/host
mount /dev/sda1 /mnt/host/boot
mount /dev/sdb1 /mnt/host/home
mount /dev/sdb2 /mnt/host/usr
chroot /dev/host
dpkg --configure -a
update-initramfs -u[/B][/FONT]

[FONT="Arial"]I have also hacked the host's[/FONT] /etc/fstab [FONT="Arial"]so it uses[/FONT] [FONT="Courier New"]**/dev/sd*[B]xn***[/B][/FONT] [FONT="Arial"]instead of the UUIDs.  All of the partitions function correctly as far as I can tell.  None are full and all are writable.

I haven't yet managed to successfully enable GRUB which doesn't offer alternative kernels from which to boot.  I am at a loss how to proceed: I just can't figure out how to "configure"[/FONT] [FONT="Courier New"]**udev**[/FONT] [FONT="Arial"]or at least convince it to mount the partitions.  The UUID seems to be being used for that (failed) purpose, judging by the message shown after the mount timeout at boot time.

**Help!!**[/FONT]

---

### Post by Hauke on 2010-09-02
I had the same problem and solved it.

Try to boot an other kernel, that should still work.
run ```
sudo update-initramfs -u -k 2.6.32-24-generic
```

After a reboot the kernel should find the disks again.

---

### Post by rikjwells on 2010-09-02
Phew!  I was concerned regarding the kernel version being the same as my most recent one (I ***really*** have to get to understand the workings of this area better) and that I got 3 grep errors when running the command, but thankfully I'm now back up and running!  :-D

Thank you so much!  I hoped there would be a simple solution.  :-)


Cheers for now,
    Rik

---

