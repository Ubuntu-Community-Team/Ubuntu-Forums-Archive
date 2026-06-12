---
title: "Location of GRUB in dual-boot installation"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by Cicero480 on 2007-03-10
Hi. I'm considering installing Ubuntu 6.10 in order to create a dual-boot system with Windows XP. I have two hard drives and my desired configuration is as follows:
[LIST]
[*]On /dev/hda, Windows XP is currently installed, and its native boot loader is located on the master boot record (MBR) of that hard drive. I want to leave everything on that drive unchanged, including the old boot loader, so that if /dev/hda is placed first in my system's boot order, it will boot straight to Windows as it used to.
[*]I'd like to install Ubuntu on /dev/hdb and place GRUB on that hard drive's MBR, so that I can place it first in the boot order and boot to either Ubuntu or Windows from that drive.
[/LIST]
I think I understand what I need to do in the graphical installation to do this, except that I'm not sure where GRUB will be placed. What do I need to do during Ubuntu installation to ensure that GRUB is placed on the MBR of /dev/hdb and that /dev/hda will not be touched?

(Also, after installation, can I expect GRUB to be able to boot to either OS pretty much automatically? If not, could someone provide a link to documentation on setting GRUB up to boot Windows XP properly?)

Thank you for any assistance. If I can provide any additional information to help you answer my question, please let me know.

---

### Post by nero_86 on 2007-03-10
It is exactly my configuration. If you have Win installed you can run the livecd and then start the installation.
When requested build the partitions on hdb whit a little (40 M) partition for the /boot mount point.
Then istall the system. During the configuration grub will automaticly detect your win partition in hda and add the system at the boot of the computer.
hda is not touched and the default system is linux.

---

### Post by Herman on 2007-03-10
Just to make sure, you should make a backup of your hda MBR with a 'dd' command from a LiveCD, here's how, [MBR backup and restore]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd")

Regards, Herman :)

---

### Post by Herman on 2007-03-10
> On /dev/hda, Windows XP is currently installed, and its native boot loader is located on the master boot record (MBR) of that hard drive.That's an abbreviated way to say it but it is extremely misleading to new users. :)

As you are probably well aware, the space in one sector is only 512 bytes, and in the MBR, some of that needs to be reserved for the partition table. There is only enough room for a small amount of code to 'point' to a partition where a boot loader will be installed. This small 'pointer' code that is written to MBR is called 'stage1' of a bootloader.

The real part of the boot loader is installed in a partition. 
If it is Windows, you have NTLDR, NTdetect and your boot.ini file.  
In Ubuntu, we have our /boot/grub/stage2 and our menu.lst file.

NTLDR is 250032 bytes, NTdetect.com is 47564 bytes, and boot.ini is another 234 bytes in my PC. That makes 297830 bytes altogether!

My grub stage2 in Ubuntu is 105652 bytes, 4435 bytes for  menu.lst,  7508 bytes for e2fs_stage1_5, 197 bytes for default, and 47 bytes for device.map, and that's only a few of grub's files. My necessary grub files total 158471 bytes.

So obviously it is a ridiculous statement to say one has a boot loader installed in one's 512 byte MBR. 

I just wanted to make sure people reading this will not be misled, because it does cause some people some concern. Some people seem to think that their entire Windows boot loader is in the MBR and will be overwritten with Grub, which is not the case at all.

Regards, Herman :)

---

### Post by Cicero480 on 2007-03-11
Thank you very much for your replies, Nero and Herman. I think that's everything I'll need to know.

> **Herman said:**
> Just to make sure, you should make a backup of your hda MBR with a 'dd' command from a LiveCD, here's how, [MBR backup and restore]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd")

Regards, Herman :)

I was hoping to do exactly that but had no idea how. This link will be very helpful.

> 
So obviously it is a ridiculous statement to say one has a boot loader installed in one's 512 byte MBR.

I just wanted to make sure people reading this will not be misled, because it does cause some people some concern. Some people seem to think that their entire Windows boot loader is in the MBR and will be overwritten with Grub, which is not the case at all.


Actually, I misunderstood this myself. (I didn't know that the MBR was only one sector.) So thanks also for the correction.

---

### Post by louieb on 2007-03-11
confused57 and myself just got finished walking a guy through close to the same thing you want to do. XP on master, Linux on Slave. GRUB on slave MBR. only real diffrence is he had Win98 on the slave drive also. Might help to take a look before you start.
[http://ubuntuforums.org/showthread.php?t=376253](http://ubuntuforums.org/showthread.php?t=376253)

---

### Post by Cicero480 on 2007-04-12
A quick addendum: I've since performed the installation as it was discussed above. I encountered some errors and then resolved them at the thread "[GRUB Errors 17 and 13 immediately after dual boot installation]("http://ubuntuforums.org/showthread.php?p=2442724")". For anyone else using the above as a guide, the problem was that I installed Ubuntu (and GRUB along with it) and then messed with my system's boot order afterward, causing errors in GRUB. If you do what's described above, it's important to get your boot order the way you want it first and then let GRUB configure itself. Details are at the other thread.

---

