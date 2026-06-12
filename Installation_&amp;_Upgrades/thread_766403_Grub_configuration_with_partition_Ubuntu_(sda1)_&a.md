---
title: "Grub configuration with partition Ubuntu (sda1) &amp; Windows (sda6)"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by aroddo on 2008-04-25
Here's what gpared shows:
[[IMG]http://img150.imageshack.us/img150/1163/gpartedvh8.png[/IMG]](http://imageshack.us)

Due to several reinstallations (xp -> vista -> xp again) I ended up with my main Windows OS on drive E:
It still had an old unused windows partition on C: but i think it just served as mount point for the windwos bootselection.

Now I finally decided to install ubuntu as regular os on my pc with the intention of killing the C: windows and keeping the E; windows.

I successfully installed Ubuntu 8.04 on sda1 and it boots just fine.
The Windows E: drive is located on sda6 but wasn't detected by grub, so I have to do it manually.

So I opened /boot/grub/menu.lst and found this:
```

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7997de24-3f8a-4a69-a6d8-d13f1fab4bce ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7997de24-3f8a-4a69-a6d8-d13f1fab4bce ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

```

No mention of sda1 - although I guess it translates to hd0,0

So, what do I have to put in there to be able to dual boot windows from sda6 ?

Cheers!

---

### Post by sisco311 on 2008-04-25
sda1 -> (hd0,0)
sda2 -> (hd0,1)
...
sda6 -> (hd0,5)
...
sdb1 -> (hd1,0)
sdb2 -> (hd1,1)
...

> 
title        Windows 
root        (hd0,5)
makeactive
chainloader    +1


---

### Post by aroddo on 2008-04-25
Thanks, but I get an error:


error 12: Invalid Device Requested


I played a bit with grub (really cool feature being able to edit the bootloader configuration live), but the partition containing windows gets labeled invalid.

I'm not sure, but I assume that windows wrote something on the c: drive which allowed it to boot other windows versions from non-primary partitions.

any ideas (or better yet: experience?)

Cheers!

---

### Post by Herman on 2008-04-25
Yes, in spite of all the hype about Vista's 'new boot manager', Windows ability to boot more than one operating system remains prehistoric.

What has happened is, Windows has been allowed to set up a 'default Microsoft style dual boot' arrangement, and in so doing, your vital boot loader files from your later Windows operating system were copied over to your older system, which you have now deleted.
One way to avoid this is to use GRUB or some other 'third party' boot loader to 'hide' the Windows partition that's on the hard disk before installing another Windows. Then both Windows installs will remain independant and retain their vital boot loader files.
Here's a link for more information about what happened, [http://www.goodells.net/multiboot/principles.htm](http://www.goodells.net/multiboot/principles.htm)[COLOR=#cc0000][FONT=Arial][COLOR=#000000], and here's the home page of that site, [/COLOR][/FONT][/COLOR][Understanding MultiBooting and Booting Windows from an Extended Partition.]("http://www.goodells.net/multiboot/index.htm")

So, to get your operating system to boot now, you need to get back a copy of your vital boot loader files.
I'm not sure how to do that with Vista. With Windows XP it was okay to go find another Windows XP install in another computer and copy the files ntldr, NTDETECT.COM and boot.ini, and paste those into the root of your Windows drive and boot.
I don't even know what the boot loader files for Vista are called.

The other things to do are to set the boot flag in your logical partition with GParted by right-clicking on the partition and clicking 'manage flags'. As far as I know, no boot loader can set the boot flag in a logical partition, but a partition editor can.
Also, you need to comment out the 'makeactive' command from your Windows booting stanza in your /boot/grub/menu.lst. GRUB's 'makeactive' command is for setting the boot flag. Windows can't boot without a boot flag, and even though the boot flag is already there, GRUB will think it has to do it, and give you 'Error 12: Invalid device requested, Press and key to continue...', and fail.

You should be able to boot your Vista with GRUB if you can do those three or four things.
ie set boot flag, add boot loader files, delete 'makeactive' command and if needed, edit boot.ini as well.

Actually, after re-reading your posts, I'm still a little unclear if you have deleted Windows XP, and you're trying to boot Vista,, or the other way around. I'm just guessing that's it's Vista you want to boot.
If it was XP you wanted to get going again, the CD from the following website,  [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm"), not only contains the files you need, but also will boot Windows for you so you can edit boot.ni from within Windows itself.
That CD may boot Vista too, I really don't know.
The other way to do it is to use a Windows Installation CD, (that should contain the files you need), and run 'bootcfg /rebuild', if it's Windows XP, to generate a new boot.ini if none exists, or repair your old boot.ini if there is one. I don't know what command to use if you have Vista.

If you have a floppy disc drive, another thing you can do is you can make a bootable floppy disc from another Windows computer. I don't know of another way to do it that will work, maybe with syslinux, I have yet to try that. You will be able to copy the boot loader files from the CD to the floppy disc using Ubuntu, and edit the boot.ini file in the floppy disk from Ubuntu to boot Vista (from the boot floppy). You must only edit letters and numbers, avoid making any new lines in the boot.ini file.

Anyway, I'm sure you'll be able to get it to boot if you keep on trying and don't give up.

Regards, Herman :)

---

### Post by aroddo on 2008-04-25
Thank you for your elaborate answer.

Before I read your advice, I already tried some things by myself:

I copied the boot.ini, ntdetect.com and ntldr files from another xp installation to the sda6 partition. And yes, it's Windows XP. 

I edited the grub entry:
```

title         Windows XP
rootnoverify  (hd0,5)
chainloader +1
boot

```

This made a difference because i didn't get the invalid device error anymore.
Grub now tries to boot the partition, but I get stuck immedeatly afterwards, getting a fresh black screen with the message:
```
Starting up ...
```
or so in the top left.

I'm not sure if that's a windows message or a grub message, but i suspect it's the former.

Sadly I get no further messages thereafter since it's stuck there. I don't even get to *"NTLDR is missing, press any key to restart"*

I'll read through the material you gave me but I don't understand why flagging the sd6 with boot could help. Wouldn't that mean that grub gets completely ignored because gparted removes the boot flag from the sda1 partition when I do that ?

Anyway, thanks, I'll try some of those.

Cheers!

PS: About the xp/vista history: I started out with xp on c: and a big d: partition. I resized d: and created an e: partition for vista. I ran into the notorious vista multiboot problems some time later, got fed up and killed vista and installed xp on the now vacant e: partition, keeping the old and crowded XP on c: without ever using it. Now I installed ubunta on what was formerly c:. I hope that makes it clearer. :)

---

### Post by aroddo on 2008-04-25
[[IMG]http://img234.imageshack.us/img234/7718/part2gy7.png[/IMG]](http://imageshack.us)

menu.lst
```

title		Windows XP
root		(hd0,5)
chainloader +1

```

I copied the ntdetecd.com, ntldr and boot.ini to the XP partition.

I flagged sda6 with boot.

I still get the freeze at:
> Starting up .. 

And since it looks like a Grub message (i see that when booting ubuntu, too) I have to assume that grub detects the partition as bootable but doesn't do anything about it.

After all, i should get at least some error messages saying that no OS is present or something along that line...

doesn't look like there's an easy way out. :(

[edit]
Just  for the heck of it I changed the root to (hd0,4) and got the exact same result. looks like there's more to it than just setting flags and copying files.

---

### Post by sisco311 on 2008-04-25
Boot your Windows XP Installation CD and enter the Recovery Console. Try to restore the boot sector of the partition:
```
FIXBOOT E:
```

---

### Post by dstew on 2008-04-25
I have heard that Windows will not boot on a logical partition, only on a primary partition. Since /dev/sda5 is a logical partition, could this be your problem? The "Starting up..." is coming from grub, but it gives that message and hands control over to the boot loader. It is not a grub error, just grub's last message. Grub is chainloading the first sector of the target partition, then jumping to it. If that sector contains garbage, it will freeze, and not give an error. Or, if it is a Windows boot loader, any errors would be expected to come from the Windows loader. So, really, your problem is with the Windows boot loader, or with the Windows boot sector, and not with grub. The grub menu seems to be set up correctly. I suspect that your Windows is set up to boot, or is not happy being on a logical partition.

---

### Post by aroddo on 2008-04-25
Fixboot E: didn't help although truth be told I had to type Fixboot D: since for some arcane reasons my e: drive shows up as d: in the recovery console. 

I also managed to boot XP with the help of the boot-cd found here: [http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

I got it running by picking the fifth option, which amounts to a boot.ini entry of 

> 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional"


I have no idea how that entry relates to the real world, but that's not my problem since I can't even get there using grub.

Right now I don't see any solution apart from stuffing the windows bootloader on a primary drive and then reinstalling ubuntu. and I just know that this will screw up in a slightly different way.

I'd prefer to convince windows to accept it's place on that logical partition but in case it doesn't, does anyone know the best way to get the windows bootloader(or whatever) on a primary partition without having to install the whole windows crap AND keeping grub for choosing what to boot ?

---

### Post by dstew on 2008-04-25
If Windows boots after fixboot d:, and your boot.ini shows that the Windows partition is no. 3, try to chainload with root (hd0,4) again.```
root		(hd0,4)
makeactive
chainloader +1
```You can enter these commands at the grub menu by pressing 'c' to get a command line. If you do it that way, you might have to also enter **boot** after the commands to make it go. Or, you can edit the /boot/grub/menu.lst file.

---

### Post by aroddo on 2008-04-25
booting windows had nothing to do with fixboot.
I could boot it only by using the boot-cd (or the boot-usb-stick).

all attempts using just grub failed.

I haven't tried to add the makeactive command, though, but i don't expect that to work either.

---

### Post by Herman on 2008-04-25
You just have to edit boot.ini in your Windows drive to agree with the partition number that you used to successfully boot it from the tinyempire CD.
Don't worry about the fact that the partition number that works for Windows boot.ini doesn't make any sense at all.
Nobody says anything in Windows has to make sense. 

You can mount your Windows partition and edit boot.ini from Linux, but only edit the partition number, avoid making any new lines. Line breaks in Linux text editors seem to be different from line breaks from a Windows test editor and they'll corrupt your boot.ini file. It will look fine from Linux, but from Windows, the entries will all be in one line with little rectangle symbols where a new line should start.
From a Windows recovery console, the command 'bootcfg /rebuild', will rebuild your boot,ini file if it's corrupted, and should correct it if the partition number is wrong too. That's worth a try.

I speant a whole weekend learnig how to get Windows XP to boot in a logical partition not so long ago, and I can do it, so you should be able to do it too. 
Keep trying.

Regards, Herman  :)

---

### Post by Herman on 2008-04-25
Those yellow triangles with the exclamation marks in them in your GParted screencap are a sign that your NTFS file systems need a file system check too.
You should run CHKDSK /R on them from a Windows Recovery Console.

---

### Post by Pumalite on 2008-04-25
> **dstew said:**
> I have heard that Windows will not boot on a logical partition, only on a primary partition. Since /dev/sda5 is a logical partition, could this be your problem? The "Starting up..." is coming from grub, but it gives that message and hands control over to the boot loader. It is not a grub error, just grub's last message. Grub is chainloading the first sector of the target partition, then jumping to it. If that sector contains garbage, it will freeze, and not give an error. Or, if it is a Windows boot loader, any errors would be expected to come from the Windows loader. So, really, your problem is with the Windows boot loader, or with the Windows boot sector, and not with grub. The grub menu seems to be set up correctly. I suspect that your Windows is set up to boot, or is not happy being on a logical partition.

I used to think the same, but Herman says that Grub is able to boot Windows from a logical partition. ( I remember from a post of his that I read some time ago)

---

### Post by Herman on 2008-04-25
:) Well I used to think the same thing too, until two or three weeks ago when I got curious about it and ran a lot of experiments in a test computer.
GRUB can boot Windows XP in a logical partition but it can't put the boot flag on it and gets error 12 when it tries.  
GParted and maybe other partition editors can set the boot flag in a logical partition.
You have to avoid the use of GRUB's 'makeactive' command after that, just let the boot flag remain where it is. Delete or comment out the 'makeactive command.
Windows should boot from GRUB then if everything else inside Windows is okay.

  dstew might be right about the boot sector, Windows boot sector is required to be right or GRUB can't chainload Windows,FIXBOOT does have a lot to do with whether or not Windows will boot. The tinyempire boot CD doesn't require a MBR, boot sector, or the Windows bootloader files, it bypasses all of those, but those are all still needed to get Windows to boot from GRUB.
Also the boot.ini file may need to be edited, and also the file system needs to be usable too.
 It could be any one, or all three of those things that's holding up the boot process in aroddo's computer now.

If all of those things are fixed it should boot.

---

### Post by dstew on 2008-04-25
Herman posted:> GRUB can boot Windows XP in a logical partition but it can't put the boot flag on it and gets error 12 when it tries. Thanks for your addition to grub-knowledge. Just so I am clear about this, it is the "makeactive" statement that causes grub to fail if chainloading from a logical partition? And, if you can set the boot flag on the logical partition using a partition editor, and leave "makeactive" out of the grub menu item, it will chainload windows OK? Thanks for doing the experiment.

---

### Post by Herman on 2008-04-26
> Thanks for your addition to grub-knowledge. Just so I am clear about this, it is the "makeactive" statement that causes grub to fail if chainloading from a logical partition?  Yes, the 'makeactive' command causes GRUB to fail even when the boot flag is already set in the right partition with a partition editor. It is necessary to comment out or delete the 'makeactive' command and just leave the boot flag alone there and Windows will boot okay in a logical partition.
At least that's what happened in my test computer. It would be nice if someone else finds out the same thing in another computer, with a different installation.
> And, if you can set the boot flag on the logical partition using a partition editor, and leave "makeactive" out of the grub menu item, it will chainload windows OK? Thanks for doing the experiment. Yes, it will boot okay, providing the boot sector is okay, and the three vital boot loader files are all there, and there isn't anything else wrong with Windows. There could be millions of reasons why Windows might still not boot, but it's nice to be able to help Windows users this far, at least. It happens every once in a while that a Windows users who had been dual booting two Windows versions deleted their primary Windows 'boot partition' to install Ubuntu. Up until recenty I thought they had to re-install if they still needed Windows. From now on there's a good chance we can help them.

Regards, Herman :)

---

### Post by zAlbee on 2009-02-02
> **aroddo said:**
> 
I copied the ntdetecd.com, ntldr and boot.ini to the XP partition.

I flagged sda6 with boot.

I still get the freeze at:
 
> Starting up .. 

And since it looks like a Grub message (i see that when booting ubuntu, too) I have to assume that grub detects the partition as bootable but doesn't do anything about it.

After all, i should get at least some error messages saying that no OS is present or something along that line...


Hi,

This came up in my Google search, and I saw that this problem was not resolved. I had almost the same experience as the original poster, and I solved it.

I had Windows XP and 7 installed on 2 logical partitions. I was trying to boot each Windows directly from GRUB. After fixing my boot sectors with bootsect.exe, and getting rid of GRUB Error 11 and 12, I got a blank screen after "Starting up".

Turns out the logical partitions were created by my Windows XP CD. So I had to fix the "hidden sectors" value in my partition tables following **[Dan Goodell's instructions]( http://www.goodells.net/multiboot/ptedit.htm)** using **[PTedit32.exe](ftp://ftp.symantec.com/public/english_us_canada/tools/pq/utilities/PTEDIT32.zip)**. (This is a Windows program, but I was able to run it, because I was booting Windows through the Win7 bootmanager fine ;-).)

After reading [How to fix XP when the boot files are missing](http://ubuntuforums.org/showthread.php?t=813628), I think the testdisk package in Step 5 might be able to do this too? Only I never saw that link originally because the "missing boot files" problem was not my problem at all!

Hope this helps someone. My exact triple boot method is [here](http://forums.ceruleanstudios.com/showpost.php?p=763830&postcount=114).

---

