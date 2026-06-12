---
title: "Eliminate Grub Gracefully?"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by holadebob on 2009-12-08
I have my XP on Drive C and Jaunty on Drive D, separate physical HD's.
I want to eliminate Grub, and boot Jaunty manually from Drive D.
 
Since Jaunty gives me everything I need, I will be eliminating XP soon and thought that would be a smooth way of starting the change.

Then after XP is gone, and I change my slave D to Master C, How do I then make a graceful startup for Jaunty on bootup after. Do I need to reinstall Jaunty, I hope not?

Thanks,
I'm able to get things done with Jaunty, but I'm not a pro, so go easy on me please. :)

---

### Post by darkod on 2009-12-08
> **holadebob said:**
> I have my XP on Drive C and Jaunty on Drive D, separate physical HD's.
I want to eliminate Grub, and boot Jaunty manually from Drive D.
 
Since Jaunty gives me everything I need, I will be eliminating XP soon and thought that would be a smooth way of starting the change.

Then after XP is gone, and I change my slave D to Master C, How do I then make a graceful startup for Jaunty on bootup after. Do I need to reinstall Jaunty, I hope not?

Thanks,
I'm able to get things done with Jaunty, but I'm not a pro, so go easy on me please. :)

First, C; and D: are not always different physical drives but you seem sure they are. I assume you're right.
Second, if Jaunty is proper linux install windows would not see that drive at all, hence it wouldn't call it D:. Did you install Jaunty as wubi? That is not separate install, it works inside windows and you can't just simply separate them.
After you clarify what you actually have, we can talk options.

---

### Post by holadebob on 2009-12-08
thanks, yep they are separate, I installed them.
No, that's true, Windows doesn't see the drive that Jaunty is on, but I called it D out of habit. Wubi wasn't installed, Either during or right after bios, Grub runs and defaults to Jaunty and gives me the option of selecting XP after 10 seconds.

---

### Post by darkod on 2009-12-08
Ok, great. The only question now is whether grub is on the windows disk or ubuntu disk. :)
There is a script to run but it might be much easier just to disconnect the windows disk and see whether anything (Jaunty) will boot from the ubuntu disk. If there is a message like No OS or similar, that means grub is on the windows disk.

PS. Or in fact, if it's easier to you, download the script in my signature in Jaunty, put it on desktop for example, and run it with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file and right at the top it will show which bootloader is installed to which disk. Give us that info. No need to copy the whole results right now.

---

### Post by holadebob on 2009-12-08
=> Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

Hey, this is cool, I feel like a programmer!

---

### Post by holadebob on 2009-12-08
=> Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

I also disconnected the drive with bios and it booted saying "disk boot failure" No OS.

---

### Post by holadebob on 2009-12-08
sorry about the repeat, the page told me to wait for 20 seconds and try again, which I did. :)

---

### Post by darkod on 2009-12-08
OK, now in terminal run:
sudo fdisk -l

That will show all partitions. Post it here.

---

### Post by holadebob on 2009-12-08
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41774177

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    c  W95 FAT32 (LBA)

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x71be71be

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            9829       19456    77336910    5  Extended
/dev/sdb2               1        9828    78943378+  83  Linux
/dev/sdb5           10200       19456    74356821    7  HPFS/NTFS
/dev/sdb6            9829       10199     2979994+  82  Linux swap / Solaris

---

### Post by darkod on 2009-12-08
OK, now in terminal execute:
sudo grub
find /boot/grub/stage1

That will return some result like (hd0,1). In your case it might be (hd1,1).

Next use the same value to execute, depending what the result of find was:
root (hdX,Y)
setup (hdX)
quit
sudo reboot

Take the cd out, put the 160GB drive as first boot option in BIOS and see whether it's working. Hopefully it will.

---

### Post by darkod on 2009-12-08
Sorry, I got mixed up for a moment. I changed the above post, check it now. Sorry.

---

### Post by holadebob on 2009-12-08
Darko,
Which CD should have been in the drive?
Thank you very very much for your help. I am going to wait to do this until thursday, have family coming and don't have the time right now to finish this off, but I will get back to you when I do.
Thanks again,
Bob

---

### Post by darkod on 2009-12-08
Since you are installing grub1 for Jaunty, it has to be the 9.04 cd.
From what I can see, the find command should return (hd1,1) result and from there on the commands should be:
root (hd1,1)
setup (hd1)
quit
sudo reboot

---

