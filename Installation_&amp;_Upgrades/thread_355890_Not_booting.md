---
title: "Not booting"
date: 2007-02-07
forum: Installation &amp; Upgrades
---

### Post by Baelfael on 2007-02-07
Earlier today I was updating Dapper Drake to Edgy Eft, and I left it there because it was gathering all the files and was going to take a while. Well I accidentally fell asleep, and what sucks is I don't know if it updated or not, but I'm guessing my laptop ran out of batteries and shut down while it was updating. I can't boot Ubuntu. A big black screen with a white little line at the top left corner and you can type in it and all... is it just being really slow or is something wrong?

---

### Post by raul_ on 2007-02-07
Erm...could you maybe take a picture with your phone or something, and post it?

---

### Post by Baelfael on 2007-02-07
Well what happens is it goes through the first 2 steps of the booting process (it says "ok" 2 times), and then it just stops and I get a black screen with that flashing cursor at the left hand corner.

---

### Post by raul_ on 2007-02-07
But GRUB loads fine right? Can you boot in Windows?

---

### Post by Baelfael on 2007-02-07
I think the GRUB loads, and yes, I can boot windows.

---

### Post by raul_ on 2007-02-07
That's weird. Can you boot in recovery mode?

---

### Post by edubarr on 2007-02-07
You can try to boot into the system if you have a livecd around. You'll have to boot from the cd, then mount your root partition somewhere and chroot into it. From there you'll probably (and hopefully) be able to run apt and continue with the update.

---

### Post by Baelfael on 2007-02-08
> **edubarr said:**
> You can try to boot into the system if you have a livecd around. You'll have to boot from the cd, then mount your root partition somewhere and chroot into it. From there you'll probably (and hopefully) be able to run apt and continue with the update.

Can you elaborate on that? I'm extremely new to Linux.

---

### Post by edubarr on 2007-02-08
Boot form the CD and open up a terminal. 

1) Mount your filesystem, if it's not yet mounted (I don't know if the liveCD will do it for you). Anyways, you'll need to create a mount point and to know what are your disks. The mount point is simply a directory where the mounted filesystem will be placed. The disks will be on /dev/hdaX for IDE drives and /dev/sdaX for SCSI and SATA drives. The X will be a number that corresponds to your partition. For example, my root partition is on sda3 so for me to mount it on a directory "myroot" on my currently working dir I'd use:
```

mkdir myroot
sudo mount /dev/sda3 ./myroot
```

2) Once mounted, just chroot into the filesystem. It will be possible if it's a 'working' partition (if it has a shell and other things...). 
```
chroot ./myroot /bin/bash
```

3) From here it would be like working with the terminal on your system. Just to run
```
sudo dkpg --configure -a
sudo apt-get dist-upgrade
```

4) After you are done just exit the chroot and unmount the partition:
```
exit
umount ./myroot
```

5) Reboot and hopefully everything works again.

I haven't tested any of this (it's just an idea), but it may work.

---

