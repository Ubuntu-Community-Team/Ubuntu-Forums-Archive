---
title: "Cant find grub/menu.lst ??"
date: 2008-03-28
forum: Installation &amp; Upgrades
---

### Post by redgilda on 2008-03-28
Is that even possible? :)

I have many partitions. 3 Hard drives (1 SATA).
I had Windows XP installed on the Sata

Here's the fdisk output:
```

ubuntu@ubuntu:/$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2b342b33

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2165    17390331    7  HPFS/NTFS
/dev/sda2            2166       19457   138897990    f  W95 Ext'd (LBA)
/dev/sda5            2166       16755   117194143+   7  HPFS/NTFS
/dev/sda6           16756       19308    20506941   83  Linux
/dev/sda7           19309       19457     1196811   82  Linux swap / Solaris

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4cfb066e

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19929   160079661    7  HPFS/NTFS

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xebfbd117

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2499    20073186    c  W95 FAT32 (LBA)
/dev/hdb2            2500        4997    20065185    f  W95 Ext'd (LBA)
/dev/hdb5            2500        4997    20065153+   b  W95 FAT32
ubuntu@ubuntu:/$ 
```

Windows booted fine at first. Then I tried re-installing Grub for it to show up as it loaded with the 'Grub Error 12' when I changed booting drives..

When I tried to follow this:

```
grub> root (<tab>  #grub will complete the line or list your partitions

#If you do not know your boot partition, use the find command instead 

grub> find /boot/grub/stage1

grub> root (hd0,1) #Hit the <Enter> key

grub> setup (hd0) #Hit <Enter> key

grub> quit #Hit <Enter> key, quits grub
```

doing all that didnt really work - my root showed in (hd2,5)

so now I cant load anything.. I wanted to edit my menu.lst but its nowhere to be found? is that possible?

Anyway - my questions is - when looking at my fdisk list - can anyone tell me to which partition should I re-install grub?

At one Grub did load and it showed up with Ubuntu - then I got the error 12 partition does not exist or sth...

gedit /boot/grub/menu.lst - results in a blank file... ?

Any help or feedback appreciated... 

I decided to give it a go to Ubuntu AGAIN after a verrrry long time but I feel like I forgot even all the terminal commands again :(

---

### Post by Pumalite on 2008-03-28
You should reinstall Grub to sda (hd0,0)
Your menu.lst should be in:
sda6/boot/grub/menu.lst

---

### Post by redgilda on 2008-03-28
Thanks for your answer.

hmmm I did search in all the drives before and still couldnt find the menu.lst file. I even did a file search for the whole file-system

and what if now grub doesnt want to re-install  :/

```
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub> 
```

I still try to follow this:

```
grub> find /boot/grub/stage1

grub> root **(hd0,1)** #Hit the <Enter> key

grub> setup **(hd0)** #Hit <Enter> key

grub> quit #Hit <Enter> key, quits grub
```

only now I'm not sure what I should put into the bolded places above?

*still lost*

---

### Post by Pumalite on 2008-03-28
Try to boot your Ubuntu with Super Grub; if your kernel ia alive; it'll boot it:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by redgilda on 2008-03-28
Hi, yeah that was supposed to be my next step in fact :) Only I cant find a blank CD ;-) But I guess you cant help me with that ;-)

---

### Post by buntu_Geek on 2008-03-28
Did you try those grub commands... "grub>"..in your live cd ... or ??

you shud use your live cd to re-install grub...

---

### Post by redgilda on 2008-03-28
> **buntu_Geek said:**
> Did you try those grub commands... "grub>"..in your live cd ... or ??

you shud use your live cd to re-install grub...
yes I was using the Live CD with these commands... but thats the result I got - above ... :(

---

### Post by redgilda on 2008-03-28
> **Pumalite said:**
> You should reinstall Grub to sda (hd0,0)
Your menu.lst should be in:
sda6/boot/grub/menu.lst
and when I try to install to hd0,0 I get this error now (still trying from the LIVE CD) only though.. still havent tried Super Grub

```
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1

find /boot/grub/stage1
 (hd2,5)
grub> 
grub> root (hd0,0)
root (hd0,0)
grub> setup (hd0,0)  
setup (hd0,0)

Error 17: Cannot mount selected partition
grub> setup (hd0)
setup (hd0)

Error 17: Cannot mount selected partition
grub> 
```

---

### Post by redgilda on 2008-03-28
UPDATE

I still don't get it. I used the Super Grub to 'fix' the grub.. so then it does load - it shows Linux (the usual 3 options) and Windows - but Linux doesnt load - Error 22, No Such Partition

so it would mean that I do have Grub right?

but when I try to edit menu.lst

gedit /boot/grub/menu.lst

i get an empty file... :(

I have the Grub menu so it should be relatively easy to just modify the menu.lst file to get rid of the 'error 22' - but where is my correct menu.lst then? :( *very confused*

-------
EDIT

I mounted ubuntu separately and then I was able to cd /boot/grub and to edit the menu.lst !

could someone tell me what I should put in there?

title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		**(hd1,5)**
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=9ce07c6d-d4c6-42b3-9279-9139177f4b13 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

---

### Post by confused57 on 2008-03-28
What you could try is highlight your Ubuntu entry in your grub boot menu, press "e", then highlight the line with root, press "e" again, try changing it to (hd1,5) or (hd0,5), press "enter", then "b" to boot.  This is assuming (hd2,5) doesn't boot Ubuntu.  This change is temporary if either works, but easy to make permanent in your menu.lst.

---

### Post by redgilda on 2008-03-28
ok thanks, I'll try that now..

but judging by the fdisk output - if Linux is on sda6 - then the linux partition in grub should be..... (hd2,5) normally? I'm trying to find the Grub logic somewhere but I cant...

---------
FINAL EDIT - I changed the line to (hd1,5) and it seems to be working. YAY

Thanks to everyone who tried to help ;-)

---

### Post by confused57 on 2008-03-28
> **redgilda said:**
> ok thanks, I'll try that now..

but judging by the fdisk output - if Linux is on sda6 - then the linux partition in grub should be..... (hd2,5) normally? I'm trying to find the Grub logic somewhere but I cant...

---------
FINAL EDIT - I changed the line to (hd1,5) and it seems to be working. YAY

Thanks to everyone who tried to help ;-)
Great, I thought one of them would work.  You'll also need to change the line with groot to (hd1,5):
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)
be sure to leave the # in front of groot.

---

