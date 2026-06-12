---
title: "Can't format hard disk...."
date: 2010-12-06
forum: Installation &amp; Upgrades
---

### Post by anubhav.sharma on 2010-12-06
Hi All,
 

I am facing bit similar problem. I have installed ubuntu 10.10 on my machine along with windows 7. My hard disk had 4 partitions as follows: 
[LIST]
[*]25 GB NTFS WINDOWS7
[*]10 GB UNALLOCATED
[*]75 GB EXT4
[*]50 GB EXT4
[/LIST]After installing the ubuntu my windows7 has crached and the 1st partition is now cleaned by ubuntu. Moreover, the ubuntu is also not working properly (means I don't get the login screen). Now I want to re-format my whole hard disk with NTFS only for WIN7 but I am unable to format my hard drive as none of OS is working.
 
Please help me, I am in trouble as I can't use my PC. 
 
Thanks,
Anubhav

---

### Post by Quackers on 2010-12-06
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by anubhav.sharma on 2010-12-06
Thanks.
 
But I don't get the desktop while running the  USB drive with "try ubuntu". The screen freezes after displaying the Ubuntu logo..
 
:(

---

### Post by Quackers on 2010-12-06
Try booting the system normally (without the Ubuntu disc in the drive) and hold down the shift key until the grub menu shows up. This is a white on black menu which will list Ubuntu). When the menu appears the top item will be highlighted. Press the "e" key and a new screen will appear. Using the down arrow and the right arrow navigate to the end of the line that says "quiet splash".  Delete the words "quiet splash and in their place type in nomodeset and then press ctrl and X at the same time. Hopefully Ubuntu will boot up then.

---

### Post by anubhav.sharma on 2010-12-06
Thanks, I will try this out.

---

### Post by anubhav.sharma on 2010-12-11
I tried all the options you suggested.

Please see the attachment for the error I am getting while formatting the hard disk

Thanks,
Anubhav

---

### Post by laithbsoul on 2010-12-11
you could burn gparted live cd and use that to format your hdd [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

