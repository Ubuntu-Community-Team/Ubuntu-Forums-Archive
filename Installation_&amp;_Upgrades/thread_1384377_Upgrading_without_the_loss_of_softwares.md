---
title: "Upgrading without the loss of softwares"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by AmirM on 2010-01-18
Hi,
I'm new to Ubuntu(about 6 months)and I'm using Ubuntu 9.04 jaunty.
I want to install Ubuntu 9.10 from the cd but I dont want softwares that I installed to be lost.what should I do?
(It's the matter of time,internet speed and internet traffic limits)

---

### Post by phillw on 2010-01-18
Hi and welcome to the forums.

Whilst we normally say to do a clean install, if you're stuck for either speed or data allowance, you may be better doing an upgrade to 9.10.

I did this method and it worked okay for me. As with any installation - do take a backup of anything important.

> To upgrade from Ubuntu 9.04 on a desktop system, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '9.10' is available. Click Upgrade and follow the on-screen instructions. 
 Once that is running happily, I recommend upgrading to Grub2, that can be done here --> [https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202")

My how to on upgrading from ext3 --> ext4 has gone walk about, It's not a critical upgrade - If you keep an eye on my signature, it should be coming back soon.

/edit - I put it back on manually --> [http://www.vpolink.com/threads/573-Upgrade-ext3-ext4?p=684](http://www.vpolink.com/threads/573-Upgrade-ext3-ext4?p=684)

Regards,

Phill.

---

### Post by AmirM on 2010-01-19
Thanks phillw,but due to my internet data allowance and speed it takes about 6 hours and costs me about 700MBs to download that...
Any ideas?



====
Is there any "thanks" button or something here?

---

### Post by yogesh.girikumar on 2010-01-19
Hi,


       It is usually very difficult to just **upgrade** an installation from the CD since it might lead to package compatibility issues and version conflicts. You can **update** some packages from the CD. But **upgrading** the OS using the CD is not possible. You can do a clean install or you can simply **update** some packages whose new versions are available on the disk. This **DOES NOT **upgrade your system to Karmic. Your system still stays Jaunty. But it gets updated ( not Upgraded )       


[LIST=1]
[*] Boot into your system
[*]Pop in the CD
[*]If you get a prompt, click on "Open Package manager".
[*]Click on "Mark All Updates" and Click "Apply".
[*]Give the password if prompted.
[/LIST]
      

This will install any **updates** that are present in the disk. But it will not **upgrade** your system to Karmic
--
Yogesh Girikumar

---

### Post by AmirM on 2010-01-19
So...the answer is NO.
OK,thanks.

---

