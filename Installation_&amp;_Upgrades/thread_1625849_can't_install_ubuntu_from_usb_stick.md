---
title: "can't install ubuntu from usb stick"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by nowardev on 2010-11-19
i mean 
i have 3 usb stick 
all 3 working in a  friend's computer 

on my sick toshiba equium i can't get one working .

my friend has a usb stick that work on my pc but i can't understand why.

i have tried every sick thing like 

fat32 boot flag 3 gigs

i have tried to change head cylindres and what ever nothing nothing nothing 

i can 't understand why this works 


isk /dev/sdb - 1031 MB / 984 MiB - CHS 1015 **32 62  **                                                                  
Current partition structure:                                                                                          
     Partition                  Start        End    Size in sectors                                                   
                                                                                                                      
 1 * FAT32 LBA                0   1  1  1014  31 62    2013698      


and these not 


Disk /dev/sdc - 4002 MB / 3817 MiB - CHS **486 255 63 **                                                                  
Current partition structure:                                                                                          
     Partition                  Start        End    Size in sectors                                                   
                                                                                                                      
 1 * FAT32                    0   1  1   485 254 63    7807527 [MYLINUXLIVE]     


Disk /dev/sdb - 4001 MB / 3816 MiB - CHS 486 255 63                                                                   
Current partition structure:                                                                                          
     Partition                  Start        End    Size in sectors                                                   
                                                                                                                      
 1 * FAT32                    0   1  1   485 254 63    7807527  


isk /dev/sdc - 8054 MB / 7681 MiB - CHS **7803 32 63  **                                                                 
Current partition structure:                                                                                          
     Partition                  Start        End    Size in sectors                                                   
                                                                                                                      
Warning: Incorrect number of heads/cylinder 255 (FAT) != 32 (HD)                                                      
 1 * FAT32 LBA                0   1  1  3657  31 63    7374465

---

### Post by mikewhatever on 2010-11-19
If this is a help request, why don't you start over by explaining what happens when you try installing.

---

### Post by nowardev on 2010-11-19
well...i mean... it doesn't boot. i can't even try ubuntu because it doesn't boot.
so now... i could call my friend everytime i mess up my system? of course not
the problem is make these sick usbstick bootable with ubuntu inside because without them i can't install it.

---

### Post by Quackers on 2010-11-19
How did you put ubuntu on the stick? I haven't used a stick myself, I use cd's but I think you have to use something to make it bootable, like unetbootin.

---

### Post by sikander3786 on 2010-11-19
> well...i mean... it doesn't boot. i can't even try ubuntu because it doesn't boot

Are you sure you selected your USB drive as the first bootable device from Bios menu?

> I think you have to use something to make it bootable, like unetbootin.

Yes unetbootin.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

Or some more options here.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by nlsthzn on 2010-11-19
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Select USB on step two and follow the steps, have not failed me yet ;)


Neil

---

### Post by nowardev on 2010-11-20
just to be clear...
-cd doesn't work (damaged drive)
-i can't call my friend to install linux :( everytime i mess up something

NOW :S

ok what i have used :

1-unetbootin
2 boot sequence i have tried every combination : usb, fdd, cdrom, hdd
  my friend usbstick works ... :S my usbsticks no :(
3 formated on fat32 flag boot

i guess the problem is in the bios i can't understand these picture for example  
 
look at the sick bios :

[COLOR="SeaGreen"]**with the usb stick that works (my friend one )**[/COLOR]

[http://simplest-image-hosting.net/jpg-0-201120108680](http://simplest-image-hosting.net/jpg-0-201120108680)

[COLOR="Red"]**with the others don't work **[/COLOR]

[http://simplest-image-hosting.net/jpg-0-201120108690](http://simplest-image-hosting.net/jpg-0-201120108690)

[COLOR="SeaGreen"]**now ANOTHER BIOS with the same sick usbstick THAT WORKS :s**[/COLOR]

[http://simplest-image-hosting.net/jpg-0-20112010872](http://simplest-image-hosting.net/jpg-0-20112010872)

Look a that!!!! unbelievable!!! i can't figure out why in the other bios works and mine bios doesn't want recognize my usb stick

---

### Post by nowardev on 2010-11-21
Up usb expert!!!

---

### Post by Kangarooo on 2011-05-21
Check here what to do- [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) there download witch version u want. Try newest but recomended is LTS vesrsion
SO 1st step in [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) is download then check step 2 and choose how u want to put it on USB from witch OS and there ull have button to format. So thats it. Also if u want to just format u can on Windows left click usb drive in My Comp and format or in Ubuntu the same left click and format.
In Xubuntu u can try understand that theres also format possibility in same programm witch is in [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) in step 2

---

