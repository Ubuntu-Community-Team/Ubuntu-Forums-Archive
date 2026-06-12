---
title: "Can't burn boot disk"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by lift_test on 2010-07-31
Very puzzled, have previously burnt many iso Ubntu disks with no problems but evry time I try whether Linux or win I cannot boot from the disk.  The burnt disk shows separate files rather than a single iso.  I've tried them on 3 different computers with the first boot device set to CD and they all boot normally into Grub (except the netbook which only has XP).  Any ideas please.

---

### Post by howefield on 2010-07-31
You checked the integrity of the download and burned CD ?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by tommcd on 2010-07-31
> **lift_test said:**
>  The burnt disk shows separate files rather than a single iso.
NOTE: That is how an iso image CD is supposed to look when it is mounted and opened in a directory. If it shows as a single .iso file, then it was not burned as an iso image. It was just copied to a CD.
> **lift_test said:**
> 
  I've tried them on 3 different computers with the first boot device set to CD and they all boot normally into Grub (except the netbook which only has XP).  Any ideas please.
Be sure to burn the iso image at the slowest possible speed. If burning from Windows, use **Iso Recorder** or **Infra Recorder**:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
If you are burning from Ubuntu, simply right-click on the iso and choose "write to disc" and choose the slowset possible speed.
Then check the CD for defects when you boot it as Howefield said.

---

### Post by lift_test on 2010-07-31
> **tommcd said:**
> NOTE: That is how an iso image CD is supposed to look when it is mounted and opened in a directory. If it shows as a single .iso file, then it was not burned as an iso image. It was just copied to a CD.

Be sure to burn the iso image at the slowest possible speed. If burning from Windows, use **Iso Recorder** or **Infra Recorder**:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
If you are burning from Ubuntu, simply right-click on the iso and choose "write to disc" and choose the slowset possible speed.
Then check the CD for defects when you boot it as Howefield said.

I have tried in both windows AND Ubuntu.  Exactly as stated in the How To.  I am downloading again in case the original iso was corrupted.

---

### Post by tommcd on 2010-08-01
> **lift_test said:**
> I have tried in both windows AND Ubuntu.  Exactly as stated in the How To.  I am downloading again in case the original iso was corrupted.
Downloading from another mirror is a wise choice. It is entirely possible that the mirror you were using had corrupted iso images. It does happen.

Make sure the PC is set to boot from the cdrom as the first boot device.
Make sure to burn the CD at the slowest possible speed.
Make sure to run the option :"*check disc for defects*" before installing.

... And you should be good to go and rock on with Ubuntu!!!

---

