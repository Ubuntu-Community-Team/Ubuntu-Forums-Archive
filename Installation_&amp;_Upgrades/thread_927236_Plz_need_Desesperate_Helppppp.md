---
title: "Plz need Desesperate Helppppp"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by wildwolf on 2008-09-22
Hi im  new in all this UBUNTU stuft, i had windows XP sp2, and i tryied to install ubuntu as a second OS. But i choosed the wroon option when i was doing the partition. i choosed instal ubuntu in the same partition as windows xp, (dump) :( and now i dont have windows xp just ubuntu and the sadest thing is all my documents are gone. i have a 500GB HDD :lolflag: and when i had windows xp i had 350GB of documents!. but i dont care most of them just i care like 3GB of pictures i was working on (im a fhotographer) and i dont understand ubuntu and its commands, i tried to install Photorec, and testdisk but i can't i dont understand how. Please can someone help me!!!!!!

i tried already using photorec in other pc running wind. xp. but seems like it recover alot  of files but corrupted. may be cuz now the hdd got other particion not fat32 or ntfs

sorry my english!:)

---

### Post by redseventyseven on 2008-09-22
Did you back up your documents before installing? I fear that this piece of advice might be a bit late for you, but hopefully this tragic story might serve as a lesson for someone else...

To install programs, I would recommend using the "Synaptic Package Manager" (at least for the time being). I'm no expert on PhotoRec itself, however I just searched for it using Synaptic and it comes up with a package called "TestDisk". If you look at the description then you will see that this package includes PhotoRec.

Once you've installed the package then you should be able to find the program in the Applications menu.

Hope this helps you get started!

---

### Post by wildwolf on 2008-09-22
Im a idiot, i didnt backtem up

---

### Post by wildwolf on 2008-09-22
i instaled them using Synaptic Package Manager as u said they have a green square of instaled, but when i go to application i canot see  them

---

### Post by cariboo on 2008-09-22
To use either testdisk or photorec you are going to need a second hard drive to write the recovered files to. Here is a link to a photorec howt:

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

Jim

---

### Post by wildwolf on 2008-09-24
Thanks ill try the step-by-step tutorial

---

### Post by wildwolf on 2008-09-24
i was reading a similar thread and someone was taking about this [http://trinityhome.org/Home/index.php?wpid=1&front_id=12](http://trinityhome.org/Home/index.php?wpid=1&front_id=12)
sorry i dont know how to make a Hyperlink,
do u think it can helpme recover my windows partition?

---

### Post by wildwolf on 2008-09-25
> **cariboo907 said:**
> To use either testdisk or photorec you are going to need a second hard drive to write the recovered files to. Here is a link to a photorec howt:

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

Jim


When i run the application Root Terminal, and i run Photorec this is what the program said:

root@juancarlos-desktop:/home/juan# sudo photorec
PhotoRec 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)
Please wait...
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63 (RO), sector size=512

PhotoRec need 25 lines to work.
Please enlarge the terminal and restart PhotoRec.
PhotoRec exited normally.
root@juancarlos-desktop:/home/juan# 


and  i dont Know what it means!.

---

### Post by cariboo on 2008-09-25
Grab a corner of the terminal and make it large enough to see 25 lines of text.

Jim

---

### Post by wildwolf on 2008-09-25
thanks ill try 2morrow :)

---

### Post by wildwolf on 2008-09-27
i runed photorec and i got a bunch of folders, but i dont have access to them 
[IMG]http://i264.photobucket.com/albums/ii190/wildwolfjc/Screenshot-2.png[/IMG]

[IMG][IMG]http://i264.photobucket.com/albums/ii190/wildwolfjc/Screenshot.png[/IMG][/IMG]

---

### Post by cariboo on 2008-09-27
Try Alt-F2, then enter:

```
gksu nautilus
```

Enter your password when asked. This will open nautilus as root, you should now be able to navigate to File System-->Home-->Juan, and be able to access your files.

Jim

---

