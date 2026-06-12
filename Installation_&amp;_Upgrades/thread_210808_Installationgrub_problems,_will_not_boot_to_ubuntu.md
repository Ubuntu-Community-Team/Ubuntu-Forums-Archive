---
title: "Installation/grub problems, will not boot to ubuntu"
date: 2006-07-07
forum: Installation &amp; Upgrades
---

### Post by atrophic on 2006-07-07
The short of it, when booting the ubuntu partition I get an operating system error.

The long of it...

I first tried installing with the live cd, but it would not start the installation (double-clicking) install did nothing.  Running the command manually gave some kind of desktop file not found error.

I installed from the alternate cd.  I have 4 hard drives... at this time it was SATA1 (xp), SATA2 (to be formatted for ubuntu), and IDE1/2 (ext3 storages).  I partition the SATA2 for 40GB /, 3GB Swap, remaining ~120GB /home.  Installation goes fine, it comes up with grub stuff, finds xp, asks to install itself to the first hard drive and appears to do so.  I think it misunderstood first hard drive though as the computer went straight to windows on reboot.  I fudged with the grub device.map and menu.lst files (from windows with an editor that saves in the unix format still) so I could switch the sata drives around and have ubuntu be the first one, then rebooted.  I get "Operating System Error."  Yay.

I use the live cd to burn GAG to a cd, set it up to list both the ubuntu and windows partitions.  When I try to boot the ubuntu one it says boot sector not found or invalid.  Windows still works fine.

Okay, I try a different live cd (same 6.06 LTS desktop image, first image just didn't burn right apparently).  Installation GUI comes up this time.  I choose manually edit partition table, and I set it up to do the exact same thing I did with the alternate cd, formatting the 3 appropriate partitions before reinstalling.  It doesn't come up with anything about grub, but I figure I can set that up after I boot into ubuntu.  But on reboot I still get an operating system error.  It apparently still configured grub though.

[quote="device.map"]
```

(hd0)	/dev/hde
(hd1)	/dev/hdf
(hd2)	/dev/sda
(hd3)	/dev/sdb

```
[/quote]

[quote="menu.lst"]
```

# lotsa comments removed
default		0

timeout		10

#hiddenmenu

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-386
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Microsoft Windows XP Professional
root		(hd3,1)
savedefault
makeactive
map		(hd0) (hd3)
map		(hd3) (hd0)
chainloader	+1

```
[/quote]

XP is on (hd3,1) because of whatever partitioning dell does automatically for their dell utilities thing.

hd0 and hd1 are not bootable.  The bios is set to boot to the sata drives first.  Before this installation I moved them around so sata1/2 were hd0/1 and the IDEs were hd2/3, but I really don't claim to know what I was doing there.

So my question, how do I get grub to actually load at boot, and is it configured correctly when it eventually decides to load?

---

### Post by Herman on 2006-07-07
atrophic,
You can install GRUB anywhere you want by using 'Rescue a Broken System' mode with the 'Alternate' install CD. 
[*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub") to see that illustrated.

That means you should be able get GRUB installed in your MBR on your first hard disk where you need it. (Whichever one is your first hard disk now,)  I think it is being installed to the first sector of some other hard disk by mistake. (Your first IDE drive, I suspect, which is a data drive).  Once you have GRUB installed on whatever your BIOS thinks is your first hard disk, GRUB should load at boot for you.

If you still have trouble, you could also run through that for a second time and install GRUB to a blank floppy disk as well (fd0). That will mean, we (you) can use GRUB from the floppy disk to:
(a) boot Ubuntu from the GRUB floppy disk GRUB Menu, and/or,
(b) use [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") from the floppy to find out how grub sees your operating systems and drives. It should be simple to experiment with GRUB's CLI until we get Ubuntu to boot, then we can look at editing /boot/grub/menu.lst if it needs it.

> I use the live cd to burn GAG to a cd, set it up to list both the ubuntu and windows partitions. When I try to boot the ubuntu one it says boot sector not found or invalid. Windows still works fine. GAG Boot Manager just needs a boot loader like GRUB or Lilo installed in the first sector of your Ubuntu partition in order for it to boot Ubuntu. It's up to you, but you could also go through the same 'Rescue a broken system' process again for a third time if you want to install GRUB to the first sector of your new Ubuntu partition, so it will be then bootable with GAG Boot Manager, just to make sure. Actually I use and recommend LiLo for the first sector of our Ubuntu partition, since if I have to boot with GAG because of some mistake or failed experiment I made in GRUB's menu.lst, it makes sense to use a different bootloader there.

I'll be lurking around for the weekend, I'll keep an eye on this thread in case you need more help, Regards, Herman :D

---

### Post by atrophic on 2006-07-08
Hermon, thanks a ton for your response.  I'm sorry I didn't get a chance to post here that I got it working before now to save you the effort.  A lot of what you said is what I had to end up doing though.  For the sake of anybody with a similar problem, this is how I resolved it.

Like Hermon, I guessed that the automated grub install was put on my IDE MBR instead of the appropriate SATA one.  So my task was to get it on the SATA one.  Using a combination of solutions to other problems similar problems posted on the forums I got it solved.  First I unplugged my IDE drives, as they were only used for data.  This left my unbootable ubuntu drive as SATA1 and my xp drive as SATA2.  I went into the live cd and played with grub's Command Line Interface.  From memory (aka, verify this elsewhere before you try it) I did this:
```

user@box:~$ sudo grub
grub> find /boot/grub/stage1
 (hd0)

grub> root (hd0,0)

grub> setup (hd0)

grub> quit

```

Whatever the find command shows on the next line is the HD you use in the next commands.  To setup grub on the first sector (what GAG would need) you'd use setup (hd0,0) instead, I believe.

Anywho, that sets up the SATA1 drive for booting with grub.  I restart and I get the grub bootloader, yippee.  I get into ubuntu, install all available updates, then shutdown to plug the IDE drives back in.  I think updating the kernal made grub change its config, because it changed from hd0 to hd2 (an incorrect mapping) so again ubuntu wouldn't boot.  I solved this by just going into windows instead, accessing my ubuntu install with an ext2 driver for windows, and using a text editor (that preserves unix formatting, just in case) to change grub's menu.lst again.  Once I did this I was in ubuntu for good.

Finally, a working ubuntu/xp system on seperate drives.  /me does cartwheels

Thanks again to Hermon for his help.  And to anyone in the same boat as I was in, I'm sorry.  Stick with it and you'll be rewarded though.

Also, I really like the idea of adding lilo to the first sector of the ubuntu partition, I think I'll do that just in case grub ever explodes again.

---

### Post by Herman on 2006-07-08
Hello, atrophic, congratulations on overcoming your booting problems, and well done too! :D Also, thanks for sharing how you did it. 
I'm was wondering myself how to install GRUB from the new 'Desktop' Live/Install CD. some of the the re-install GRUB methods that used to work well for Breezy don't seem to be effective anymore with Dapper. So you used a GRUB shell and the command grub> setup (hd0) eh? I'll give that a run myself in a few minutes, it is one of the things on my 'to-do list' for this weekend, so I have learned something from you, thanks.
> Also, I really like the idea of adding lilo to the first sector of the ubuntu partition, I think I'll do that just in case grub ever explodes again. Here's a link to explain the easiest way to do that,  [Install Lilo from terminal.]("http://users.bigpond.net.au/hermanzone/p12.htm#Install_Lilo_from_terminal")
If you can use GRUB's Command Line, you will never have another booting problem for the rest of your life though, so I think all your problems will be behind you now. I'll bet next time I see you posting about a boot issue it will be to help someone else! All the best! Regards, Herman :D

---

### Post by ekravche on 2006-07-14
Modifying the device map to represent the correct drive order fixed my issue with this thanx! 
**device.map**
[QUOTE=]

Code:

(hd0) /dev/hde 
(hd1) /dev/hdf 
(hd2) /dev/sda 
(hd3) /dev/sdb

[/QUOTE]

---

### Post by atrophic on 2006-07-17
ekravche, glad to hear it helped somebody else (:

Herman, I used your guide to install lilo (and I'm pretty sure that's the guide I was using for GAG before I even posted here too).  Very useful information, thanks again.

---

