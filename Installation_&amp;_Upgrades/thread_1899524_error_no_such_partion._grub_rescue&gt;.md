---
title: "error: no such partion. grub rescue&gt;"
date: 2011-12-23
forum: Installation &amp; Upgrades
---

### Post by rave_phantom on 2011-12-23
I get the following error when trying after starting my computer and trying to get to the newly installed Ubuntu 10.10: 
"error: no such partition. 
grub rescue>"

Can anyone help me with this error? FYI, I'm a 100% newbie to Ubuntu. This is my 1st installation.

Yes, I know everyone and there mother has had this problem and it has been on the forums many times but I followed multiple instructions (including [http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html](http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html)) that I found on the forums / online and still got the error when I restart.

According to the attached Terminal log (txt file), you would think that everything would work out right.

FYI, I'm running Ubuntu 10.10 from a 500 GB USB External Hard Drive. I created 3 partitions (1 for PC backup, 1 for swap, 1 for Ubuntu boot). I have the ribbon from my internal hard drive to the motherbord unplugged to prevent any additional problems.

...Happy Holidays.

---

### Post by darkod on 2011-12-23
You don't mount sda6 as /mnt/boot, that is used only if you have separate /boot partition which you don't. sda6 can be either / or /boot, not both. In your case it's /.

Try only this:

```
sudo mount /dev/sda6 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
update-grub
exit
sudo umount /mnt/proc
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt
```

Reboot and see if it helped. If the error is still there write down the UUID number it reports as missing, and also post the result of:
sudo blkid

---

### Post by Bucky Ball on 2011-12-23
Or you could try Boot-Repair. If you boot from the install CD and 'Try Ubuntu', get online and you will find it in Synaptics Package Manager. Install and run it. Reboot.

You can also download the ISO image, burn a CD of Boot-repair and boot from that then run Boot-repair (it will be offered). A handy CD to have about ...

[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html)

---

### Post by rave_phantom on 2011-12-24
Attached is the terminal output for sudo blkid.

Boot Repair didn't work so I emailed the text file from Boot Repair ([http://paste.ubuntu.com/781398/](http://paste.ubuntu.com/781398/)) to [email]boot.repair@gmail.com[/email]. I'm waiting for them to respond.

I thought the boot error was my fault. At the beginning of the installation, I selected the "/dev/sda Seagate FreeAgent GoFlex (500.1 GB)" instead of "/dev/sda6". See the screenshot that I took (from LiveCD after Ubuntu installation).

So I installed Ubuntu this time selecting "/dev/sda6" instead of "/dev/sda6" Seagate FreeAgent GoFlex (500.1 GB)" for "Device for boot loader installation." It didn't work . I still got the grub rescue error.

---

### Post by darkod on 2011-12-25
Selecting /dev/sda for the bootloader destination was not an error, it's correct. The bootloader goes to the MBR of the disk which is /dev/sda. If it has a number like /dev/sda6 it means partition #6.

You posted the output of blkid but didn't post what UUID value is reported in the no such partition message. It usually says the value in the message.

Also, did you try to run the commands I posted in my last post to try and update the grub.cfg?

---

