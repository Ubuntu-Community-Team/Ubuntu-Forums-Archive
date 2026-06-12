---
title: "copy os (bootable)"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by aksx on 2009-12-22
hey i am using ubuntu from my 4Gb usb.Now the space is running out and i want to shift it to my other 8Gb usb without loosing my settings or updates that i have downloaded. is it possible????
and also i have windows 7 on my pc is there any software which would help me do it.

thankx

---

### Post by medicalystoned on 2009-12-22
can't you just copy one to the other and see if it worked?  i don't know why it wouldn't work to just transfer all files from one to the other.

---

### Post by aksx on 2009-12-22
i dont have Linux on the other usb drive, it is ntfs and with no data on it . i want to sort of clone my os to my new drive.and i m not terminal friendly....

---

### Post by medicalystoned on 2009-12-22
have u tried it?  just don't erase the original usb drive.   i don't really know and am curious.  you have ubuntu on a removable usb stick correct?  in theory your os goes with you and then can be used in any pc.... right?

---

### Post by aksx on 2009-12-22
yes it is on my removable usb and works seamlessly. (only some systems do not support compiz but works after driver update)

---

### Post by itang sanjana on 2009-12-22
> **medicalystoned said:**
> can't you just copy one to the other and see if it worked?  i don't know why it wouldn't work to just transfer all files from one to the other.

Yup, and perhaps you could use rsync to done the job. See [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by medicalystoned on 2009-12-22
ok first off, i am so jealous. i have always wanted to do that but one of the reasons i run linux is free..... i can't even afford a usb stick unless i got one for free..... any how, so just try transfering it all as one file from stick to the other.

---

### Post by sandy8925 on 2009-12-22
Even if you copied it over it might not work since there's no bootloader installed on the 2nd pendrive. It might work if you cloned it exactly though.

---

### Post by aksx on 2009-12-22
.@medicalystoned
thankx for the appreciation.
@sandy8925
so how would i install the boot loader????

---

### Post by medicalystoned on 2009-12-22
> **sandy8925 said:**
> Even if you copied it over it might not work since there's no bootloader installed on the 2nd pendrive. It might work if you cloned it exactly though.

so what does that mean exactly? is that "grub"? would that not follow with a full transfer of files?   please excuse my ignorance on the subject..... peace

---

### Post by aksx on 2009-12-22
i dont know about Linux but i used bootsect.exe for windows 7 to make my usb bootable for installation so is there a similar command for this???

---

### Post by aksx on 2009-12-22
hey i tried to copy it but windows does not support ext3. how else am i supposed to copy it???

---

### Post by aksx on 2009-12-22
hey i tried partimage too but it didnt work for me ...
any other tool available please inform..

---

### Post by aksx on 2009-12-22
Hey guys I have finally done it.(partimage didnot work well)
Ifirst I formatted the new USB and gave it the same partations
as the older one (3.5Gb primary, 220mb Swap)
the using terminal
```
sudo dd if=/dev/sdb1 of=/dev/sdc1 bs=512k
```
the bs is for byte size,it increased the speed.
It took 153.61seconds to complete.

Then unpluged the drive replugged it and from gparted
resized the primary partition to 7.8Gb.

At the end from teminal
```
sudo grub-install --root-directory=/media/disk /dev/sdc 
```
which compleated it....

---

