---
title: "Server Edition of Dapper is not included"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by textguru on 2006-09-20
I have requested a CD of 6.06. Is it really excluded a copy of the server edition on Dapper?

---

### Post by Qrk on 2006-09-20
Shipit ships you a desktop cd, not a server one. However, you can download the server iso free of charge from the Ubuntu website. 

Also, you can install the packages you need for your server after installing your desktop version, which many people prefer, because then you have a GUI for setting up your server. You can always disable X later.

---

### Post by textguru on 2006-09-22
> **Qrk said:**
> Shipit ships you a desktop cd, not a server one. However, you can download the server iso free of charge from the Ubuntu website. 

Also, you can install the packages you need for your server after installing your desktop version, which many people prefer, because then you have a GUI for setting up your server. You can always disable X later.

Thanks for the reply. Can you teach me how to install Apache, PHP and MySQL from Dapper desktop CD? I've already installed the base system. Now, how can I install these services? Also, after installing these services, how do I disable X so I may save memory?

---

### Post by imnotrich on 2006-10-17
The server download for Dapper is corrupt...I have tried downloading and burning both the regular and alternate download. 
Using different cd burners, it fails on the same packages saying they are "corrupt." 
It also does not identify my network card and is having problems identifying my cd roms, though that might be a jumper issue - still experimenting there. All I want is a cli-based server on an old pc with limited ram and horsepower, also tried to install ubuntu proper and it hung at "mounting root partition" 
Anyone know where I can find a patched copy of the server iso?

---

### Post by justin whitaker on 2006-10-17
> **imnotrich said:**
> The server download for Dapper is corrupt...I have tried downloading and burning both the regular and alternate download. 
Using different cd burners, it fails on the same packages saying they are "corrupt." 
It also does not identify my network card and is having problems identifying my cd roms, though that might be a jumper issue - still experimenting there. All I want is a cli-based server on an old pc with limited ram and horsepower, also tried to install ubuntu proper and it hung at "mounting root partition" 
Anyone know where I can find a patched copy of the server iso?

You can also install a command line system from the Alternate Install CD.

---

### Post by az on 2006-10-17
> **textguru said:**
> Thanks for the reply. Can you teach me how to install Apache, PHP and MySQL from Dapper desktop CD? I've already installed the base system. Now, how can I install these services? Also, after installing these services, how do I disable X so I may save memory?

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

To not run X when you boot, remove the gdm package.

sudo apt-get remove gdm

---

### Post by benblout on 2006-10-17
> **imnotrich said:**
> The server download for Dapper is corrupt...I have tried downloading and burning both the regular and alternate download. 
Using different cd burners, it fails on the same packages saying they are "corrupt." 
It also does not identify my network card and is having problems identifying my cd roms, though that might be a jumper issue - still experimenting there. All I want is a cli-based server on an old pc with limited ram and horsepower, also tried to install ubuntu proper and it hung at "mounting root partition" 
Anyone know where I can find a patched copy of the server iso?

You seem to be mixing several issues here - If you are having trouble with the downloads not buring properly, how can you know do the install?  And if you are not doing an install, how do you know ubuntu is having trouble with your network card?

On a separate note, I wrote this in another thread, it may apply to your problem with "mounting root partition":

> Ok, I may have a hint for you.

I have been preparing to upgrade to Breezy, and reading about the problems I may encounter. It sounds like you may have one of the common ones. Take a peak at these links and see if it applies to your situation.

[Here]("http://www.ubuntuforums.org/showthread.php?t=208207")
[and here.]("http://ubuntuforums.org/showthread.php?p=1257154")

I am not saying this is your problem - I don't know enough about this bug to fully understand all the ways it appears. So take a look at the links and decide for yourself, or wait until someone more experienced comes along!


-Ben

---

### Post by imnotrich on 2006-10-25
Thanks for all the helpful suggestions...

In the interim, I exchanged the nic with a different one and purchased the official ubuntu book. I was able to use the dvd that came with the book to succesfully install dapper server. 

This is a dual boot system with an ata66 controller card. In the process I thrashed the mbr/grub listing, but that was an easy fix. Now all I have to do is get the zip drive working in Dapper, but I think that is a mobo/bios/conflict with pci ide controller card issue. 

Rich

---

