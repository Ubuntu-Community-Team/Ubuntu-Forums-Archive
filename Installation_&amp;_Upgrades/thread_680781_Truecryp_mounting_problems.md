---
title: "Truecryp mounting problems"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by bobo99 on 2008-01-28
Hi there, I seem to be having some troubles mounting with truecrypt.
I have an interneal HD and an external USB HD. 
When I mount the internal HD(Ntfs) everything goes fine.

When I try to mount the USB HD I get this,

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/mapper/truecrypt1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/mapper/truecrypt1 /mnt/tv -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/mapper/truecrypt1 /mnt/tv ntfs-3g defaults,force 0 0
Mount failed




Any help ?


thanks
bojan

---

### Post by doddo on 2008-01-29
Hello!
Firstly, this seems to be a mount issue rather than a truecrypt one.

 Just by invoking
 ```
truecrypt /dev/sdXX 
```
 Does it map the device (under /dev/mapper) (you can list your devices with truecrypt -L)?

[Apparently,]("http://en.opensuse.org/SDB:Windows_partition_not_mounting") this error appears when you do not make a proper shutdown of windows (or safely removing the hardware) before you disconnect the disk

you can try to mount the disk read only:
```
mount -o ro /dev/mapper/truecrypt1 /media/vid
```
Assuming your disk gets mapped as truecrypt1 and you want to mount it on /media/vid

That should let you access the files. 

To solve this issue, boot Windows and mount then safely umount/remove the disk. That should solve it.

Regards!

---

### Post by crimsontime on 2008-04-27
> **bobo99 said:**
> Hi there, I seem to be having some troubles mounting with truecrypt.
I have an interneal HD and an external USB HD. 
When I mount the internal HD(Ntfs) everything goes fine.

When I try to mount the USB HD I get this,

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/mapper/truecrypt1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/mapper/truecrypt1 /mnt/tv -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/mapper/truecrypt1 /mnt/tv ntfs-3g defaults,force 0 0
Mount failed




Any help ?


thanks
bojan

I also encountered this problem and rebooting vista, making sure shutdown is clean does solve the problem.  However this is a big hassle.  I found that you can go into the TrueCrypt GUI Settings>Preferences>Mount Options and enter "force" (don't use quotes) and then it will mount.  I'm sure there is a commandline way to do this as well but I'm a n00b and haven't worked on that yet.:)

---

