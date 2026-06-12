---
title: "Popular Problem - Dual Boot Dual Hard Drives 6.06"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by ianmm on 2007-02-13
Hi There,

I'm just now starting to make my long-planned transition to linux by setting up a dual boot system with dual SATA hard drives.  I found some good threads that have helped, but I am unable to get windows xp to boot from grub. Additionally, I reinstalled ubuntu with a partition for a /boot mount since it seems that makes the grub.bin/linux.bin addition to boot.ini a little easier or more logical. 

In it's currently inoperable state, I have switched hd(1,0) and hd(0,0) and remapped (after trying normal) and receiving  "Grub loading, please wait... Error 15."  

The first time I got grub working to boot linux, I had to switch my (hd1,0) and (hd0,0) and remap.  After getting it to work for linux, I could not get grub to hand the loading process to windows xp (nor could I get boot.ini to recognize my linux install). 

/dev/sda = Windows XP (NTFS)
/dev/sdb = Linux
             1 =/boot (ext3)
             2 =/    (ext3)
             3 =/swap 

I appreciate everyone's efforts with this, and it's great to see this forum community so responsive and interested, I hope I can contribute in my future endeavours. 

-Ian MM

---

### Post by rsambuca on 2007-02-13
Why don't you post your menu.lst so we can see what you have done.

---

### Post by ianmm on 2007-02-13
okay, here's the only parts of menu.lst I've modified.

## END Default Options ##

title                    Ubuntu, kernel 2.6.15-23-amd64generic
root                   (hd1,0)                      // my change
kernel                /vmlinuz-2.6.15  ...
initrd                  /initrd.img02.6.15-23-amd64-generic
savedefault
map                   (hd0) (hd1)               // my change
map                   (hd1) (hd0)               // my change
boot

//same changes apply to  recovery and memtest

title                    Microsoft Windows XP Pro
rootnoverify        (hd0,0)                      // my change
savedefault
makeactive
map                   (hd1) (hd0)                 //my change
map                   (hd0) (hd1)                // my change
chainloader +1


// END

Grub console can't find anything either, am I overlooking something huge?

Thank you for your patience with me.

-Ian

---

### Post by ianmm on 2007-02-13
Progress!

I posted the menu.lst that I just made changes to after re-running setup from grub console.

I now get a grub menu. 

The grub menu claims "Error 13: invalid or unsupported executable format" when trying to enter into windows XP...

Gives "Error 15: file not found" when trying to boot into Ubuntu.

I was able to recover the linux portion with [Herman's page]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer") , so i will try that again. But windows is still a mystery... any ideas?

-Ian

---

### Post by ianmm on 2007-02-13
Okay, I am in ubuntu again, my menu.lst is working well for linux booting, but still will not boot Windows XP (see below). My menu.lst had to be changed from the last one that I posted, This is what the end of menu.lst looks like now, it is contradictory to my setup (XP Disk is /dev/sda,  Ubuntu is /dev/sdb, which would seem to be HD0 and HD1 respectively, but it's opposite):

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-amd64-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.15-23-amd64-generic root=/dev/sdb2 ro quiet splash
initrd		/initrd.img-2.6.15-23-amd64-generic
savedefault
map 		(hd1) (hd0)
map		(hd0) (hd1)
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.15-23-amd64-generic root=/dev/sdb2 ro single
initrd		/initrd.img-2.6.15-23-amd64-generic
map 		(hd1) (hd0)
map		(hd0) (hd1)
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin 
map 		(hd1) (hd0)
map		(hd0) (hd1)
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
map 		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

//END





Now when i try to get grub to hand over the boot process to windows I get the error I had last time... 

"Loading Stage2Read Error"

My XP install is completely ntfs, and while grub can't read ntfs, the chainloader makes the hand-off possible right? If that is true, I can't figure out why windows won't pick up the boot process.

-Ian

---

### Post by confused57 on 2007-02-13
I've never seen anyone use mapping commands to boot Ubuntu, sounds like it works.
What you might want to do is post the output of:
```
cat /boot/grub/device.map
```

as well as

```
sudo fdisk -l
```
The -l is a small "L"

Which drive do you have in bios to boot first?

---

### Post by ianmm on 2007-02-13
here is device.map
//Start
$ cat /boot/grub/device.map
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
(hd3)   /dev/sdd
(hd4)   /dev/sde
(hd5)   /dev/sdf
(hd6)   /dev/sdg
//End



and here is fdisk -l


//Start
$ sudo fdisk -l

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      104391   83  Linux
/dev/sdb2              14        8778    70404862+  83  Linux
/dev/sdb3            8779        9039     2096482+  82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001    c  W95 FAT32 (LBA)

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       30401   244196001    c  W95 FAT32 (LBA)

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sde doesn't contain a valid partition table

Disk /dev/sdf: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdf doesn't contain a valid partition table
// END  //


Thanks for taking a look at this for me.

My second SATA drive is set to boot in bios. I can boot into windows by changing that order, but I would prefer to use be able to use grub.

As an aside, how do you get those spiffy "Code:" windows in your messages? (If I just labeled myself as 'noob' that would be appropriate :) )

-Ian

---

### Post by confused57 on 2007-02-13
I don't know, but you might try removing the mapping commands in your Ubuntu entries in grub & see if Ubuntu will boot without them.

You can try this temporarily in your grub menu at startup, highlight your Ubuntu entry, press "e" to edit, then remove the two mapping lines, then press "b" to boot...as I mentioned this change is only temporary, but I believe you already know how to make it permanent in your /boot/grub/menu.lst.

You can make code or quote "windows" by:
[code[enter command here[/code[

reverse the second bracket to enclose code & you get this:
```
enter command here
```

Add: You can change the device.map, which may help:
[http://users.bigpond.net.au/hermanzone/p15.htm#device.map](http://users.bigpond.net.au/hermanzone/p15.htm#device.map)

---

### Post by ianmm on 2007-02-13
Thanks for the tip on the code window.

I took the mappings out, and ubuntu is working fine. I'll give windows a try now, that my inevitable concern. It seems like SATA dual booting is somewhat broken.

Thanks for your help, I appreciate it greatly.

-Ian

---

### Post by confused57 on 2007-02-13
> **ianmm said:**
> Thanks for the tip on the code window.

I took the mappings out, and ubuntu is working fine. I'll give windows a try now, that my inevitable concern. It seems like SATA dual booting is somewhat broken.

Thanks for your help, I appreciate it greatly.

-Ian

I thought it would work without the mapping...if Windows still won't boot, you may be able to change your hd0 & hd1 designation in your device.map.
I'm gonna have to run, getting my bedtime...good luck.

Added: If you really want to get "fancy" with your posts:
[Click Me](http://www.ubuntuforums.org/misc.php?do=bbcode)

---

### Post by ianmm on 2007-02-13
Bump...

Does anyone have a clue as to why grub will still not boot windows? I have yet to try redoing the device map, and will report on that hopefully later this evening.

Any success stories for dual sata dual boot with windows on Sata1 and ubuntu on Sata2?

-Ian

---

### Post by confused57 on 2007-02-13
> **ianmm said:**
> Bump...

Does anyone have a clue as to why grub will still not boot windows? I have yet to try redoing the device map, and will report on that hopefully later this evening.

Any success stories for dual sata dual boot with windows on Sata1 and ubuntu on Sata2?

-Ian

You definitely need the mapping commands to boot your Windows drive, the entry you listed should work OK...if it doesn't, then you'll probably need to change your device.map.

title Microsoft Windows XP Professional
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

---

### Post by truck87bp on 2007-02-13
I had to change my IDE ribbon cable from my mobo to hd.  Had the old big wire style and replaced it with the fine wire style and it solved the problem....not sure about sata stuff.

---

### Post by rsambuca on 2007-02-13
You might consider trying a quick flip of the hard drive order in the bios.  Often the SATA drive order in grub can be different from the bios.

---

### Post by ianmm on 2007-02-13
Okay, 

I have tried a couple different things.

My menu.lst is the same as above, except that I've taken out the remapping entries in the linux menu entries. 

root is (hd0,0) for linux

root is (hd1,0) for windows
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 
(remapped so that windows thinks it's hd0)

This windows entry gives me "loading stage2[~10sec wait]read error"

Same thing happens if I try to load the windows entry without the remapping.

To make sure that this was grub and not windows, I booted the windows hd from my bios boot menu, and sure enough, windows loaded fine, in fact I'm writing this from windows.

Next I changed the device.map file to reflect /dev/sda as hd1 and /dev/sdb as hd0 .   Again, nothing. It has since been changed back.

My next inclination was to install grub on the windows drive via #grub-install /dev/sda .
i just tried it and got "Grub Loading... Error 17" . I am going to try it again right now.

I have not yet tried physically switching the order of the hard drives (unplugging #2 and #1 and putting #2 plug in #1 seat and vice versa). I will update how that goes if trying to install grub on windows drive doesn't work.

Question...

If grub installs on my windows drive, and I continue getting these errors, is there a way I can edit the menu.lst within that mbr, I've found that I can fix most of these errors from the grub console?


Again I appreciate everyones contribution to the discovery of the solution for this issue, I hope this helps those who are pursuing this same path.

If I can get this to work, I will post a final solution.

-Ian

---

### Post by confused57 on 2007-02-14
Don't try to install grub to your Windows mbr just yet...what you can try is go ahead and switch the position of your hard drives & set bios to boot to sda first(with your Ubuntu drive).

Do the editing of the grub menu at bootup by pressing "e", in your kernel line change the entry with root to root=/dev/sda2 & try to boot.

---

### Post by ianmm on 2007-02-14
Sorry, got your post a little late, anyways not to fret, grub-install was unable to install on my windows disk anyways for whatever reason (probably has something to do with it being NTFS).

I changed the physical plugs, so now /sda is my ubuntu drive, and /sdb is my windows drive as you recommended, but now I cannot locate menu.lst . My /boot folder appears as empty within Linux, and in spite of the fact that everything is working, it shows my root directory as being on /dev/sdb2.

When I check grub console geometry, /dev/sda is hd0 and /dev/sdb is hd1.

Things seem prime to do something more, but I'm a touch stumped because I cant find menu.lst. What do you suggest?

-Ian

---

### Post by confused57 on 2007-02-14
> **ianmm said:**
> Sorry, got your post a little late, anyways not to fret, grub-install was unable to install on my windows disk anyways for whatever reason (probably has something to do with it being NTFS).

I changed the physical plugs, so now /sda is my ubuntu drive, and /sdb is my windows drive as you recommended, but now I cannot locate menu.lst . My /boot folder appears as empty within Linux, and in spite of the fact that everything is working, it shows my root directory as being on /dev/sdb2.

When I check grub console geometry, /dev/sda is hd0 and /dev/sdb is hd1.

Things seem prime to do something more, but I'm a touch stumped because I cant find menu.lst. What do you suggest?

-Ian

First of all, does your Windows drive still boot if it is set in bios as the first hard drive booted?

You've switched your Ubuntu drive to the sda position and Windows drive to sdb...when you boot first to sda, if you get a grub menu, then do the press "e" to edit, then in the kernel line change to **root=/dev/sda2**, & press "b" to boot.   Try this first, if I'm understanding you correctly.

---

### Post by ianmm on 2007-02-14
Trouble... I'm currently booted on my live-cd because I tried to repair the windows mbr with "fixmbr" and silly me... it fixed the wrong mbr because I switched sata cables...

I cant seem to install grub to /dev/sda to fix things now. It returns a line that says "Could not find device for /boot: Not found or not a block device." same thing is returned with /dev/sda1.

Not sure what to do here...

Oh, and i was trying to fix the windows mbr because it seems that I screwed it up when I was trying my "#grub-install /sda" before switching cables.  I was booted into ubuntu as /dev/sda, so linux was able to boot after changing the cables, but windows disk was giving me a grub error 17.

Sometimes you have to take a step back to move forward right?

-Ian

---

### Post by confused57 on 2007-02-14
> **ianmm said:**
> Trouble... I'm currently booted on my live-cd because I tried to repair the windows mbr with "fixmbr" and silly me... it fixed the wrong mbr because I switched sata cables...

I cant seem to install grub to /dev/sda to fix things now. It returns a line that says "Could not find device for /boot: Not found or not a block device." same thing is returned with /dev/sda1.

Not sure what to do here...

Oh, and i was trying to fix the windows mbr because it seems that I screwed it up when I was trying my "#grub-install /sda" before switching cables.  I was booted into ubuntu as /dev/sda, so linux was able to boot after changing the cables, but windows disk was giving me a grub error 17.

Sometimes you have to take a step back to move forward right?

-Ian

If you don't mind reinstalling, I think that would be the quickest and easiest way to get up and running...since you don't mind grub being installed to Window's mbr, what I would do is connect your Windows drive to sda & your Ubuntu drive to sdb, set your bios to boot first to sda...install Ubuntu to sdb, when you have the option of where to install grub, type in** /dev/sda**...that way you'll be sure grub is installed on your Windows drive.

If you want to explore other possiblities, I'll try to help.

---

### Post by ianmm on 2007-02-14
I greatly appreciate your consistent help confused...

The trouble I've been having with the windows /dev/sda and linux /dev/sdb setup is that when I try to install grub to sda, it has been giving me those error 17... i suppose if I do that at install, it would find the menu.lst from /dev/sdb/boot. Is this correct? 

I'm certainly not opposed to reinstalling and trying again and that seems an interesting way to do it, but I can't recall last time having come across a section where I could install grub to /dev/sda.

-Ian

---

### Post by confused57 on 2007-02-14
> **ianmm said:**
> I greatly appreciate your consistent help confused...

The trouble I've been having with the windows /dev/hda and linux /dev/hdb setup is that when I try to install grub to hda, it has been giving me those error 17... i suppose if I do that at install, it would find the menu.lst from /dev/hdb/boot. Is this correct? 

I'm certainly not opposed to reinstalling and trying again and that seems an interesting way to do it, but I can't recall last time having come across a section where I could install grub to /dev/hda.

-Ian

If you have one of the earlier desktop live cd's, grub is automatically installed to (hd0)...on the more recent live cd's, when it asks where to install grub, there is a small "box" with hd0 entered, but there's an arrow with a drop-down menu, or you should actually be able to type in /dev/sda, in the "box".   If you reinstall, you really don't need a separate /boot partition.

You've been given so many options to try, that I'm not sure where you "stand" with your current booting capabilities...i.e., does the Ubuntu drive boot when connected as sda or sdb(booting first to the controller it's connected to) & I gather that you're not able to boot your Windows drive independent of Ubuntu...how you would prefer your system setup?

Your fdisk -l showed that you had SATA(sda, sdb, etc) drives, not PATA(hda, hdb, etc).

---

### Post by ianmm on 2007-02-14
Sorry hdb/hda was a mistake of habit. I will edit those entries to reflect sda/sdb.

Very interesting news! I switched the cables back to reflect windows=/dev/sda, linux=/dev/sdb

I have dual boot working. That mistake turned out to be a boon. Apparently the grub install on the MBR of the windows hd that keeps returning "Error 17" is perfectly operable. Here's where my newness doesnt pay off, I'm not sure what error 17 means, but I do know that somehow having a bootable xp cd in my cd drive, then not hitting a key to boot from it, sent it back to the windows drive mbr, which booted grub!

I thought this was my working grub install on /sdb, but on investigating geometry, hd0 showed an unknown partition and hd1 showed extfs. So I tried to boot into linux, had to change root to (hd1,0) and it worked. 

Windows didnt boot from grub right off the bat, I had to fixboot from the rescue console. After running fixboot, it boots from grub!

It seems now all I have to do is be rid of the Error 17 when booting to grub on /dev/sda, otherwise it seems this is going to work. I suppose the option being that I could leave the xp boot cd in there, boot from cd everytime and just let it be. Not a huge fan of that option, so I'm going to keep trying and let you know what happens.

Any ideas on the Error 17?

Indeed, sometimes you have to take a couple steps back to move forward.

I'll post a summary once this is all done.

-Ian

---

### Post by confused57 on 2007-02-14
> **ianmm said:**
> Sorry hdb/hda was a mistake of habit. I will edit those entries to reflect sda/sdb.

Very interesting news! I switched the cables back to reflect windows=/dev/sda, linux=/dev/sdb

I have dual boot working. That mistake turned out to be a boon. Apparently the grub install on the MBR of the windows hd that keeps returning "Error 17" is perfectly operable. Here's where my newness doesnt pay off, I'm not sure what error 17 means, but I do know that somehow having a bootable xp cd in my cd drive, then not hitting a key to boot from it, sent it back to the windows drive mbr, which booted grub!

I thought this was my working grub install on /sdb, but on investigating geometry, hd0 showed an unknown partition and hd1 showed extfs. So I tried to boot into linux, had to change root to (hd1,0) and it worked. 

Windows didnt boot from grub right off the bat, I had to fixboot from the rescue console. After running fixboot, it boots from grub!

It seems now all I have to do is be rid of the Error 17 when booting to grub on /dev/sda, otherwise it seems this is going to work. I suppose the option being that I could leave the xp boot cd in there, boot from cd everytime and just let it be. Not a huge fan of that option, so I'm going to keep trying and let you know what happens.

Any ideas on the Error 17?

Indeed, sometimes you have to take a couple steps back to move forward.

I'll post a summary once this is all done.

-Ian
Thought I'd check in once before "hitting the sack"...glad you got it working in a round-about-way...you'll get it eventually, it seems I learn more from trying to correct my snafus.

Here's one explanation of grub error 17:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)

from the Gentoo grub error page:
[http://www.gentoo.org/doc/en/grub-error-guide.xml](http://www.gentoo.org/doc/en/grub-error-guide.xml)

I don't remember if I've given you this link or not, the live cd can also be used to reinstall grub:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Also, you might want to download the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
this is Herman's site(he's an active forum member)...see the index for SGD and you might want to read his section on Grub, which explains how grub works.

Hang in there, there's always another day to "get it right".

I correctly assumed you meant sda, rather than hda.

---

