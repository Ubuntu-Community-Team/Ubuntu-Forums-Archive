---
title: "kernel panic with 2.6.32.-26"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by j33pn on 2010-12-01
I guess I had a background update from  Linux 2.6.32-25 to Linux 2.6.32.26 yesterday.  Now when I boot, GRUB lists three versions of linux (-24, -25, and -26) and vista.  If I choose the new version of linux (2.6.32-26) from yesterday, I get: kernel panic - not syncing - VFS: unable to mount root fs on unknown block (0,0).  Luckily the -25 version still boots without problem.

After a small heart attack and googling, I looked at my grub.cnf file:

> menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set edded2ae-5b29-44a3-8013-e8d9823f97be
    linux    /boot/vmlinuz-2.6.32-26-generic root=/dev/sdb1 ro   quiet splash
}

menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set edded2ae-5b29-44a3-8013-e8d9823f97be
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=edded2ae-5b29-44a3-8013-e8d9823f97be ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}The new kernel calls out the root differently and it doesn't have the initrd line, as the other two versions of linux do.  I changed the -26 line to match the -25 line:

> menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set edded2ae-5b29-44a3-8013-e8d9823f97be
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=edded2ae-5b29-44a3-8013-e8d9823f97be ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}BUT, I still get the kernel panic error.

Any suggestions as how to upgrade to the -26 version?

FYI: HP DV9500 laptop with 10.04 AMD64

---

### Post by j33pn on 2010-12-02
Wrong forum?
Wrong question?
Non-problem?
There is no answer?

---

### Post by Cavsfan on 2010-12-02
Remove it with this:
```
sudo apt-get purge linux-headers-2.6.32-26 linux-headers-2.6.32-26-generic linux-image-2.6.32-26-generic
```Re-install it with this:
```
sudo apt-get install linux-headers-2.6.32-26 linux-headers-2.6.32-26-generic linux-image-2.6.32-26-generic
```And run **sudo update grub** afterwards, if it doesn't already do so automatically.
This might help. I got a beta nVida driver update this morning and could not even boot into any kernel.
Took half a day to fix it. No more nvidia beta ppa in my software sources!

---

### Post by ScoobyDog_DE on 2010-12-02
Hello,  I had the same problem, but with adding the UUID an initrd I can boot my Ubuntu 10.04, to see more output at boottime you can replaye "quiet splash" with debug, then you can see more Information.  My Kernel Panic was, the bootfilesystem can not be found.  br Scooby

---

### Post by spiderwort on 2010-12-04
I too got a kernel panic after applying the new updates for kernel 2.6.32-26 this morning. The errors indicated it could not find the root device.

In examining my grub.cfg file, I also saw that my newest menuentry had no initrd and was trying to boot the kernel directly from the file system. I knew that would not work with my SCSI hardware RAID Mylex card ;-)

So I opened a terminal window and typed: sudo update-grub

After that I rebooted into the new kernel, and am now running it with no issues.

For what it's worth, I've applied the same updates to 2 laptops with no issues.

Hope this helps j33pn.

---

