---
title: "Booting to RAID 5"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by un_dave on 2007-11-18
Hey all,
I'm in the process of completing my project described here:
[http://ubuntuforums.org/showthread.php?t=552093](http://ubuntuforums.org/showthread.php?t=552093)

And i've got to the point where i need to boot the system up. Current layout is:
sdb1, sdc1, sdd1 are 100mb partitions, raid 1, and contain the contents of the boot folder. 
this is /dev/md1, and will be mounted at /boot
sdb2, sdc2, sdd2 are the remaining space left on the drives, raid 5, and contains root, which at the moment is a copy of my current root folder on my in-use single drive. 

For setting up, i have:
/dev/md0 mounted to /mnt/raid
and
/dev/md1 mounted to /mnt/raid/boot 

I've run the grub installer with these commands, 
sudo grub-install --root-directory=/mnt/raid --no-floppy /dev/sdb
sudo grub-install --root-directory=/mnt/raid --no-floppy /dev/sdc
sudo grub-install --root-directory=/mnt/raid --no-floppy /dev/sdd

And edited the /mnt/raid/boot/grub/menu.lst:
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic (raid 5)
root		(hd3,0) 
kernel		/vmlinuz-2.6.22-14-generic root=UUID=f0083520-dc7e-4104-b98d-445588f9dd10 ro quiet splash
initrd		/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (raid 5) (recovery mode)
root		(hd3,0) 
kernel		/vmlinuz-2.6.22-14-generic root=UUID=f0083520-dc7e-4104-b98d-445588f9dd10 ro single
initrd		/initrd.img-2.6.22-14-generic

```

as well as the /mnt/raid/etc/fstab:

```
# Entry for /dev/md0 :
UUID=f0083520-dc7e-4104-b98d-445588f9dd10 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/md1 :
UUID=f1763bb0-775e-476b-bdeb-940455eb6be5 /boot ext3 defaults,errors=remount-ro 0 1

# Entry for /dev/sda1 :
/dev/sda1 /mnt/old_drive ext3 defaults,errors=remount-ro 0 1

# Entry for /dev/sda5 :
UUID=544540d3-cf22-4823-9fba-15d3fb114ac6 none swap sw 0 0

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
```

However when I try to boot from either of the two listed in that menu, it hangs. (soft crash, i can press ctrl-alt-del and restart) In recovery mode, it often stops after getting to a line like sdd 5:0:1:0: Attached SCSI Disk, however there doesnt seem to be any error messages. 
It doesn't seem to be connecting to /dev/md0 yet, so there are no changes to the logs. 

Can anyone see where i've gone wrong?

---

### Post by un_dave on 2007-11-18
Just a quick thought. I have grub 0.95 installed, or whatever the default is for ubuntu 7.10. 

I notice there is Grub2 around now. Should I be using that instead?

---

### Post by un_dave on 2007-11-19
Ok, i had an epiphany last night, and while i should have been sleeping, i was messing around with this.
In grub, there's a file called menu.lst, which essentually sets up the grub boot menu, and tells each entry what to do.
In mine, i have an entry like this:

title           Ubuntu 7.10, kernel 2.6.22-14-generic (raid 5)
root            (hd1,0)
kernel          /vmlinuz-2.6.22-14-generic root=UUID=f0083520-dc7e-4104-b98d-445588f9dd10 ro quiet splash
initrd          /initrd.img-2.6.22-14-generic
quiet

Now, (hd1,0) is the address of one of the 1tb, hdd, the first partition, which is part of the mirrored raid for the boot partition. Grub doesn't seem to care that it's mirrored, and can just read the partition as a regular drive.

So when I run all that on boot, i get the ubuntu splash screen, which hangs at about 1%. If i drop the 'quiet splash' stuff, i basically get the initrd thing starting up as per normal. However, at some point, it simply stops. No error's are reported, and if i hit any keys they're echoed on the screen. Interestingly, when i hit ctrl-alt-del to restart, i get something along the lines of :
MD going down, or MD stopping, or something like that, before it restarts.
mdadm is the software raid tool, and the raid drives are mounted as /dev/md0-1.

So the hanging to me seems to indicated that for some reason the boot kernel can't mount/deal with the root i provided,
root=UUID=f0083520-dc7e-4104-b98d-445588f9dd10 or
root=/dev/md0
(they should be the same thing)

But, the message it gives me before it reboots seems to indicate that the raid handling module is loaded in the boot kernel.

So why cant i boot?

---

### Post by Zimmer on 2007-11-20
I was just passing, looking for info for setting up RAID for my son's machine (No RAID here).
I have many links open here, 
[http://ubuntuforums.org/showthread.php?t=504463](http://ubuntuforums.org/showthread.php?t=504463)
Lots of good info and
this one re GRUB may help you, I cannot, since I still haven't a clue myself.... good luck...
[http://www.linuxsa.org.au/mailing-list/2003-07/1270.html](http://www.linuxsa.org.au/mailing-list/2003-07/1270.html)

---

### Post by un_dave on 2007-11-29
Well, I've now admitted defeat. 

After trying everything i could think of, and more. I've ended up not being able to get the root partition to reside on the raid 5. I can get everything to work right up to the grub bootloader, but then it doesn't seem to want to mount the raid, and the boot halts. 

I've fallen back on having a raid 5 /home, and / living on a single disk. 

The frustrating thing is that at no point has anyone said that this can't be done. It's just that no-one seems to be able to tell me how to do it!

---

### Post by psusi on 2007-11-30
Switch splash to nosplash and see what exactly is going on.  Need specific error messages.  Also you want root (hd0,0) in menu.lst.  There is no sense trying to load from the third drive, which won't even be there in the event that one of the drives fails.

---

