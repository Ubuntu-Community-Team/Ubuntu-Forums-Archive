---
title: "GRUB error"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by jay0613 on 2009-11-21
Hey,
I'm sorry I'm prob getting annoying. I installed ubuntu 9.10 as a dual boot on windows xp. Well I was in ubuntu and I was having audio problems so I followed what someone else said and restarted, well now I am getting a GRUB loading error: no such disk. Now what do I do? I just want to get back to xp

---

### Post by jay0613 on 2009-11-21
bump......

---

### Post by jay0613 on 2009-11-21
This is pretty important I really need to get back to XP. The only thing I can do is run Ubuntu on a test drive off of the disc. If I don't have the disc in I get the GRUB error. So how can I get back to XP? Sorry for being impatient/annoying.

---

### Post by darkod on 2009-11-21
Try to restore grub2 from here:
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

Look at number 2) Using Ubuntu 9.10 LiveCD

---

### Post by emigrant on 2009-11-21
hi, plz go through this thread,similar issue:
[http://ubuntuforums.org/showthread.php?t=1333129](http://ubuntuforums.org/showthread.php?t=1333129)

---

### Post by jay0613 on 2009-11-21
> **emigrant said:**
> hi, plz go through this thread,similar issue:
[http://ubuntuforums.org/showthread.php?t=1333129](http://ubuntuforums.org/showthread.php?t=1333129)

Yea I read through that and I still haven't had any luck. I don't have the XP install disc or recovery disc. So now what do I do?

---

### Post by ssican on 2009-11-21
Maybe, this will help:

On this webpage:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

See item: 
 6 - Boot Display Behavior
  6.1 - Initial Default
  6.2 - Timed Display
  6.3 - Hidden

EDIT:
Another solution it is to use SUPERGRUB DISK, see:

1)- [http://www.supergrubdisk.org/w/index.php5?title=UninstallGRUB](http://www.supergrubdisk.org/w/index.php5?title=UninstallGRUB)

2)- [http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

---

### Post by phillw on 2009-11-21
> **jay0613 said:**
> Yea I read through that and I still haven't had any luck. I don't have the XP install disc or recovery disc. So now what do I do?

there is one available for xphome available on-line. The download speed is not too fast, but it does work.

			 			 		   		 		 		If you have XP Home I found a disc image for you here:
[http://www.thecomputerparamedic.com/files/](http://www.thecomputerparamedic.com/files/)

Look for WXPHOME_EN.iso it's close to the top. Download it and burn it on CD. Since you have license purchased with the computer you are in titled to use downloaded images, they didn't give you a windows CD with the computer.


thanks to darkod for digging that one out - I know it works because I've just helped s.o. with it.

Phill.

---

### Post by jay0613 on 2009-11-21
> **ssican said:**
> Maybe, this will help:

On this webpage:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

See item: 
 6 - Boot Display Behavior
  6.1 - Initial Default
  6.2 - Timed Display
  6.3 - Hidden

EDIT:
Another solution it is to use SUPERGRUB DISK, see:

1)- [http://www.supergrubdisk.org/w/index.php5?title=UninstallGRUB](http://www.supergrubdisk.org/w/index.php5?title=UninstallGRUB)

2)- [http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

I opened the terminal and typed in "grub-install -v" and it said I have grub 1.97~beta4. So I have it installed but when it tries to load the grub menu it says "GRUB loading error: no such disk." I don't know what to do and I don't want to loose my stuff in XP. I just getting very frustrated. I don't know if I have anymore blank CDs to burn the Super Grub to. 

I restarted my computer and tried holding shift and then I got an error that said my keyboard wasn't plugged in or something, which obviously doesn't make sense. 

> there is one available for xphome available on-line. The download speed is not too fast, but it does work.

			 			 		   		 		 		If you have XP Home I found a disc image for you here:
[http://www.thecomputerparamedic.com/files/](http://www.thecomputerparamedic.com/files/)

Look for WXPHOME_EN.iso it's close to the top. Download it and burn it on CD. Since you have license purchased with the computer you are in titled to use downloaded images, they didn't give you a windows CD with the computer.


thanks to darkod for digging that one out - I know it works because I've just helped s.o. with it.

Phill. 	

Would that erase everything? Because I really don't want to lose everything.

---

### Post by drs305 on 2009-11-21
The time to start holding down the SHIFT key, if necessary, is just after you hear the computer POST, or hear the system beep. In your current state, are you left with a grub or grub-rescue *prompt*?

If so, just take your time and follow the instructions for booting from the grub command line. Nothing will be erased. The instructions are on the page I think you have already seen:
[https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot")

If you find you can't get into Ubuntu, you can either reinstall it on the partition it was previously installed on and your Windows partition and data won't be touched.

---

### Post by jay0613 on 2009-11-21
It says 

GRUB loading:
error: no such disk
grub rescue>

I guess it's the grub rescue.

---

### Post by drs305 on 2009-11-21
> **jay0613 said:**
> It says 

GRUB loading:
error: no such disk
grub rescue>

I guess it's the grub rescue.

Yes, it's the rescue mode - that means that G2 can't find a usable grub.cfg file. Follow the instructions on booting from the command line. See if G2 can find the system using the commands listed in the community documentation.

If you can get into the system, run "sudo update-grub" and we can make sure you will be able to boot normally the next time.

---

### Post by jay0613 on 2009-11-22
So I followed what it said on that site. I typed in "set" and this is what I got:

prefix=(UUID=6a880397-27fe-4b27-aa63-94f715a244da)/boot/grub
root=UUID=6a880397-27fe-4b27-aa63-94f715a244da

Then I typed "ls" and I got 

(hd0) (hd0,1) (hd1) (hd1,1) (hd2) (hd2,1) (hd3) (hd3,1) (fd0)

Then on that link it says to do other stuff after ^ but I don't understand it. So after I type "set" and "ls" then what do I do?

---

### Post by drs305 on 2009-11-22
> **jay0613 said:**
> So I followed what it said on that site. I typed in "set" and this is what I got:

prefix=(UUID=6a880397-27fe-4b27-aa63-94f715a244da)/boot/grub
root=UUID=6a880397-27fe-4b27-aa63-94f715a244da

Then I typed "ls" and I got 

(hd0) (hd0,1) (hd1) (hd1,1) (hd2) (hd2,1) (hd3) (hd3,1) (fd0)

Then on that link it says to do other stuff after ^ but I don't understand it. So after I type "set" and "ls" then what do I do?

The 'set' command shows you the current settings. The 'ls' command shows you the devices (hd0, hd1, hd2, hd3) and partitions.

Next you have to determine which device and partition your linux is installed in. If it *is* installed, it is going to be on either sda1, sdb1, sdc1 or sdd1. If you don't know, you could type on the Grub command line, for example to check sda1:
ls (hd0,1)/boot/
If that is where linux is, you should see some initrd and vmlinuz files. If you don't see them, try the same commands with (hd1,1) or (hd2,1), etc. Once you know which device/partition your Linux install is on, you run the rest of the commands.

If you decide it is sda1, you would run the following commands from the Grub 2 command line:
set root=(hd0,1)
and continue with the instructions. 

I can't really talk you through the procedure via a thread. If you need step by step help the best thing would be to log onto one of the Ubuntu IRC help channels where you can get live support (if you have access to a second computer). 

If you don't know how to use IRC, refer to this post:
[https://help.ubuntu.com/community/InternetRelayChat]("https://help.ubuntu.com/community/InternetRelayChat")

---

### Post by jay0613 on 2009-11-22
I ran the boot info script and my ubuntu is on sdb5. So then would I put set root(hd2)?

---

### Post by jay0613 on 2009-11-22
Alright I just ran all of them and I got "error unknown filesystem" for pretty much all of them. Except when I did ls (fd0)/boot/ I got the error "biosdisk read error" So now what?

---

### Post by drs305 on 2009-11-22
> **jay0613 said:**
> I ran the boot info script and my ubuntu is on sdb5. So then would I put set root(hd2)?

Grub 2 starts counting the drives at 0, and the partitions at 1. So sdb5 would be the second drive (1) and 5th partition (5). So for Grub 2, that would translate to (hd1,5).

According to the "ls" command in Grub, it didn't see a sdb5, only sdb1, But you can try it and see. 

At the Grub 2 prompt, try this to see if G2 detects any files in the boot folder of sdb5:
```
ls (hd1,5)/boot
```

Do you see any of the normal boot files, such as an initrd or 
vmlinuz.... files? If it doesn't see any, try (hd0,1), (hd1,1), (hd2,1), and (hd3,1). 

You can also try running the LiveCD and running GParted (System, Admin, Gparted) to see what kind of partitions you have and how much data is contained in them.

If you can't boot from the G2 prompt, you can try reinstalling it from the LiveCD. There are instructions on the GRUB 2 page. 

As you can see, you can spend a lot more time trying to fix an installation rather than just reinstalling it again. A new installation would probably take less than an hour unless you have a slow internet connection or have other issues. Before doing that you would want to mount whatever partitions you can find with Gparted and copy your data files to another partition.

---

### Post by jay0613 on 2009-11-22
In GParted it has /dev/sdb/ then it shows /dev/sdb1. Then it also has /dev/sdb2 and under that is shows /dev/sdb5 and /dev/sdb6. 

If I reinstall, then would it make it so I have 3 partitions? One for XP and one for this ubuntu I'm having trouble with, then another one for the new ubuntu?

---

