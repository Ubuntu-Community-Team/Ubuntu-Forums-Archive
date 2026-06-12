---
title: "Ubuntu on Mac on External Hard Drive"
date: 2014-10-29
forum: Installation &amp; Upgrades
---

### Post by Michael_Newton on 2014-10-29
I have a MacBook Air (2013) which I have OS X Yosemite installed on the main internal SSD. I have successfully installed Windows 8 onto a external USB 3 hard drive and by pressing the Option key upon starting the Mac, I can select the 'EFI Boot' of the external hard drive and load up Windows.

I would now like to try installing Ubuntu using the same method on the same external hard drive. I have followed some instructions on the internet and created two new partitions. One is almost 150 GB which would hold Ubuntu and the other is 8GB for 'swap' (the same as the amount of RAM in my Mac).

I have loaded the Ubuntu Live CD successfully on my Mac and tried to install on the empty partition but it just hangs at 'Detecting File Systems'

Can anyone advise? I don't really want to use any third party boot menus for my Mac. I was hoping that I could get it set up so I can hold Option upon startup, select the EFI partition of the external hard drive and then the Ubuntu Grub boot loader could allow me to select either Ubuntu or Windows on the external hard drive. Leaving my main internal hard drive as the default OS X installation.

Is this possible? Thanks

---

### Post by Michael_Newton on 2014-10-30
After a bit of trial and error, I've finally managed to get Ubuntu working on my Mac via External Hard Drive without affecting my internal SSD. From the partitions I'd already made for Ubuntu on the external drive, I took 100 MB and created a rEFInd partition which I accessed and through the Ubuntu CD, installed Ubuntu alongside Windows 8 on the drive. It all seems to boot up ok however I now have yet another issue to try and resolve.

I have followed the instructions online to install the WiFi drivers however after doing this, whilst I can connect to my 5GHz WiFi, it just refuses to join any 2.4GHz WiFi. I input the WPA password and the little WiFi indicator looks as if its trying to connect, then it just asks me for the password again, and again, etc.

Can anyone advise on what could be the issue?

---

### Post by mi_ickeo on 2015-01-05
I am trying to do something similar. Can you tell me the steps to create rEFInd partition in the external harddisk?

---

