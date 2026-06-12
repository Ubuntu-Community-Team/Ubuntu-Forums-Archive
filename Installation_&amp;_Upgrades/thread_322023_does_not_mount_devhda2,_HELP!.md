---
title: "does not mount /dev/hda2, HELP!"
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by Wall86 on 2006-12-19
ok, it seems that ubuntu currently is not mounting my / partition hard drive layout:

1st partition is a 250 MB /boot (/dev/hda1)
2nd partition is a 20GB / (/dev/hda2)
3rd partition is about 160GB /home (/dev/hda3)
4th is a 1GB /swap (/dev/hda4)


now i can boot to live cd, and when i run "sudo lshw" it recognises all of my partitions, but will not boot to "/dev/hda2" when i attempt to start with no live cd. 

any ideas?

oh ya, ubuntu 6.10 i386

---

### Post by rsambuca on 2006-12-19
Sorry, I am a little confused.  You are able to use the live CD?  If so, have you gone through the installation process?

---

### Post by Wall86 on 2006-12-19
ya, I install it, but then on booting with no live cd, it does not mount my / partition i am guessing

oh ya, only a brief flicker from my hdd light when trying to mount, then no activity

---

### Post by rsambuca on 2006-12-19
Where is the grub installed?

---

### Post by Wall86 on 2006-12-19
i have not been able to check (all i have is ubuntu, and it is not working)

i would guess it is on the /boot

but i can boot to the gurb loader by hitting esc. on boot,

any way with live cd i can mount some of these partitions, and actually go through them and possibly modify GRUB from live cd?

---

### Post by rsambuca on 2006-12-19
Yes, the live CD is quite a handy way to fix a borked system!

---

### Post by Wall86 on 2006-12-19
but how can i mount the partitions to look through them? any ideas? i am a newb in all honesty (with pertaining to linux) so i have been learning ever step of the way (more then i have learned in windows in like 3 years combined) and now i am talking the head first plunge into linux with no chance of going back, i have seen where windows is taking vista, and i will not go there.

so how could i mount my partitions within the live cd?

---

### Post by rsambuca on 2006-12-19
First go to the terminal. 

try this:

```
sudo mkdir /media/hda2
sudo mount /dev/hda2 /media/hda2
```
The first line will create a directory called /media/hda2
the second line will mount the hda2 partition to the newly created directory.  Then you should be able to view the files in hda2 by going to the "Places" on your toolbar.

---

### Post by Wall86 on 2006-12-19
kk, i will try that when i get home from work (don't think my work would like me installing ubuntu onto there precious windows machine....) 

but hopefully that will work, will that also work with my other partitions as well? just so i can look through them for any other problems?

---

### Post by rsambuca on 2006-12-19
Yeah, it should work for all of them.  Obviously you will have to change the hda# for each particular partition, and create a separate directory for each.

---

### Post by Wall86 on 2006-12-19
ok, one more thing, what am i looking for? 

should i be looking for liek a wrong directory to the /dev/hda2 ? or just for errors in general? if i post it onto here will people be abel to help me debug? and will i also be able to modify files in the partition?

---

### Post by Wall86 on 2006-12-19
thought it had not posted, sry

---

### Post by beebelo on 2006-12-20
> **Wall86 said:**
> ok, one more thing, what am i looking for? 

should i be looking for liek a wrong directory to the /dev/hda2 ? or just for errors in general? if i post it onto here will people be abel to help me debug? and will i also be able to modify files in the partition?

Wall86, if you are able to mount using rsambuca's directions above, then come back and post the contents of your /boot/grub/menu.lst file.

---

### Post by Wall86 on 2006-12-20
ok, when i try to mount it i get:

```
mount: /dev/hda2 is not a block device
```

---

### Post by Wall86 on 2006-12-20
anyone have some ideas? 

```
sudo ls -l /dev/hda
```

returns: 
```
root disk 3, 0 2006-12-19 19:31 /dev/hda
```

---

### Post by Wall86 on 2006-12-20
ok, when i go into the GRUB at boot, this is what ubuntu looks like:

```
root (hd0,0)
kernel /vmlinuz-2.6.12-10-generic root=/dev/hda2 ro quiet splash
initrd /initrd.img-2.6.17-10generic
quiet
savedefault
boot
```

---

### Post by Wall86 on 2006-12-20
if i click ctrl-alt-f1 at boot i get:

```
Buffer I/O error on device hda, logical block 0
```


any ideas?



EDIT:

When i attempt to modify the GRUB "kernel" it tells me "un recognised device string" (error 11 i think) when i press >tab< for automatic device listing, i think......

---

### Post by rsambuca on 2006-12-20
hmmm...  I have never dealt with these type of errors before.  I hope someone else might be able to assist you.

---

### Post by ChM on 2006-12-20
Just a naive question. Are you installing edgy ? Is it suppose to be a dual boot with windows ? 
Have you set the partition as bootable ? In the live CD look for the GParted partition manager. This is a very convenient tool to manage your partitions. You should see the word boot in the right most column on the partition holding ubuntu.

---

### Post by Wall86 on 2006-12-20
i have made it bootable a few times, no luck,

this is just ubuntu, no other os's

i got edy eft amd64 working, but it would not use my wireless card, so i have opted for the i386, and now it will not work....



UPDATE: installed oem from alternate, now all it does is go to the splash screen, then it just kinda go's to a black screen with blinking cursor.....

---

### Post by Wall86 on 2006-12-20
still no luck with an oem install, this time tho, after boot, it go's to a blinking cursor on black screen, (after showing usplash)

that was using the guided partitioning, tonight, if i have time after work, im gonan be doing a manual partitioning. see if that helps out.

---

### Post by beebelo on 2006-12-21
> **Wall86 said:**
> anyone have some ideas? 

```
sudo ls -l /dev/hda
```

returns: 
```
root disk 3, 0 2006-12-19 19:31 /dev/hda
```

Sorry to not reply, I've been offline.  I dont' know what that means.  If you did as rsambuca suggested:
```
mkdir /media/hda2
sudo mount /dev/hda2 /media/hda2
```

then you would type this to get the directory listing:
```
cd /media/hda2
ls -l 
```

If this is not a dual boot, and you have no data to lose, I'd just go ahead and start over.  I'm not sure what you're doing/not doing.  I get the feeling your problem has a very simple answer, and we're just assuming it's something that was already done...

What do you get if you do this:

sudo fdisk -l  (that's an L)

This will display your partition table.

Is it possible you didn't set your mount points during installation??

One other thing:  Don't install the OEM version!   You'll lose most of your configuration  when you convert it to a regular install.  I've not used the installer recently so I can't say the exact wording, but you just want to install a normal installation.

One other other thing:  Can you edit grub menu.lst and remove the "quiet" and "splash" parameters.  That way you can watch the text as it boots.  Or, look in /var/log/messages (I hope thats the correct location).

---

### Post by Wall86 on 2006-12-21
it was just that the oem version was the first type that worked (amd64, but it does not support my wifi), i am going on my 30th re-install with dif settings, getting very very frustrating because i am currently stuck on an uber slow laptop. when i am done trying to fix this, i will boot to live cd and try the fdisk -l

---

### Post by Wall86 on 2006-12-21
ok, when i remove the quiet splash screen, it go's till it says :

```
Begin: Waiting for root filesystem... ...
```

and after that line, it is just loading my USB mouse, and USB HUB (if i remove, makes no difference,

then it just drops me to a shell with no tty job control

---

### Post by beebelo on 2006-12-22
Try searching for "mounting root file system" and you'll find other posts on this topic.  I'm afraid your problem is beyond my experience or expertise.  

Thoughts/questions:
- Is LVM or RAID involved? I know you can have problems there ...  
- Are you using a SATA drive?

[Check out this thread]("http://ubuntuforums.org/showthread.php?t=244074").  USB may be causing your problem somehow.

---

### Post by Wall86 on 2006-12-22
i have no SATA drives,

i only have 1 ultra ATA/133 7200 RPM 200 GB hard drive,

i think this might have something to do with BIOS settings, any help on what might be causing this?

---

### Post by bulldog on 2006-12-22
Just a ```
sudo fdisk -l
``` would be sufficient for now :D

Any special reason you made a separate /boot?
And on which partition is your / (root)?

---

### Post by Wall86 on 2006-12-22
this is how my hard drive is layed out

/boot 250 MB 
/ 10 GB
/home 160GB
/swap 1GB

---

### Post by Wall86 on 2006-12-23
ok, i have tried almost everything, im thinking of just giving up, think i might just be stuck with windows, i think i will be re-installing windows after boxing day, so i give myself that long to try and get this working, im hoping i can, but i do not see very many more things i can try.

---

### Post by Wall86 on 2006-12-23
results from : 
```
 fdisk -l 
```

after a re-install using guided partitioning.

```

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       24415   196113456   83  Linux
/dev/hda2           24416       24792     3028252+   5  Extended
/dev/hda5           24416       24792     3028221   82  Linux swap / Solaris

```

still no boot.

---

### Post by bulldog on 2006-12-23
Okay,you'll use the live cd I suppose?
We have to mount your ubuntu to access the menu.lst.
To make a mount point```
sudo mkdir /mnt/rescue
```
To mount ```
sudo mount /dev/hda1 /mnt/rescue
```
To access your menu.lst```
gksudo gedit /mnt/rescue/boot/grub/menu.lst
```

If you can copy the outcome of the last command to the forum we can have a look if the problem lies inhere.
If it's a hardware issue this won't help of course.
But if installing goes well and you can use the live cd without a problem,ubuntu should boot from your hard disk.

---

### Post by SurferJoe on 2006-12-29
Thanks for the hints - I had a similar problem.

Still have one small niggle.
hda2 is shown there OK in media but when I reboot , the hda2 section is empty -
I need to do a manual entry of 

sudo mount /dev/hda2 /media/hda2

in terminal to get my files back.

Where abouts do I need to make this change so it becomes permanent and automounts on startup?

---

### Post by beebelo on 2006-12-30
Hey SurferJoe,
 
I lost track of this thread what with Christmas and all... Anyway:
 
> **SurferJoe said:**
> 
Where abouts do I need to make this change so it becomes permanent and automounts on startup?
 
 
The file you're looking for is /etc/fstab. This is where your root, home and swap partitions get automounted. Also any other partitions or drives you want available. But if /dev/hda2 is where your root is, you don't want to mount that in /media. The system should be mounting it something like:
 
```
 
[SIZE=2]/dev/hda2 / ext3 defaults 1 1 [/SIZE]
[SIZE=2]
```[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Don't take that too literally; I'm just kinda going by memory.  [/SIZE]
 
But I'm perplexed by all this. I don't understand why you guys' installation didn't take care of this as it should have. The only reason I've come up with is that you didn't set your mount points in the partitioning step of installation. But I'm certainly no expert...

---

### Post by SurferJoe on 2006-12-30
What I actually had on install was :

1 of 320GB hdd
1 of 300GB hdd

All I did originally was put the home folder onto the 320GB which ended up with way too much space free on the , what I would call , the "system" drive.

Anyway , I booted with the Live CD , used GParted and shrunk the "system" partition down to 20GB , which I understand should be more than ample.
Then I created the new partition hda2 which was the balance of space.

Rebooted as usual and then entered some mount commands I picked up from there and here and this is sort of where I am now.
I am not overly fussed if I need to reformat completely to sort this out correctly , as from what I understand the home partition remains intact and so should more or less be OK , and even if it isn't , it is no great disaster.

My fstab file at present is :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=364e75be-4af6-4a43-9a81-737e2224ca27 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2 
UUID=364e75be-4af6-4a43-9a81-737e2224ca27 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=5a6d0185-c94c-42be-b617-382b9f515293 /home           ext3    defaults        0       2
# /dev/hda5
UUID=749ff423-f69e-40cd-819f-d79b0f3e14d1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
mount dev/hda2 media/hda2

The last mount statement was my last attempt before replying to your post.

Thanks for any tips you may give.

---

### Post by SurferJoe on 2006-12-30
OK took the "easy" way out.

Did a reinstall leaving the home and hda2 partitions intact and on reboot everything is recognised as I needed it.

Thanks again - got to love the installer for not screwing up things.

---

### Post by beebelo on 2006-12-31
I'm glad you got it worked out!

Looking at your original fstab, it appears you had been mounting the root system in two different places (removing the UUID junk for simplicity):  

> **SurferJoe said:**
> 
# /dev/hda1  /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2  /               ext3    defaults,errors=remount-ro 0       1


That's probably what went wrong.  Don't know how this would happen...  I use the installer's partitioner.  I think the installer has changed with Edgy, but I still like the traditional Debian-style partitioner.  After making each partition, you go to the menu option for setting the mount point.  Do that for each partition.   

Sorry I'm not being very specific about these things. Seems that whenever I have time to reply, I'm on a windows computer instead of my home system.

Happy New Year -- enjoy!

---

### Post by Vox754 on 2007-01-01
**First.** You should avoid posting small questions or giving information right after a previous post of yours. You should either edit your previous post, to clarify the problem and give more information, or wait at least a week to post again to bump the thread back to the top.

**Second.**
[QUOTE="wall86"]1st partition is a 250 MB /boot (/dev/hda1)
2nd partition is a 20GB / (/dev/hda2)
3rd partition is about 160GB /home (/dev/hda3)
4th is a 1GB /swap (/dev/hda4)[/QUOTE]
So you say. But what actually counts is what your system gets with "fdisk -l".

**Third.** The command "lshw" does not give you partitioning information, it "lists hardware".

**Fourth.**
[QUOTE="wall86"]ok, when i go into the GRUB at boot, this is what ubuntu looks like:

```
root (hd0,0)
kernel /vmlinuz-2.6.12-10-generic root=**/dev/hda2** ro quiet splash
initrd /initrd.img-2.6.17-10generic
quiet
savedefault
boot
```
[/QUOTE]
Remember, just for reference, what you posted is part of a file called "/boot/grub/menu.lst"

**Fifth.**
[QUOTE="wall86"]after a re-install using guided partitioning.

```
Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device             Boot     Start       End      Blocks        Id    System
**/dev/hda1**     *         1        24415    196113456   83   Linux
/dev/hda2                      24416    24792     3028252+    5   Extended
/dev/hda5                      24416    24792     3028221     82   Linux swap / Solaris
```

still no boot.[/QUOTE]
Obviously, if you reinstalled with a different partitioning scheme, the root device in the GRUB menu ("menu.lst") no longer matches with the partitioning table located in "/etc/fstab". Just for reference, the bold face device names in the two previous sections should match.
Whenever needing help for partitioning or mounting file systems you should provide "/boot/grub/menu.lst" and "/etc/fstab" right away.

**Sixth**. Solutions. As you have an IDE/ATA drive, it is possible that you have connected the drive first to one cable connector, installed Ubuntu, and then connected the drive to another connector. If this is the case, the drive may be initially recognized as "/dev/hda", but upon reconnection it may be relabeled as "/dev/hdb". Therefore, the GRUB menu points the "root=" directory to a nonexistent drive and the system cannot boot. You can manually edit the booting options by pressing "e" in the GRUB menu. Permanent changes can be made at "/boot/grub/menu.lst", once you have booted the system.

Make sure you are using an 80-wire IDE cable instead of a 40-wire one.

In your BIOS locate the section that describes your hard drive and try changing the "translation method" from one option (Auto, Normal, LBA, Large) to another.

If you think there is a problem with your BIOS, try resetting it to factory defaults. On the physical main board there should be jumpers that need to be short-circuited in order to erase settings on the BIOS. You can also try taking off and reinstalling the circular battery that powers it. This is done in case of a disrupted or virus-infected BIOS.

---

