---
title: "Installing Ubuntu 12.04 beside Win 7 from DVD"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by Mollie25 on 2012-05-15
Hi, 

I'm new to Ubuntu, I downloaded Ubuntu live DVD, tested it and liked it, but when I tried to install it, my instillation is always interrupted for some reason, I don't know it, all a got is a message "please remove instillation media and close the tray (if any) then press Enter " 

I tried to install Ubuntu using Wubi, but the OS is unstable, and i had to download and install many applications, which weren't included with Wubi installation, and got many errors, and finally I got GRUB message 

Now my question is how to install Ubuntu from DVD with all applications installed with this version 

thank you in advance

---

### Post by westie457 on 2012-05-15
> **Mollie25 said:**
> Hi, 

I'm new to Ubuntu, I downloaded Ubuntu live DVD, tested it and liked it, but when I tried to install it, my instillation is always interrupted for some reason, I don't know it, all a got is a message "please remove instillation media and close the tray (if any) then press Enter " 

I tried to install Ubuntu using Wubi, but the OS is unstable, and i had to download and install many applications, which weren't included with Wubi installation, and got many errors, and finally I got GRUB message 

Now my question is how to install Ubuntu from DVD with all applications installed with this version 

thank you in advance

Hi welcome to UF.

The message about removing the installation media means the install has finished and needs to restart the computer. If you reboot with the DVD in the installation procedure will run again.

That message confused me as well a couple of years ago.

---

### Post by Mollie25 on 2012-05-15
> **westie457 said:**
> Hi welcome to UF.

The message about removing the installation media means the install has finished and needs to restart the computer. If you reboot with the DVD in the installation procedure will run again.

That message confused me as well a couple of years ago.

thank you for your reply, unfortunately it's not so in my case, the installation took less than a minute, and when i restart, I there is no Ubuntu OS installed 

forget to say my lap is Asus X42J, core I5, 3G RAM

---

### Post by jadtech on 2012-05-15
did you make enough free space on the hard drive for ubuntu to install ???

keep in mind when windows install it uses the whole hard drive you have to shrink the partition it on  by the amount of space you want to use for ubuntu some where between 30 and 100 gb is good but will install on far less ...

---

### Post by Mollie25 on 2012-05-15
yes, C partition is 97G

---

### Post by darkod on 2012-05-15
C: partition? Ubuntu doesn't install on ntfs partitions, not unless you are trying to install wubi inside windows.

We are not talking how much space the partition has unused, we are talking about having unallocated (unpartitioned) space on the HDD not belonging to any partition. You can't see that in windows in Computer.

You can see all partitions and unallocated space in windows Disk Management.

---

### Post by Enigmapond on 2012-05-15
And are you certain the ISO you downloaded is correct? Did you verify the md5sum? That's what it sounds like..bad data.

---

### Post by Mollie25 on 2012-05-15
> **Enigmapond said:**
> And are you certain the ISO you downloaded is correct? Did you verify the md5sum? That's what it sounds like..bad data.

yes , MD5 sum check are the same

---

### Post by Mollie25 on 2012-05-16
[IMG]http://a4.sphotos.ak.fbcdn.net/hphotos-ak-ash4/318150_10150781941150882_522480881_9958857_312509423_n.jpg[/IMG]
here a photo of my screen, on the right side .......[OK]

---

### Post by gogo_t on 2012-05-16
Edit - I think it would be better to ask my question in a different thread

---

### Post by westie457 on 2012-05-17
@ mollie25

Yesterday when I tried to install using the DVD ISO I ended up with a similar scenario of the installation completing and the message to remove the media and hit enter. I got a wall of text on the screen that just sat there. To get out this I pressed Ctrl+Alt+Del (the keyboard shortcut to log out) then I pressed 'Cancel', everything carried on as it should do. The computer restarted normally and the installation was in place.

Why your attempts are unsuccessful we cannot say for definite without more information. Could you boot from the DVD into 'Try' mode open a terminal (Ctrl+Alt+T) and run this command please ```
sudo fdisk -l
``` The l is a small L not a 1. Post the output back here so we can see which partitions you have on your hard drive.

Thankyou.

---

### Post by Mollie25 on 2012-05-17
> **westie457 said:**
> @ mollie25

then I pressed 'Cancel', 

thank you for your reply, do you mean with cancel to press ESC?

I'll try it right away

---

### Post by Mollie25 on 2012-05-17
here what I got
ubuntu@ubuntu:~$ sudo fdisk -l


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x16d04eb3

   Device    Boot              Start                       End                     Blocks                   Id                        System
/dev/sda1                                 63                    2047                         992+                42                               SFS
/dev/sda2   *             2048        206847                   102400                 42                                SFS
/dev/sda3                     206848         204797951        102295552         42                                SFS
/dev/sda4          204797952    976771119          385986584       42                                SFS
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$

---

### Post by Mollie25 on 2012-05-17
I tried one more time, until I got black screen with 
umount :  /run/lock:not mounted 
unable to connect to system bus: failed to connect to socket    /var/ran/dbus/system_bus_socket:no such file or directory
so I put the DVD again and pressed ESC, now i got the loading Ubuntu screen, but don't know if it's installing the System or not!!

---

### Post by westie457 on 2012-05-17
> Device Boot Start End Blocks Id System
/dev/sda1 63 2047 992+ 42 SFS
/dev/sda2 * 2048 206847 102400 42 SFS
/dev/sda3 206848 204797951 102295552 42 SFS
/dev/sda4 204797952 976771119 385986584 42 SFS

Whoa there. MAJOR PROBLEM. Somehow your hard drive has been converted to 'Dynamic' which is Windows proprietry. Only Windows can work with it however not even Windows can install to the hard drive. It is possible to re-convert it back to a normal drive but is a task filled with danger to your files, ie - you might lose them completely.

Get all of your personal files off that hard drive and put them somewhere safe (dvd, USB drive or external hard drive.

Am now going to find the procedure to re-convert the partitions. worst-case scenario from here is to completely wipe the hard drive and reinstall everything including Windows.

If you have a recovery partition on the hard drive back that up as well. This is very important.

EDIT:

Have found what is probably the best thing to use here.
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

This is a free program and some people have had success using it. There is an on-line help section that covers disk conversion. The whole process is best done with Windows running. Cannot stress enough now how important it is to back things up in case it goes the way of the pear.

---

### Post by Mollie25 on 2012-05-20
thank you so much westie457, I'll convert my hard, and install ubuntu again

---

### Post by Mollie25 on 2012-05-20
thank you westie457 so much I'll convert my Hard to static and install ubuntu again

---

