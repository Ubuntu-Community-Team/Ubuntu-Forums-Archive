---
title: "Grub Error 22"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by acidzfire on 2007-11-14
Ok, so I just did a fresh install of Ubuntu 7.10 dual boot with XP Pro. Everything seemed to go ok during install. When I rebooted after installation was complete, it gave me a Grub Error 22. I have 3 SATA drives with XP on sda, Ubuntu on sdb and sdc is used to store random stuff. I'm back on the live CD now. Is there anything i can do? I thought I was going to look at the menu.lst file under /boot/grub but there is no grub directory under /boot/. i tried to look at a couple of manuals saying to run "sudo grub" in a terminal and make changes but they weren't much help since they were only for single ide drives. Help!

---

### Post by bulldog on 2007-11-14
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

For all the info you need.

Can you post the output of```
sudo fdisk -l
``` small L not a one,to the forum?

Can't wait to long,have to get some sleep.
Some tips.
On which hdd is grub installed?
Try of you can boot windows from the sda by changing the boot order in your BIOS or what ever.
Set the sdb as first bootdevice in the bios.
Then select the boot line in grub, hit the  e key and edit this line,Ithink it should be (hd0,0) hit the  b key to boot.
You can try this,it won't hurt your system because it's not in the menu.lst,you can try different settings as much as you want.

If you post the info here,give me a PM with the link of this topic,and I'll look into it to morrow.
It's not so hard to solve this,your menu.lst isn't in line with your partitions.

---

### Post by acidzfire on 2007-11-14
Here is output from fdisk -l:
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f8004b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c1293

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         365     2931831   82  Linux swap / Solaris
/dev/sdb2             366        5228    39062047+  83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05fb9f8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS
```


I'm no sure what hd grub is installed on since it did not ask nor tell. i just did the guided install and chose the 2nd disk. i'll try the other suggestions and post back the results of it.

---

### Post by acidzfire on 2007-11-14
I changed the boot order of my disk in BIOS. With the windows disk set 1st, I get the Error 22. With either of the other disks set as boot drive, it shows a black screen with 
```

GRUB  _
```

the _ representing a blinking cursor.

---

### Post by meierfra on 2007-11-14
1) Try changing your boot order again  It does not only matter what drive is first, but also which one is second. 
Put sda first, sdb second and sdc last.  If that did not work try different orders.

2) To get to the menu.lst you need to mount your ubuntu partition first:

```

mkdir ubuntu
sudo mount -t ext3 /dev/sdb2 ubuntu 
```

To open the file

```
gksudo gedit  ubuntu/boot/grub/menu.lst
```

Post the file here.


3) To reinstall grub


sudo grub

find /boot/grub/menu.lst

The output will be (hdx,y)   (probably  (hd1,1))

root (hdx,y)
setup (hd0)
quit

---

### Post by acidzfire on 2007-11-14
I tried every combination, but no matter how i do it i get either the error 22 or just the word grub. Thanks for the hint on menu.lst. Here is the contents of it...i am removing most of it, as everything before this was commented out. If that is needed too, let me know:

```

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7bd5a968-f184-461b-bbf5-c96a07555c07 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7bd5a968-f184-461b-bbf5-c96a07555c07 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by acidzfire on 2007-11-14
```

grub> find /boot/grub/menu.lst
 (hd1,1)

grub> root (hd1,1)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+17 p (hd1,1)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

```

---

### Post by acidzfire on 2007-11-14
is it possible that it did not write the changes to the windows MBR and installed to the wrong partition or something? and would trying to run super grub help? i've heard ppl talk about it, mabe i should try using it

---

### Post by meierfra on 2007-11-14
```
is it possible that it did not write the changes to the windows MBR and installed to the wrong partition or something? a
```

Maybe, but I don´t really see a reason for it.

Super Grub is always a good idea. See[ Hermanzone]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") for information

You might also try [mbwardle howto]("http://ubuntuforums.org/showthread.php?t=442945#9") (although since you only have sata drives, this should not be the issue.)

Finally bulldog link contains a few more suggestions to try.

---

### Post by meierfra on 2007-11-14
Also now that you reinstalled grub, you might try different boot order again. (  sda first, sdb second or sdc first, sdb second are the  mostly likely ones to succeed.

---

### Post by meierfra on 2007-11-14
Here is a suggestion which might actually work:

sudo grub
root (hd1,1)
setup (hd1)
quit

Then boot with the Ubuntu drive (sdb) first in the boot order.

This  should get you to the grub menu (You will get an error message after you selected ubuntu from the grub menu,  This can easily fixed by editing ¨menu.lst", but no reason to edit menu.lst, before we know whether  you actually get to the grub menu.)

There are other things one can try: unplugging drives, adjusting cables ... But bulldog knows much more about that than I do. So I let him deal with that, then he comes back.

---

### Post by acidzfire on 2007-11-15
ok. i'll try that. thanks for the help!

---

### Post by bulldog on 2007-11-15
First boot sda,if you see the grub menu with your boot partitons,boot the windows option and see if that will boot windows.
If yes,grub is on the windows hdd.

If windows won't boot with an error,grub will probably installed on the ubuntu hdd,sdb.
This is more likely,because all Sata devices are master.
In that case,make the sdb first boot device in the BIOS,and see if grub comes on screen.
If so,select the ubuntu boot line, and hit the  e  [edit] key.
Change whatever there is listed in (hd0,1) enter and hit the  b  [boot] key.
Lets see if ubuntu will boot.

If yes change the menu.lst while you are logged in ubuntu .
```
gksu gedit /boot/grub/menu.lst
```
Change all three lines from (hd1,1) into (hd0,1) 
To make windows boot from grub you have to edit the entry too
Make it look like this ```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

Save the file and you're done.
If this is not the solution,post back please.
I have three Sata hdd's as well,booting windows and ubuntu on separate hdd's
Your ubuntu hdd must be set to boot from,and grub should be on that hdd installed.

I notice you have not created a separate /home partition.
This is not a problem,till you want to reinstall,then you have to backup all your data.
And in your case,with enough hdd space,I would discuss another matter.
If you want to upgrade to a new ubuntu,and you will,it's better to make some space available now you have the chance.
If you do, you can do a clean install on a new partition with the same /home and swap.
You have your 'old' working ubuntu,you can try out the new ubuntu and you'll have always a working ubuntu,in case the new one is buggy.
The only thing to remeber is:**choose a new login name for the new install** otherwise it will mess with the 'old' one.
Now there will be a new folder created in your /home for the new ubuntu,you can copy your files [firefox preferences,mail andwhat ever you want] into the new ubuntu.
You see,you can do things different ways,I use linux for some years now,and I have learned to be carefull with my data,so I will not upgrade anymore,just a clean install.
And if the new ubuntu is perfect,you can wait for the next ubuntu and install it in the first 'old' ubuntu and so on,this will cost only 10GB of your hdd space.
It's worth it.
Think about it and let me know.

---

### Post by girto on 2007-11-15
You can use the geometry GRUB command in order to identify what hdx represents:

sudo grub
geometry (hd0)     # or (hdx,y) where x= is the hard disk (0=1st hard disk)
                              #                              y is the partition number (0=1st partition)
 
The above command will show you the drive size and its partitions IIRC. That would help you identify the name of the drive/partition you wish to install GRUB to.

then:

root (hdx,y)           # x and y defined as above
setup (hdx)
quit

---

### Post by acidzfire on 2007-11-15
ok, i got it to where it will get to the grub screen now. when i choose windows, it says:
```

Error 13: Invalid or unsupported executable format

Press any key to continue..._
```
Ubuntu gave me another code 17 cannot mount this partition.

so I changed this:
```
(hd 1,1)
```
to 
```
(hd 0,1)
```
and am now able to boot into Ubuntu.. i'll try to edit menu.lst to see about getting windows up

---

### Post by acidzfire on 2007-11-15
Thanks Bulldog! I finally got it! After working with it i finally got a NTLDR missing error when choosing windows, so i knew i was closer. Since my 3rd hard drive is an NTFS drive and not an OS, i assumed it was looking at that drive. So i changed my boot order once again and swapped the 2nd and 3rd disk around in the order and got another bad partition error. so i edited it to have windows set to 
```
(hd 1,0)
```and it finally worked. That and changing the menu.lst. I changed the xp portion to look like the one you posted. Everything is good now. ...about the /home. I initially set up a seperate partition for it but it kept messing up during the install. That's why there is still so much free drive space. I had never thought about doing the installs like you mentioned for new versions. I'll try that next time I "upgrade"...Well...Thanks again. Now it's time for me to try and install the newest NVIDIA drivers

---

### Post by meierfra on 2007-11-15
Just out of curiosity: What did you do to get the "grub menu" to appear?

---

### Post by acidzfire on 2007-11-15
i'm not sure lol...
at first i used super grub and did something that caused it to stop bringing up the grub error and instead just booted windows. so i booted back with super grub again and was playinig around changing the      
```

(hd x,x)
```
and changing the boot order as you had suggested...eventually i got the grub menu. then it was just a matter of getting the second drive set as the windows one. since i have 3 identical drives, they all show the same in bios, so it was trial and error. without yours and bulldogs guidance, I'd prolly still be lost. :)

thanks again.

---

