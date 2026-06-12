---
title: "How to boot Grub 2 from Grub legacy (Karmic from Jaunty)"
date: 2009-06-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Jags_FL on 2009-06-27
I have a Grub legacy installed on MBR (hd0) and I like to boot Grub 2 (Karmic default) installed on hd1,1

Untill now I was using:

title Any-Name
configfile (hd1,1)/boot/grub/menu.lst

Which seems to not working anymore (with Grub 2). I tried replacing 'menu.lst' part with 'grub.cfg' but it didn't work either.

I would also like to know _other way around_ how to boot Grub legacy FROM Grub 2.

Many thanks in advance, any help is highly appreciated. - Jags

---

### Post by tommcd on 2009-06-27
You can install grub2 alongside your grub legacy. Then you can use grub legacy to chainload into grub2. I have not tried this; but I have read about it in Herman's excellent tutorial:
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)
The Zenwalk wiki also has a good tutorial on grub2 which explains the grub.cfg file:
[http://wiki.zenwalk.org/index.php?title=Welcome_to_GRUB2--replacing_Grub_legacy_or_LILO_with_GRUB2](http://wiki.zenwalk.org/index.php?title=Welcome_to_GRUB2--replacing_Grub_legacy_or_LILO_with_GRUB2)
Hope these help. I have been interested in grub2 as well.

EDIT: I just noticed you have Suse in your sig. Is your grub legacy in Suse or Ubuntu? If you boot grub legacy from Suse, I'm not sure how you could chainload grub2 from Suse.

---

### Post by Jags_FL on 2009-06-27
@ tommcd

Thanks for the reply. openSUSE is on another machine.

I'm just trying to boot Grub 2 (Karmic; hd1,1) FROM Grub legacy (Ubuntu Jaunty; hd0). -jags

---

### Post by Herman on 2009-06-27
Make sure your Karmic GRUB2 is installed to the first sector of your Karmic partition, (aka 'boot sector'. If it isn't, install it there with [grub-setup]("http://members.iinet.net/%7Eherman546/p20/GRUB2m%20Bash%20Commands.html#grub-setup")  from within Karmic Koala,
```
sudo grub-setup /dev/sdb1
```Then assuming your Jaunty GRUB is installed to MBR in your first hard disk, add a chainloader command to Jaunty's menu.lst file,
```
title   Ubuntu Karmic Koala Alpha 2
root   (hd1,1)
chainloader +1
```The configfile command only works when the boot loader you're using can understand the commands in the configuration file you're using for instructions to boot with. That can be very handy if you're booting another operating system that also uses the same version of GRUB, or a similar version.
If the other boot loader is not GRUB, or is a far different version of GRUB, (uses different commands), the configfile command is useless because the GRUB you're using can't handle those commands.

The chainloader command can boot another boot loader, but the other boot loader needs to have an IPL installed in a MBR or Partition Boot Sector somewhere for that to work. It can be a totally different kind of boot loader.
The chainloader command is the one to choose in this situation.

Regards, Herman :)

---

### Post by Jags_FL on 2009-06-27
@ Herman

Many thanks for your detailed reply.

Ok, I added:

```
title   Karmic
root   (hd1,1)
chainloader +1
```

to Jaunty's menu.lst but now I'm getting this error:

```
Error 13: Invalid or unsupported executable format.

Press any key to continue...
```

For now I'm using following to boot into Karmic:

(from Jaunty) I accessed hd1,1 through Nautilus, opened Karmic's grub.cfg with gedit and copied following:

```
menuentry "Ubuntu, Linux 2.6.30-10-generic" {
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 148a23b9-685b-4fdb-b475-2c599bbf425b
	linux	/boot/vmlinuz-2.6.30-10-generic root=UUID=148a23b9-685b-4fdb-b475-2c599bbf425b ro  quiet splash 
	initrd	/boot/initrd.img-2.6.30-10-generic
}
``` 

changed it to this and pasted into Jaunty's menu.lst :

```
title	Karmic Daily
uuid	148a23b9-685b-4fdb-b475-2c599bbf425b
kernel	/boot/vmlinuz-2.6.30-10-generic root=UUID=148a23b9-685b-4fdb-b475-2c599bbf425b ro  quiet splash 
initrd	/boot/initrd.img-2.6.30-10-generic
quiet

```

But I guess that's not the 'proper' way to do it :)

Jaunty's grub is installed onto MBR (hd0) and Karmic's grub is on (hd1,1)

Thanks again, -Jags

---

### Post by Herman on 2009-06-27
GRUB Error 13 in your case probably means that something went wrong when you tried to install GRUB to the (hd1,1) boot sector, or you forgot or overlooked that step. [Grub error 13]("http://members.iinet.net.au/%7Eherman546/p15.html#13").
One thing I thought of that might cause some confusion is that to avoid confusion between linux numbering and GRUB's numbering, GRUB2 starts counting partitions from 1 now instead of from zero.
That makes it a lot more confusing than ever, because they still count hard disks from zero, so it doesn't match GRUB Legacy's numbering scheme either now. When you said (hd1,1) did you mean hard drive number 2, partition number 1, as in GRUB2's numbering scheme? Or did you mean hard drive 2, partition 2, as in Legacy GRUB's numbering? 

Next time you have Karmic Koala up and running, open a terminal and try installing it to your second hard disk's MBR, then there'll be no confusion,
```
sudo grub-setup /dev/sdb
```
,and/or
```
sudo grub-setup /dev/sdb2
```
Sorry for the confusion,

Regards, Herman :)

---

### Post by Jags_FL on 2009-06-27
@ Herman

thanks a lot.

Ok Grub2 was installed onto (hd1,1) _second hard drive - second partition_ at the time of Karmic installation.

I can boot into Karmic using the method I described in my earlier post. 

Now while creating entry **for** Karmic **in** Jaunty(Grub legacy) should I enter (hd1,1) or (hd2,2) for second hard drive, second partition ? 

I'm not at the machine right now... so when I get back, I'll check both out and will post the result here.

---

### Post by Herman on 2009-06-27
/dev/sdb2 stands for second hard drive, second partition in Linux terms
(hd1,1) is for second hard drive, second partition in Grub legacy in Jaunty for your chainloader command.
(hd1,2) for second hard drive, second partition in Grub2 in Karmic.

I think.

What's the output from sudo fdisk -lu?
```
sudo fdisk -lu
```

---

### Post by Jags_FL on 2009-06-28
ok so far I've tried:

(hd1,1)
(hd1,2)
(hd2,2)

with this:

```
title   Ubuntu Karmic Koala Alpha 2
root   (hd1,1)
chainloader +1
```

and I'm getting that Error 13 (as mentioned earlier) with all of those options.

Here's the result for sudo fdisk -lu:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00023706

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   156299263    78046208    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00056313

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    42363404    21181671   83  Linux
/dev/sdb2        42363405    59151329     8393962+  83  Linux
/dev/sdb3        59151330    75939254     8393962+  83  Linux
/dev/sdb4        75939255    78156224     1108485   82  Linux swap / Solaris

---

### Post by Jags_FL on 2009-06-28
sda1 : NTFS : Windows 7
sda2 : NTFS : Windows 7

sdb1 : EXT4 : Jaunty : Grub  on (hd0)
sdb2 : EXT4 : Karmic : Grub2 on (hd1,2) (hd1,2 as per new Grub2)
sdb3 : EXT3 : Blank
sdb4 : SWAP : SWAP

Windows 7, Jaunty boots up just fine. 

Karmic boots up too, if I use this:

```
For now I'm using following to boot into Karmic:

(from Jaunty) I accessed hd1,1 through Nautilus, opened Karmic's grub.cfg with gedit and copied following:

Code:

menuentry "Ubuntu, Linux 2.6.30-10-generic" {
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set 148a23b9-685b-4fdb-b475-2c599bbf425b
	linux	/boot/vmlinuz-2.6.30-10-generic root=UUID=148a23b9-685b-4fdb-b475-2c599bbf425b ro  quiet splash 
	initrd	/boot/initrd.img-2.6.30-10-generic
}

changed it to this and pasted into Jaunty's menu.lst :

Code:

title	Karmic Daily
uuid	148a23b9-685b-4fdb-b475-2c599bbf425b
kernel	/boot/vmlinuz-2.6.30-10-generic root=UUID=148a23b9-685b-4fdb-b475-2c599bbf425b ro  quiet splash 
initrd	/boot/initrd.img-2.6.30-10-generic
quiet

But I guess that's not the 'proper' way to do it.
```

---

### Post by Herman on 2009-06-28
:-k Hmmm, well I'm still learning things too, it seems they've changed GRUB 1.96 since last time I was playing with it and when I tried the equivalent of the same command I gave you earlier it gave me a warning message. It seems that GRUB 1.96 doesn't like being installed to a boot sector. I had to use --force after the command.
Nevertheless, it's working for me, and I'm having no problems chainloading any of my operating systems with GRUB2 installed to the first sector by chainloading from my 'Dedicated GRUB Partitions', (with GRUB Legacy in them).

I don't know why yours won't, perhaps try again with,
```
sudo grub-setup /dev/sdb2
```Otherwise, it will be quite alright to keep on booting with the direct kernel boot style boot entry you're using. 
Why not make that into a symlink boot entry though, so you won't need to edit it when you get a kernel update?
```
title    Karmic Daily
uuid    148a23b9-685b-4fdb-b475-2c599bbf425b
kernel    /vmlinuz root=UUID=148a23b9-685b-4fdb-b475-2c599bbf425b ro  quiet splash 
initrd    /initrd.img
quiet
```

---

### Post by Jags_FL on 2009-06-28
@ Herman
Upon this:
```
sudo grub-setup /dev/sdb2
```

I got this error:
```
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: If you really want blocklists, use --force.
```

So I tried this:
```
sudo grub-setup --force /dev/sdb2
```

and **finally** I was able to boot up using the chainloader FROM Jaunty. :D

Also, since its Grub legacy in Jaunty, I had to use (hd1,1) _second hard drive-second partition_ or else (if I use (hd1,2)) it was throwing me off to _second hard drive-**third** partition_ where I've just installed another OS.

I'm also going to keep one entry just in case as you said:
```
title    Karmic Daily
uuid    148a23b9-685b-4fdb-b475-2c599bbf425b
kernel  /vmlinuz root=UUID=148a23b9-685b-4fdb-b475-2c599bbf425b ro  quiet splash 
initrd  /initrd.img
quiet
```
[B]
Thanks a million for all your help[/B]. - Jags

---

### Post by Herman on 2009-06-28
:oops: Oops, that was what I was trying to tell you but I was interupted and hurried with my post and forgot to ammend the command, sorry.
Well done for figuring it out, and I'm glad you have managed to get your GRUB2 working okay now from Legacy GRUB.
Have you tried the splashimages in GRUB2 yet? They're great! :D
[GRUB2 Splashimages]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Splashimages.html")

---

### Post by Jags_FL on 2009-06-29
@ Herman

Many thanks for [GRUB2 Splashimages]("http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html"). I tried one of the picture ( 050817-N-3488C-028.tga ) through:

```
sudo apt-get install grub2-splashimages
> sudo apt-get install grub2-splashimages
```

but as you said it was still cutting off a lot of the bottom and right-hand side of the picture, may be because it was 640x424 but when I tried 'Flower_jtca001.tga' (640x480) it got displayed just fine.

Now even though I've gone through:

***** [http://grub.enbug.org/Manual](http://grub.enbug.org/Manual) : GNU GRUB 2 Manual

***** [http://wiki.archlinux.org/index.php/GRUB2](http://wiki.archlinux.org/index.php/GRUB2) : ArchWiki for GRUB2

***** [https://wiki.ubuntu.com/KernelTeam/Grub2Testing](https://wiki.ubuntu.com/KernelTeam/Grub2Testing) : Ubuntu Wiki for GRUB2 Testing

and have managed to boot GRUB2 from Grub legacy, still I couldn't figure out **how to edit or add entries to GRUB2 manually**. But I was able to edit GRUB TIMEOUT through
```
sudo gedit /etc/default/grub
```

Though [KernelTeam/Grub2Testing]("https://wiki.ubuntu.com/KernelTeam/Grub2Testing") does say 
```
nano /boot/grub/grub.cfg
```

under "Editing" but when I tried, I got "Permission Denied" message as grub.cfg is read-only file (the same message I got when I tried to edit through gedit).

If you know any place / Wiki to read on GRUB2, please let me know.

---

### Post by Herman on 2009-06-29
[FONT=Bitstream Vera Sans Mono]I don't know.
We aren't supposed to directly edit the grub.cfg file, it is 'automatically generated by /usr/sbin/update-grub using templates from /etc/grub.d and settings from /etc/default/grub.
I think we can edit files in /usr/sbin/update-grub, but I don't know how yet.
If you go look there, you'll see a README advising us that we can add more boot entries and they'll be added to the grub.cfg in numerical sequence according to the number we give our file name. Those other files look like they're for programmers to work on and not regular users.
I suppose that's what new users think about editing the old menu.lst file though at first. Maybe in time we'll come to understand more and it'll seem easy.
All I did was make a 'dedicated GRUB2 partition'. When GRUB2 isn't part of an operating system it's okay to edit the grub.cfg file any way we like. It's only when it is built in to an operating system that it's controlled by those other files.
I don't know where to go to find out more, I have googled and searched and pieced together fragments of information from here and there and all over the place. Googling is time consuming and it's tiresome when a person isn't able to find anything much. I guess we'll have to work on gathering as much info as we can and then wait to see what the developers are doing. I am expecting a lot of changes, and probably there'll be some surprises. Playing around with GRUB2 and doing our own experiments is a good way to learn. It seems as if we'll need to be patient but [/FONT][FONT=Bitstream Vera Sans Mono]persistant[/FONT][FONT=Bitstream Vera Sans Mono]. 
[/FONT][B][URL="http://www.google.com.au/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fwiki.archlinux.org%2Findex.php%2FGRUB2&ei=2alISuCXAcSCkQWvleT5CQ&usg=AFQjCNHYPBIYX4qPVQtg9AsxuRiR1fWE_g&sig2=gqvgq75m6LHzdGlBIROaXA"]
[/URL][/B]

---

### Post by Jags_FL on 2009-06-29
Thanks for the info :)

'dedicated GRUB2 partition' sounds a good idea, next time I'm gonna format the HD I'll go for it.

---

### Post by Herman on 2009-06-30
> If you know any place / Wiki to read on GRUB2, please let me know. 	
Here's a thread I just found that you might also like, [GRUB2 Theming]("http://ubuntuforums.org/showthread.php?t=1182436"). 
There's going to be a new 'SUM' (Start Up Manager), for editing the files that are used for generating grub.conf. See page5, post #45.
> 'dedicated GRUB2 partition' sounds a good idea, next time I'm gonna format the HD I'll go for it. 	Yes, or a GRUB2 USB would be fun. I think we'd be able to install GRUB2 to a partition or USB with the grub-install command fairly easily.

---

