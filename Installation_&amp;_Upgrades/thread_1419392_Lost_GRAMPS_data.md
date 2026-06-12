---
title: "Lost GRAMPS data"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by asharpham on 2010-03-01
My Ubuntu USB drive has stopped loading so I no longer have access to Ubuntu programs. I don't mind reinstalling Ubuntu but I'd like to try and recover my GRAMPS data first.

I can run Ubuntu from the installation CD and I can see the whole file system on the USB drive, but I have no idea where to start looking for my GRAMPS data or what the files are called. Can someone help me with this?

And please, no lectures about backing up data. You'd think I'd know to do that by now!!

Alan.

---

### Post by Old_Grey_Wolf on 2010-03-01
I do not have mine on a USB; however, on my HDD it stores the database in /home/username/.gramps/grampsdb. Maybe you have a hidden folder ".gramps" on your USB.

---

### Post by asharpham on 2010-03-02
That wass a good answer and should have enabled me to find the files in question. However, after enabling viewing of hidden files, GRAMPS was still not found in that folder.

I guess if I could find what files are missing that stops Ubuntu booting up, I may be able to solve the problem that way. But I have absolutely no idea what I'd be looking for.

---

### Post by elite0083 on 2010-03-02
if you create a live cd and then run it and plug the usb in you should be able to recognize it and pull up the files if it is saved to the usb or if its somewhere else you should be able to pull it up under places.

---

### Post by asharpham on 2010-03-02
Yes I can see the file structure on the USB drive but I don't know what I'm looking for. I can't find GRAMPS files anywhere.

---

### Post by DrMelon on 2010-03-02
Try using "locate gramps" in the terminal.
Do "sudo update-db" or something similar to update the search index.

---

### Post by asharpham on 2010-03-02
"sudo update-db" came up with an error. "Locate gramps" found 2 mentions but they're in the folders on my installation CD (weird). Gramps was installed on the USB drive that is now somehow corrupted but, while I can still see the structure and files on the drive, there is no mention of Gramps.

I can still see the "/home/(username)/" folders on the drive but they don't contain the "Documents..." etc folders that should be there.

---

### Post by asharpham on 2010-03-02
How do I access the USB drive in Terminal? Because I'm using the installation CD to "browse" Ubuntu, I can't seem to get to the /home/ etc files on the USB drive in Terminal. It will only "locate" stuff on the CD.

---

### Post by elite0083 on 2010-03-02
so why is it that you just can't pop in the live cd and then tell it to try ubuntu without installing and then go to places and look in the usb?

---

### Post by Dr Droid on 2010-03-02
He says that he can see the fs. 

If you were booting ubuntu from your usb in the past i would double check bios first of all to make sure that it is still set to boot from usb and also I would check that the /boot folder on the usb is located in the root partition...  In order to get to the files in the CLI you need to find out where the usb drive is mounted, if it has been mounted. Nautilus will tell you that when you click on the thumb drive in places and press ctrl+l which should bring up thte location you are in. Then in the terminal use cd to get there. EG: 

```
cd /media/usb/

```

Then do a dir and you should see the whole tree... I might be able to help you however, if you explain to me what this system you are using is like. Does it have windows installed as its main OS on the hard drive? If so which version... Also is your MBR booting off of grub or boot.ini (Windows bootloader)

---

### Post by asharpham on 2010-03-02
Ok thanks so much for that. I followed your suggestion and then did a "ls -l" and this is the result:
ubuntu@ubuntu:~$ cd /media/0749af0b-b54b-4120-85ae-263635edff6a
ubuntu@ubuntu:/media/0749af0b-b54b-4120-85ae-263635edff6a$ ls -l
ls: cannot access media: Input/output error
total 100
drwxr-xr-x   2 root  root    4096 2010-02-05 00:50 bin
drwxr-xr-x   3 root  root    4096 2010-02-07 04:18 boot
lrwxrwxrwx   1 root  root      11 2010-01-31 15:57 cdrom -> media/cdrom
drwxr-xr-x   4 root  root    4096 2010-01-31 16:19 dev
drwxr-xr-x 148 root  root   12288 2010-02-28 12:08 etc
drwxr-xr-x   3 root  root    4096 2010-01-31 16:19 home
lrwxrwxrwx   1 root  root      33 2010-01-31 16:20 initrd.img -> boot/initrd.img-2.6.31-14-generic
drwxr-xr-x  18 root  root   12288 2010-02-27 04:43 lib
drwx------   2 root  root   16384 2010-01-31 15:55 lost+found
d?????????   ? ?     ?          ?                ? media
drwxr-xr-x   2 root  root    4096 2009-10-20 00:04 mnt
drwxr-xr-x   4 10490 floppy  4096 2010-02-27 04:43 opt
drwxr-xr-x   2 root  root    4096 2009-10-20 00:04 proc
drwx------  14 root  root    4096 2010-02-21 04:00 root
drwxr-xr-x   2 root  root    4096 2010-02-07 04:18 sbin
drwxr-xr-x   2 root  root    4096 2009-10-19 23:05 selinux
drwxr-xr-x   3 root  root    4096 2010-02-18 07:35 srv
drwxr-xr-x   2 root  root    4096 2009-10-19 15:18 sys
drwxrwxrwt  11 root  root    4096 2010-02-28 12:08 tmp
drwxr-xr-x  11 root  root    4096 2010-02-02 05:23 usr
drwxr-xr-x  15 root  root    4096 2009-10-28 21:02 var
lrwxrwxrwx   1 root  root      30 2010-01-31 16:20 vmlinuz -> boot/vmlinuz-2.6.31-14-generic
ubuntu@ubuntu:/media/0749af0b-b54b-4120-85ae-263635edff6a$
 
One thing that bothers me is that I can't find any folders in /home/alan/ on ther USB drive where Documents etc should be.There is an error mentioned above but I have no idea what it means and what is missing/corrupted. I can't find any mention of the GRAMPS files I'm desperately after. Nor my documents. If I could retrieve my data off this stick I'd be happy but I'm starting to realise it's gone forever.

It was booting up in Grub and then I had the choice of Ubuntu or Windows. Now I don't get the gateway that gives me those options. So I can't run Windows and can only access Ubuntu from the installation CD.

Alan.

---

### Post by asharpham on 2010-03-03
Good news! I've got my Grub boot working again. However, it will only boot up in Windows (still using Grub) but not Ubuntu. I've had some help from the Absolute Beginner forum to get this far with the boot problem.

Now getting back to the GRAMPS problem - I have some good news here too. I discovered what appears to be a full backup (a .ful file plus several .inc files) on my Windows drive. Having a look inside the file, there are GRAMPS folders and files so I'd say I may be out of the woods.

Still, I'll wait to see what comes out of the Absolute Beginner forum and then get back here to advise whether it worked or not.

Much obliged for all the help so far.

Alan.

---

### Post by asharpham on 2010-03-03
I've got it all back. Thanks to all who helped.

---

