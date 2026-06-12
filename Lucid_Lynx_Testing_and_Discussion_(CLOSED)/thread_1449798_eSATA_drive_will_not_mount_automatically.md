---
title: "eSATA drive will not mount automatically"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by oobuntoo on 2010-04-08
Does Linux have the ability to mount eSATA drive automatically like it does with USB drive? Lucid, at least, doesn't seem to know the difference between internal SATA and external SATA drives.

---

### Post by psusi on 2010-04-08
Indeed, it doesn't know it is external.  You either need to manually mount it, or add a line for the drive to your /etc/fstab for it to auto mount.

---

### Post by MacUntu on 2010-04-08
AFAIK it's not possible because there's no difference between eSATA and SATA other than the potential/connector/cable specifications (they share the same protocol and logic).

---

### Post by dannyboy79 on 2010-04-08
> **oobuntoo said:**
> Does Linux have the ability to mount eSATA drive automatically like it does with USB drive? Lucid, at least, doesn't seem to know the difference between internal SATA and external SATA drives.

teh libata driver (if that's what it's using) can not hot plug the esata device. i found this out back in feisty or hardy if I recall. you just need to make sure it's plugged in prior to boot, add a line in your fstab to automount it and you'll be set.

---

### Post by cariboo on 2010-04-08
I don't know if this still works, as I don't have any eSATA drives at the moment. I found that if I had a usb device plugged in, the eSATA drive would get detected and mounted automagically.

---

### Post by powder on 2010-04-08
AHCI enables SATA hot swapping so perhaps if you enabled AHCI in your BIOS and reinstalled the OS hot plug might be possible.

---

### Post by dannyboy79 on 2010-04-08
only some sata chipsets in combination with linux drivers support hotpluging eSATA. See here: 
[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)
and then use a ctrl-f  and search for hotplug. Good luck!

---

### Post by oobuntoo on 2010-04-08
> **psusi said:**
> Indeed, it doesn't know it is external.  You either need to manually mount it, or add a line for the drive to your /etc/fstab for it to auto mount.

Yes, I can mount it like it's an internal drive by adding relevant info to fstab. The only problem is that I have to leave my eSATA drive attached while booting or I'd get a complaint that the drive is not ready and have to manually tell it skip waiting for the drive.

---

### Post by oobuntoo on 2010-04-08
After searching around a little more, I came across this site:

[http://vstone.eu/2009/04/hal-and-auto-mounting-external-e-sata-devices/](http://vstone.eu/2009/04/hal-and-auto-mounting-external-e-sata-devices/)

I made changes to my /etc/hal/fdi/policy/preferences.fdi file with the following info:

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
     <!-- My eSATA -->
    <match key="storage.serial" string="SATA_WDC_WD3200BEVT-11ZCT0-_WD-WX30A89S2059">
        <merge key="storage.is_external" type="bool">true</merge>
    </match>

    <!--         DONT CHANGE           -->
    <match key="storage.is_external" bool="true">
        <merge key="storage.removable" type="bool">true</merge>
        <merge key="storage.hotpluggable" type="bool">true</merge>
        <merge key="volume.ignore" type="bool">false</merge>
    </match>
    <match key="@block.storage_device:storage.is_external" bool="true">
        <merge key="volume.ignore" type="bool">false</merge>
    </match>
  </device>
</deviceinfo>
```

I've got my drive serial number with this command:
```
sudo hdparm -I /dev/sdh1
```

It seems to be working so far although it's taking like half a minute for the drive to get mounted.

---

### Post by Jordanwb on 2010-04-08
You might be able to write a udev rule to automount. Not sure how to do that though.

---

### Post by cariboo on 2010-04-08
Has a bug been filed?

---

### Post by oobuntoo on 2010-04-09
I've found two similar bugs had been filed, but probably under different releases.

[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/452256](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/452256)

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/153768](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/153768)

Do I have to file another for Lucid?

---

### Post by Killigrew on 2010-04-09
no, making a comment to the one regarding devicekit, 
and sending a bug report like stated in the comments would help.

greetings

---

### Post by psusi on 2010-04-09
HAL is obsolete and being removed.  If you have no entry for it in your fstab, it should just show up automatically on the places menu and be mounted when you try to open it, no differently than an internal drive.  It just doesn't automatically mount it and open a nautilus window there for you when connected like a usb drive does.

---

### Post by oobuntoo on 2010-04-09
> **psusi said:**
> HAL is obsolete and being removed.  If you have no entry for it in your fstab, it should just show up automatically on the places menu and be mounted when you try to open it, no differently than an internal drive.  It just doesn't automatically mount it and open a nautilus window there for you when connected like a usb drive does.

I think you're right. I went back and changed /etc/hal/fdi/policy/preferences.fdi file back to the way it was before and it still automatically mounted my eSATA drive. It took more than a minute after I attached the drive for it to show up. It also asked for a password before I could use the drive. Is that normal?

I guess this is a non-issue after all :biggrin:

---

### Post by psusi on 2010-04-09
Yes, I think it normally asks for admin password to mount internal disks.

---

