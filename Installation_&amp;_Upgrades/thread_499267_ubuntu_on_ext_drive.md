---
title: "ubuntu on ext drive"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by reoni on 2007-07-12
i would like to install ubuntu on an external usb 2.0 hard drive which 
   would be used mainly on a dell inspiron 1150 .
   your guidance would be greatly appriciated.

                                              reoni.

---

### Post by compwiz18 on 2007-07-12
> **reoni said:**
> i would like to install ubuntu on an external usb 2.0 hard drive which 
   would be used mainly on a dell inspiron 1150 .
   your guidance would be greatly appriciated.

                                              reoni.

Plug the drive in, put the Ubuntu LiveCD in, click install, and choose the external drive to use.

---

### Post by reoni on 2007-07-12
Thank compuwiz18
  
  i am going to try that tomorrow   
                                reoni.

---

### Post by reoni on 2007-07-14
guys i got to step 7/7 then got a error message 
      the installer needs to commit changes to partition tables  
      the following mount points could not be unmounted 
        /media /new\040volume

        also in advance options  it lists the device for boot loader
        installation as (hd0)
                                            any help on this.
                                                                                        reoni.

---

### Post by compwiz18 on 2007-07-15
All I can suggest is try it again :/ The bootloader device (assuming you only have 1 external drive plugged in) should be hd1 (if you have multiple drives, I suggest you remove them temporarily)

if you have issues with commiting the parition table, you can use gparted (which can be found in System -> Administration -> gparted) to fix the partitions, then run the installer, but don't change the partitions.

---

