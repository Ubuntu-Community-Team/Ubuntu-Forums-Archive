---
title: "boot-repair a corrupted/retired Win7 HDD"
date: 2015-09-26
forum: Installation &amp; Upgrades
---

### Post by 10kJS on 2015-09-26
The 14.04 LTS install was done from a LiveUSB to a USB 128G SSD.  An internal HDD with Win7 somehow got Grub installed without me selecting anything to do that.  Booting from the Win7 SSD internally or via USB now gives the Grub recovery prompt and says 'no device found' with I believe this device that in the beginning of these pastebins:

     search.fs_uuid 4f9b0e8e-99c8-4b72-9d4c-a77de9261ce3 root hd2,msdos1 
I want to be able to boot the previously internal Win7 HDD via the USB if data or a future app not on Linux is ever needed again.
I appreciate all help though obviously want a confident, I accept that there are no guarantees, not a 'try this' solution.

This from the 14.04 LTS installed to internal SSD /dev/sda:
[http://paste.ubuntu.com/12585667/](http://paste.ubuntu.com/12585667/)

Both of these are from the LiveUSB:

    Is sda removable answered 'No'.  It is inside the PC:
        [http://paste.ubuntu.com/12585870/](http://paste.ubuntu.com/12585870/) 


    Is sda removable answered 'Yes'.  It is inside the PC:
        [http://paste.ubuntu.com/12585911/](http://paste.ubuntu.com/12585911/)

---

### Post by grahammechanical on 2015-09-26
Boot Repair has a recommended repair that may solve this problem if you tell Boot Repair that the drive with Ubuntu on is a removable drive. The repair will be:

1) Grub of sda1 will be reinstalled into the MBR of sda which is the the Ubuntu drive.
2) Fix access to other systems for the situations when the removable media is disconnected. This should put a Windows boot manager on sdc, the Windows disk.
3) Remember to make your BIOS boot on the removable disk. That would be sda.

Once you load into Ubuntu open a terminal and run this command

```
sudo update-grub
```

Watch the printout. It should show that grub has detected a Windows boot loader of sdc. It may be sdb by this time as the live session USB stick (sdb?) will have been removed. You should then be able to load from Grub either Ubuntu or Windows and also change boot priority to the Windows drive and just boot Windows.

Regards.

---

### Post by oldfred on 2015-09-26
But you cannot boot Windows as an external USB drive. If drive is eSATA then it may work.

Windows checks and does not allow external drive booting.

---

### Post by 10kJS on 2015-09-27
Have to see if it's eSATA.  Want to remove the Ubuntu SSD anyway to be safe next weekend and install the Win7 HDD and see if the LiveUSB finds it.  If it doesn't find it, then the update-grub probably wouldn't save the config unless I used a persistent version of Linux?

---

### Post by kurt18947 on 2015-09-28
If I understand correctly, the drive under discussion has only Windows on it with no wish for anything Ubuntu? Grub was installed against your wishes? If that's the case, why not do a Windows repair and overwrite anything grub related? If you don't have a Windows 7 disk, they are available via legitimate sources as .iso files. Reinstall the Windows disk and disconnect/unplug any other drives so as to not write to them unintentionally. Apologies if I misunderstand.

---

### Post by 10kJS on 2015-09-29
Yes, am considering the Windows repair utility if someone recommends one for this situation though first I'm going to create a persistent Ubuntu USB stick with the usb-creator-gtk that is installed and see if that finds the internal Win7 with update-grub.  Should report my findings this weekend.

---

### Post by 10kJS on 2015-09-30
The usb-creator-gtk created a persistent Ubuntu however it didn't allow the update-grub to complete.  
Got it recovered with the boot-repair restore MBR advanced option.  I selected it though the suggested repair said it would have done the same thing on [http://paste.ubuntu.com/12627380/](http://paste.ubuntu.com/12627380/)

---

