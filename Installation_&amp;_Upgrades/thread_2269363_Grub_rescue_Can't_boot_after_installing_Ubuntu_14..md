---
title: "Grub rescue: Can't boot after installing Ubuntu 14.10 next to Windows 8.1"
date: 2015-03-15
forum: Installation &amp; Upgrades
---

### Post by andy37927 on 2015-03-15
The error message is:
error: unknown filesystem.
grub rescue>

I installed ubuntu next to windows and it worked fine for about 2 days, I was able to choose in GRUB which OS I want to boot and both of them worked.
Then i turned off my laptop (Lenovo Y50 70), and next time I tried to turn it on all I got was this error message. I didn't make any changes to the computer immediately before this.

Please help me restore grub, or at least save my files from my windows partition.
I have an ubuntu live cd (pendrive), and an external hdd to work with.
Please also tell me what other information to post.

Thanks in advance.

---

### Post by ajgreeny on 2015-03-15
I think you need to run Boot-repair (in my signature) and show us the pastebin link it gives you.  Don't accept the default repair at this stage; until we know what is going on it's best to get all the info we can.

---

### Post by andy37927 on 2015-03-15
I ran the BootInfo summary, here it is: [http://paste.ubuntu.com/10605881/](http://paste.ubuntu.com/10605881/)

---

### Post by oldfred on 2015-03-15
You have an empty extended partition. 
And Boot-Repair says your left Windows 8 hibernated or its always on hibernation which it calls fast boot.

You may be able to restore the Linux partitions with testdisk. It is in repository so you can use it from Ubuntu's live installer.

       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)


 WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast startup
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

---

### Post by andy37927 on 2015-03-15
I ran the recommended repair, but I still get the same error. It gave me this url: [http://paste.ubuntu.com/10606461/](http://paste.ubuntu.com/10606461/)

---

### Post by andy37927 on 2015-03-15
Thanks I will try that tomorrow.

---

### Post by oldfred on 2015-03-15
You did not restore a partition using testdisk?

---

### Post by andy37927 on 2015-03-17
I decided to just reinstall my entire system.

My windows partition was stuck in a hibernated state (because of fast-boot), but I managed to mount it as read-only, and save my files with the following instructions:

```
sudo mkdir /media/windows
sudo mount -t ntfs-3g -o ro /dev/sda3 /media/windows
```

I am including these here because I found them to be very useful.

This thread can be archived now, though I'm not sure if it is "solved" because I have given up on restoring GRUB.

Thank you for you answers.

---

