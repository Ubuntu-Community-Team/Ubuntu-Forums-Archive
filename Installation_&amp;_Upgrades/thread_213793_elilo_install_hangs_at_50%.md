---
title: "elilo install hangs at 50%"
date: 2006-07-11
forum: Installation &amp; Upgrades
---

### Post by majestikmoose on 2006-07-11
Hi guys,

I'm trying to tri-boot on my macbook, but I'm having some difficulties install dapper.  The installation seems to finish up, but then when it tries to install elilo it hangs at 50% everytime.  I've burned the disk at 2x just in case, and it's still doing the same thing.  Has anyone run into this problem here?

---

### Post by quini on 2006-10-07
Hallo!  I'm also trying to install 6.06.1 on a friend's Macbook (no windows in that machine  ;) ), and I'm experiencing the same behavior.

It stops at 50% of "instaling elilo on hd", and at the bottom "running ELILO for /dev/sda1" (both translated from english).

Help is welcome!!  ;)

---

### Post by Kerdobald on 2006-11-05
Hi i've the same problem...

No idea anywhere?

Please, if someone has any idea, so i would very pleased to know it

I want to leave my windows... And don't want to use Mac Os...

I've a new Intel iMac...

---

### Post by Kerdobald on 2006-11-05
The console shows me that:

```

[...]
apt-install: Setting up efibootmgr (0.5.1-1ubuntu1)
apt-install: Setting up elilo (3.6-1ubuntu5)
elilo-installer: Couldn't load efivars module - is it statically linked? 

```

---

### Post by Kerdobald on 2006-11-06
Could it be, that there are serios problems with imac, efi and elilo?

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=381584](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=381584)

---

### Post by Kerdobald on 2006-11-10
I followed that guide:

[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu)

But it seems iMac is not supported very well, or not?

---

### Post by cabdouch on 2007-12-03
I had the same experiance and found the following to work.

The problem was that when the install did a "modprobe efivars" it hung.

I used the [CTRL]+[ALT]+[F2] to switch to another tty session and ran the command "ps -ef" 
(Note: MAC Keyboards have the ALT Key marked Option)

This gives a detailed list of the processes running. Near the bottom you should see a process that is running "modprobe efivars"
Look at the process identification (PID) which is in the 2nd column and kill it
kill {PID}
Switch back to the install tty with [CTRL]+[ALT]+[F1]
(Note: MAC Keyboards have the ALT Key marked Option)

You should see the installer continue running.

NOTE: If efivars didn't get loaded, then chances are that Linux was unable to modify the EFI Boot Manager, or copy the boot files to the EFI Partition. You may have to do this step manually and you need to do it before you end the install. Usually I do this manual step at the end of the install when Linux wants me to press "Continue" to reset and reboot the system.

You may have to also make sure you have installed the packages "elilo" and "efibootmgr" as part of the install process.
To do this manually, I switch back to the other session with the [CTRL]+[ALT]+[F2]

Note: Linux has mounted the install partition as /target
I install the EFI Partition as /mnt using the following command.
mount /dev/sda1 /mnt
Note: This may be different based on the system you have. Your EFI Partition may be /dev/hda1 or may be /dev/sda2, /dev/hda2, or something else.
How can you tell?
Try dumping the partitions files in proc to get a hint.
cat /proc/partitions 
Perhaps try listing the /dev directory for a hint based on what /dev/sd?? or /dev/hd?? partitions have entries.

Once you have mounted your EFI partition as /mnt then you need to copy the boot files to it
cp  /target/initrd.img  /mnt
cp  /target/vmlinuz  /mnt

You will also need to obtain a copy of elilo.efi to copy to it. It should have been installed to the Linux directory (/target) somewhere:
find  /target  -name  elilo.efi

Once you have these three files, then should GRUB not work and you need EFI Boot files, you will already have them.

Then you just need to know how to kick off the boot from EFI. I use the following command:
elilo  -i  initrd.img  vmlinuz  ro root=/dev/sda3
Note: you will have to substitute for sda3 the actual device and partition of your Linux install.

Hope this helps

---

### Post by cabdouch on 2007-12-03
Another way to find out where the EFI and Linux partitions are, is during the install, type "mount" and see where the /target mount came from.
example:
/target  /dev/sda3

Hopefully it isn't one of the convaluted /dev/usb/usb-host/host0/bus0/....

---

