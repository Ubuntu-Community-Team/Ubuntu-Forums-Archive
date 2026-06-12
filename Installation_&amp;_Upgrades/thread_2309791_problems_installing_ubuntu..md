---
title: "problems installing ubuntu."
date: 2016-01-13
forum: Installation &amp; Upgrades
---

### Post by gijs4 on 2016-01-13
hello, im new to ubuntu and to linux.

the device im trying to install ubuntu on is my old acer aspire switch 10 wich runs on windows 8.1 at the moment.a

the reason i want to install ubuntu is that i wanted to give ubuntu a good try on my old laptop before installing it on my regular laptop and desktop.

but here are the problems, i downloaded the ubuntu 14.04.3 and the ubuntu 15.0 files and both have them set up on an usb drive.

but i somehow cant unstall them from the usb drive. ive started up in the bios and chanced the prefered boot device to usb hdd, and then restarted it with the boot menu option.

but all it allows me to do is use the windows boot menu setup.


at first i tried ubuntu 15.0, and when that diddnt work i decided to try ubuntu 14.04.3 wich gave me the same result.

can someone please tell me what i might be doing wrong?

---

### Post by yancek on 2016-01-13
Did you do an md5 checksum on the downloaded iso files?
How did you put them on the flash drive?  Simply copying them to the drive is pointless.  It won't work.  Since you have windows running, download the pendrivelinux software or the windows version of unetbootin and use that to correctly create a bootable flash drive.  If you've done this, please post back to confirm.  Do an online search for either software and you should get the site with the download.

If windows 10 was pre-installed, it is likely to be using UEFI.  Dual booting windows 10 and Ubuntu UEFI is explained at the site below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by gijs4 on 2016-01-14
thank you for pointing out this obvious flaw in my method :)

ive used pendrivelinux to make my usb to a UUI, and the software also put ubuntu 15.10 on it.

but when i start up my old acer in boot menu i can only select the windows boot menu, and the UUI doesnt show up. 

its currently running on windows 8.1, so i think the UEFI wouldnt be the issue. 

ill have another look on the ubuntu site for help but if you can help me it would be great :)

---

### Post by grahammechanical on 2016-01-14
With Windows 8.1 and Windows 10 UEFI is most definitely an issue. If Windows is installed in EFI mode then the Ubuntu live session must also be run in EFI mode so that Ubuntu can be installed in EFI mode. Both OS need to be installed in the same mode. It avoids problems. And there are many posts on this forum from people with problems because Windows & Ubuntu are installed in different modes.

Regards

---

### Post by gijs4 on 2016-01-14
ive had a look at the EUFI guide,

and since my old laptop is a intel atom based windows device on 32bit windows, and im not that experienced with software ive decided not to go trough with the ubuntu on it.

the guide tells me that i need a "complicated work-around" on my laptop and i just dont wanna mess things up. 

so in a few days ill give ubuntu a try on my new laptop to see what its like.

thanks for your help anyways :)

---

