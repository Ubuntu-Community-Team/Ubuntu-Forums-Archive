---
title: "Win7 does not boot after 12.10 dual boot installation"
date: 2012-11-20
forum: Installation &amp; Upgrades
---

### Post by stonefuzz on 2012-11-20
Hi all,

I'm new to Ubuntu and I've installed Ubuntu desktop 12.10 in my Satellite L300D, alongside with Win7.
While the Ubuntu installation seems to be just fine, I can't boot Win7.
When I choose the "Windows 7 (loader) (on /dev/sda2)" it changes to a black screen for 1 second and then it returns to GRUB.

I've tried the Boot Repair solution but it didn't work. This is my Boot Info:
[http://paste.ubuntu.com/1371004/](http://paste.ubuntu.com/1371004/)

Can you please help me?
Please tell me if you need further information about my settings.

Thanks and regards!

---

### Post by darkod on 2012-11-20
You have grub2 installed also on the windows partition /dev/sda2. I don't know whether you put it there, or it installed itself, because it shouldn't do that.
In any case, windows can't load with grub2 there.

You can use a testdisk procedure to recover the backup sector of the partition, (like BackupBS). You can use testdisk from your ubuntu or from ubuntu live mode. You only need to download it and run it depending in which folder you extract it.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

That tutorial is also for recovering partitions, which you don't need. Focus only on the instructions to recover the partition boot sector towards the middle-end of the page.

---

### Post by stonefuzz on 2012-11-20
Thanks for your help Darko.

I used the option "Install Ubuntu alongside Windows 7" so I don't how grub2 got installed there.
I'm quite new to Ubuntu so, you're saying that I've two grub2 installed?
I should use TestDisk to repair my /dev/sda2 partition and grub2 will still work after that?

Later today I will try to run the "NTFS Boot sector recovery" tutorial section.

Thanks a lot once again

---

### Post by darkod on 2012-11-20
Correct, you have the main grub2 on the MBR of the disk, which is only /dev/sda and it's where it should be. It will work after the repair.

You also have grub2 on the boot sector of the partition /dev/sda2, which shouldn't be there. That is what needs fixing.

---

### Post by stonefuzz on 2012-11-20
Ok, thanks a lot.
I'll reply with the fixing results later on.
Cheers

---

### Post by stonefuzz on 2012-11-20
It worked! Thanks once again.
Cheers!

---

