---
title: "Problem installing Ubuntu with Raid 0, Grub: No such device"
date: 2011-06-29
forum: Installation &amp; Upgrades
---

### Post by eximius1 on 2011-06-29
I have a raid 0 setup with 2 x 1TB drives. I have an ASUS P8P67 LE motherboard and am using Interl RST for the Raid setup. I'm utterly ignorant of raid and therefore forgive any mistakes...

I already had windows 7 installed and was attempting to dual boot ubuntu. 

I installed Ubuntu from CD. The raid was picked up properly as only one drive by ubuntu. So it picked up the windows MBR and the main windows partition. I resized the main partition and used the "install ubuntu and windows 7 side by side" option. Installation went fine but once I restarted the PC I was welcomed by a grub rescue screen with the message: "error: no such device e196.....". 

Any and all adivce would be appreciated.

Edit: I used the Windows 7 disc to repair the windows bootloader so I can now boot into Windows 7.

Before doing so I used gparted on the live cd to check the partitions on the drives. The only ones present were the MBR and windows one. So ubuntu seemingly didn't install... Although GRUB did... I was advised by someone on the ubuntu IRC chat to avoid trying to reinstall ubuntu at that point just in case there was an error in the partitioning process. 

I've since checked the state of the partitions from within windows and there's the MBR partiton, the windows partiton AND the partition that I created for ubuntu... 965MB of the partition that I created is listed as used space as well...

I have no idea what's happened.

---

### Post by psusi on 2011-06-29
You did a WUBI install from within windows, which doesn't create a partition, but tries to install to a file within the windows partition.  You need to actually boot from the cd and do a normal install instead of trying to run the installer from within windows.

---

### Post by eximius1 on 2011-06-29
> **psusi said:**
> You did a WUBI install from within windows, which doesn't create a partition, but tries to install to a file within the windows partition.  You need to actually boot from the cd and do a normal install instead of trying to run the installer from within windows.

Sorry I didn't explain myself well enough. I burned an ubuntu cd and tried to install ubuntu onto a partition.

EDIT: HERP DERP, does the side by side option use wubi?

---

### Post by psusi on 2011-06-29
No, WUBI is what you get when you run the installer from within windows instead of booting from the cd.  If you boot from the cd, the installer should see both individual drives, typically as /dev/sda and /dev/sdb, as well as the raid volume, named something like /dev/mapper/something.  It is the /dev/mapper/ one you need to install to.

---

### Post by eximius1 on 2011-06-29
> **psusi said:**
> No, WUBI is what you get when you run the installer from within windows instead of booting from the cd.  If you boot from the cd, the installer should see both individual drives, typically as /dev/sda and /dev/sdb, as well as the raid volume, named something like /dev/mapper/something.  It is the /dev/mapper/ one you need to install to.


Yeah I thought so, but didn't want to miss something that might be obvious :P

I'll give it another try tomorrow and post results. Thanks

---

### Post by eximius1 on 2011-07-04
I'm still having trouble. I've got the same error and I'm stuck at the grub rescue screen.

---

### Post by psusi on 2011-07-04
Can you enter the following two commands at the rescue prompt and post their output:

```

ls
set

```

---

