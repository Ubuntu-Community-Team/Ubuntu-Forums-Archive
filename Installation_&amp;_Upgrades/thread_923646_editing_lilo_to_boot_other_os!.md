---
title: "editing lilo to boot other os!"
date: 2008-09-18
forum: Installation &amp; Upgrades
---

### Post by yoma819 on 2008-09-18
ok i am trying to boot another os
i cant use the more conventional methods like thumb drive or cd drive as i am using a tablet that cannot boot off either
it only supports really expensive brands of cd drive and thumb drive so thats a no go
i got ubuntu to install by using the windows installer and then it recognised the usb thumb drive
i am thinking that i could create a small partition, put the linux distro i want to boot in it and add a line onto lilo to boot the new partition.
my only problem is that i have no idea how to do any of this
i have never partitoned a drive in linux and i have never editied the lilo config file
can anyone help?
many thanks
--yoma

---

### Post by yoma819 on 2008-09-18
bump

---

### Post by yoma819 on 2008-09-19
bump

---

### Post by Partyboi2 on 2008-09-19
maybe you could use [[COLOR=Blue]unetbootin[/COLOR]]("http://unetbootin.sourceforge.net/"), it supports all different types of linux distro's. Or maybe [[COLOR=Blue]this[/COLOR]]("https://help.ubuntu.com/community/Installation/FromLinux") will interest you.

---

### Post by yoma819 on 2008-09-19
thank you 
thank you
thank you


this is exactly what i was looking for
many thanks 
--yoma

---

### Post by yoma819 on 2008-09-19
right 
ok i have a slight problem in that i have only 2 partitions on my disk
my root and my swap
i cant obviously use gparted to partiton my root partiton while it is mounted!
how do i get around this?
is there anyway to resise it without having to boot from an extenal device!
thanks
--yoma

---

### Post by yoma819 on 2008-09-19
also i am thinking of changing the line:

root            (hd0,0)

so it is targeted at the usb flash drive
the only thing is i dont know what to replace it with or how to find out by myself what the flash drive would be called
--yoma

---

### Post by Partyboi2 on 2008-09-19
I am not sure what other operating system you are wanting to install but check and see if its on the unetbootin  list, on the main unetbootin screen select "Distribution" and "version" and check if its there select it then down the bottom change "type" from usb to hard disk.
Or maybe try selecting "Parted magic" from the list and see if you are able to partition using that tool as I think it should run much like a live cd and allow you to unmount the partitions to work on them. I have never actually used parted magic with unetbootin.

Another longer way could be to use unetbootin to install dsl (darn small linux) and then after you have installed it use the partitioning tool that dsl uses to make the partitions you are wanting. Then after you have installed the os you want you can delete dsl.

---

### Post by yoma819 on 2008-09-21
i have tried using the partition manager in backtrack
but it wont work because no matter what i do the os is being booted off the hard drive so i cant partition it!
is there any way i can get grub to boot off a usb stick
i saw when adding lines to grub you define the hard drive 
hd0,0
how would i find out what the thumb drive is called
i am just shooting in the dark
i have tried hd0,1 etc
thanks
--yoma
p.s. i tried parted magic and it woukld not boot 
came back with an error
--yoma

---

### Post by Partyboi2 on 2008-09-22
You should be able to run gparted from a usb.
[http://gparted.sourceforge.net/liveusb.php](http://gparted.sourceforge.net/liveusb.php)

---

### Post by yoma819 on 2008-09-22
i can't
my bios will onyl recognise cirtain very specific usb decvices that are very expensive
i now have a usb cdrom drive
as mentioned above is there any way i can use grub to direct the boot to this device?
or any other?
--yoma

---

