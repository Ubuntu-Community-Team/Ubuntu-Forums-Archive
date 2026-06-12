---
title: "Can't mount Ubuntu 14.04.1"
date: 2014-10-28
forum: Installation &amp; Upgrades
---

### Post by Djanguez on 2014-10-28
Hello everybody, I am trying to install Ubuntu for the first time.

I have a Macbook Pro 2.2 GHz Intel Core i7 16GB. 

I downloaded the Ubuntu Desktop 14.04.1 LTS (64bit) and toasted it to a DVD. I did it once with Toast Titanium and another with Disk Utility. Both ways, when I insert the DVD the computer doesn't recognize it and says "The computer doesn't read the inserted disc".
Then I tried to mount the .iso file and copy to a USB, but when I try to mount the file, it says "file system can not be mounted".

Do you know what might be the problem? 

Thank you

---

### Post by yancek on 2014-10-28
You need to burn the iso file of Ubuntu as an image and not copy it to the DVD.  

> Then I tried to mount the .iso file and copy to a USB,

That won't work.  Google "unetbootin" and download the version for Mac and use that software to put the Ubuntu iso on a flash drive, then reboot your computer with the flash set to first boot priority.

---

### Post by flaymond on 2014-10-28
Greetings! ):P. Im new here! and I had the same problem with you...but it fixed with just a few tries...i prefer you to try Unetbootin or UUI (for your usb method)...These softwares help you 'change' your drive to 'bootable' drive. Example, if you had a Windows installation disk...when you open it...it doesnt have any file other than 'Bootable' or hidden NSTP(i guess its NFTS) that you CANNOT open. It just direct you to the installation menu. so...in your case...you can use the softwares given..and follow the instructions....'burn' your iso file using these sofwares to the drive. after it finished...safely eject your drive and put it back to make sure your file is completely 'burned'. then, restart your pc...wait until first screen appear,then click a button TO CHANGE BOOT DEVICE (f12 for acer)...then click arrow down until you find your USB name or HDD.click enter and you will directed to the Ubuntu Installation Menu. Hope that help! :p

---

### Post by Djanguez on 2014-10-29
It worked! Thanks a lot for your advice :)

---

