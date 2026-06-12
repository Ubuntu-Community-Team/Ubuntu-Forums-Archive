---
title: "Installer Fails on Installing Grub"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Wlo on 2009-10-03
Hiya.

I have a machine running Windows 7.  When I tried to install Karmic Beta it fails at the Grub stage with "Cannot install the grub bootloader".

I can continue the install fine but don't have grub.

I'm using the Alternate 64 beta.  Tried previously with Alpha 6 both standard 64 and alternate 64 but same thing.

Same install on a Windows 7 laptop was fine.

Any ideas?  Can I add Ubuntu to my Win 7 bootloader or can I install Grub 2 some other way?

Thanks!

Wlo.

---

### Post by Wlo on 2009-10-03
Ah - prolly relevant - I'd done manual partition setup.

Kept my NTFS Win7 at first partition, so am thinking it had probs installing there.

Also Ext4 10gb for /home
Ext4 8gb for /
8gb Swap

So could be failing as it can't install to the NTFS partition where my Win7 loader currently is?

Wlo.

---

### Post by ajgreeny on 2009-10-03
I don't think that should have anything to do with the failure to get grub on the MBR; it's normally put on a disk that is formatted as NTFS these days, as it overwrites the windows MBR as default.  Are you sure the CD you are using is OK?

---

### Post by DougieFresh4U on 2009-10-03
Just finished installing on a multi partition machine. When I rebooted, my Windows 7 didn't appear. Then I ran **sudo update-grub2** and rebooted and all are present

---

### Post by ajgreeny on 2009-10-03
> **DougieFresh4U said:**
> Just finished installing on a multi partition machine. When I rebooted, my Windows 7 didn't appear. Then I ran **sudo update-grub2** and rebooted and all are present
But with no grub it will not be possible to run ```
sudo update-grub2
``` as you did, because the OP will not be able to even get into ubuntu.

---

### Post by Wlo on 2009-10-03
> **ajgreeny said:**
> I don't think that should have anything to do with the failure to get grub on the MBR; it's normally put on a disk that is formatted as NTFS these days, as it overwrites the windows MBR as default.  Are you sure the CD you are using is OK?

Tried with 3 different ISO images (Alpha 6 64 and alternate 64, and alternate beta 64) so defs not the disk.

> **DougieFresh4U said:**
> Just finished installing on a multi partition machine. When I rebooted, my Windows 7 didn't appear. Then I ran **sudo update-grub2** and rebooted and all are present

Windows 7 still loads but don't get Grub or an option for Ubuntu.

CHeers for help :).

Wlo.

---

### Post by Wlo on 2009-10-03
Could I install grub from a live CD?  Live CD boots okay.

---

### Post by VMC on 2009-10-03
> **Wlo said:**
> Could I install grub from a live CD?  Live CD boots okay.

Boot with livecd and follow [**_these_**]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD") instructions.

---

### Post by Longinus00 on 2009-10-03
> **Wlo said:**
> Hiya.

I have a machine running Windows 7.  When I tried to install Karmic Beta it fails at the Grub stage with "Cannot install the grub bootloader".

I can continue the install fine but don't have grub.

I'm using the Alternate 64 beta.  Tried previously with Alpha 6 both standard 64 and alternate 64 but same thing.

Same install on a Windows 7 laptop was fine.

Any ideas?  Can I add Ubuntu to my Win 7 bootloader or can I install Grub 2 some other way?

Thanks!

Wlo.

Is writing to the MBR restricted in bios? If it is grub will have a hell of a time trying to install itself.

---

### Post by Wlo on 2009-10-04
> **Longinus00 said:**
> Is writing to the MBR restricted in bios? If it is grub will have a hell of a time trying to install itself.

Jaunty and Windows 7 were both okay, but good call, I'll check that.  Thanks.

---

### Post by Wlo on 2009-10-05
> **VMC said:**
> Boot with livecd and follow [**_these_**]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD") instructions.

Followed the instructions and Grub installed okay, but when I rebooted only Karmic (and recovery) were listed on the boot menu and that wouldn't boot (something about being unable to access a device and then stuck on a line starting with some numbers).  Rebooted and selected recovery option to run a root shell, tried update-grub2 and lo and behold it found both my operating systems.  Rebooted and can now run both Karmic and Windows 7 fine.

Got there in the end - thanks for your help!  Hope it's not a prob for anyone else, although at least this thread will show up in Google if it is.

Thanks loads for the help, all.

Wlo.

---

