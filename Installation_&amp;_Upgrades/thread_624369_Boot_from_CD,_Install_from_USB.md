---
title: "Boot from CD, Install from USB"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by texasjoehotdog42 on 2007-11-26
I have an old laptop whose CD rom works for booting up the 7.10 Ubuntu CD, but always chokes on the install. So, what I want to do is use the CD just to boot the computer, then once in the live mode, plug in a USB flash drive that has a carbon copy of the install/live CD on it and have the installer point to that for all the install files. I would just have the computer boot from the USB, but it doesn't support it. It seems like this should be a fairly simple thing to do, but I really don't know how. I looked at this on the wiki: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick), and that is almost what I want to do. Another way I could do it is with a network install, but my internet is so slow here that I think it would be more trouble then it's worth. If anyone can help, that would be great.

---

### Post by Herman on 2007-11-27
:) Hello texasjoehotdog42, 

First, consider the possibility that your problem might not be your CD drive, but lack of memory. 
The easiest way to try first would be to get a [GParted -- LiveCD]("http://gparted.sourceforge.net/") and use that to partition your disk, being sure to make a swap area of up to 1.0 GB on your hard drive.
If your computer has around 256 MB of RAM, and you have a swap area made on your hard disk, the Ubuntu Live CD will find that automatically and use that instead of extra RAM and your install from the CD will be able to proceed as normal.
WARNING: Back up your files first, because a faulty CD drive can cause problems with disk partitioning programs running from a CD, which can cause loss of access to your data in the way you are used to, so you might then need to rescue your data.

The 'Alternate' CD will be easiest if you have much less than around 256 MB of RAM. You can still use the 'Alternate' CD with as little as 64 or even 32 MB of RAM, see my sig link for more details.


Either of those two above ideas will work if the problem is lack of RAM, but if the problem really is a faulty CD drive, you can try something from this list underneath, ordered from easiest to hardest.

Clean the optical lens of your CD/DVD drive with a QTip (cotton bud), dipped in a little denatured alcohol (methylated spirits), and try again. If the CD/DVD drive is the kind that has the lens attached to the CD/DVD drawer so it slides out where you can easily reach it, this will be easy. If the CD/DVD drive lens is built in and the machine will need to be dismantled to reach it then this idea might be too hard, but many times this is all that is needed to fix a faulty CD/DVD drive.

If you already have your .iso file that you made the CD from in your computer somewhere, (like in the Windows partition for example), you can use your [GParted -- LiveCD]("http://gparted.sourceforge.net/")
 to partition your hard disk for you, and also make an extra partition of around 1.0 GB in size somewhere on your disk, maybe near the end if you like. You can copy the CD files to that and boot it as a LiveCD and install from it.
That's just a little easier than using a USB disk but it works almost the same way. The advantage of doing it this way is you don't need to worry about whether or not your computer will be able to boot a USB after you go to all the trouble of setting one up.
Here's a link about it, [Installation/FromLinux.]("https://help.ubuntu.com/community/Installation/FromLinux")
 You will be able to use your Live CD to mount your partition already containing the .iso file and mount the .iso file in the Ubuntu Live CD to copy the files to the partition you will use to install from. I can help you with that, 

Finally, the how-to you have chosen,  [https://help.ubuntu.com/community/In...n/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick"), is an excellent how-to, but you are right to ask for help with it, it's not really something easy to accomplish for even fairly advanced users without help.

An easier way to do the same thing if you just want to use it for installing Ubuntu would be to use the [Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux")
 ohw-to but copy the files to the USB disk instead of a partition and try to boot it with GRUB. You should be able to boot it from a [Super Grub Disk]("http://sgd.benjamin-butschko.de/")
 with a little help.

If you want to go more advanced, but only a little bit, you can try this how-to by me, [HOW TO make a USB Disc with Ubuntu LiveCD and Super Grub Disc in it.]("http://ubuntuforums.org/showthread.php?t=575406&highlight=herman")
That way you'll have [Super Grub Disk for USB]("http://supergrub.forjamari.linex.org/?section=download#usb") available for the extra purpose of helping with any booting problems you might ever have too, so you'll be accomplishing two things at the same time.

Even more advanced, (only one step harder than the how-to you chose), I was just experimenting with this type of thing last weekend and was able to make a USB disk with the Ubuntu Live CD in it with  'persistence', (you can make changes or install software and it will be remembered over reboots, unlike with a normal live cd, and you use Syslinux as the bootloader. See this thread here,                                                     [Bootable USB Pen Drive]("http://ubuntuforums.org/showthread.php?t=611763")             .

If you really want to try with the how-to you specified, please check that your computer can boot from a USB disk first by testing it with [Super Grub Disk for USB]("http://supergrub.forjamari.linex.org/?section=download#usb") and see if that will work before we got to the effort of copying the Ubuntu CD to the USB flash disk.

You might still need to make a swap area before the install will work if you only have around 256 MB or memory.

Let me know what you decide to do and how you get along.
Regards, Herman :)

---

### Post by texasjoehotdog42 on 2007-11-27
Thanks a lot for that in depth response. I'm not at home right now so I can't try any of this yet, but as soon as school is over I will have to try a few of those. I was talking to my computer science teacher a few min ago, and he suggested that if I put all the install files on the USB drive, and boot from the CD, I should just be able to mount the flash drive, and run the installer from there, which is basically what I wanted to do. If you can see any reason why that wouldn't work, please let me know. If I can't figure out how to do any of these on my own, I might just do a network install from school as their connection is a lot faster then my home one. Thanks a lot.

---

### Post by Herman on 2007-11-28
:-k Hmmm, well your computer science teacher should know best, so maybe it's me who doesn't quite understand. I'm not sure.

If you copy the files from the Ubuntu Desktop Live/Install CD, you can either a spare partition in your hard disk or a USB drive.
Then you can boot the partition or the USB drive as if it was a live CD, and perform an installation if you want.

If you can mount the flash drive and run the installer from there, I believe you, it must be some advanced method I haven't read about yet. 

Are you sure your computer science teacher didn't say 'Use the Live CD to *boot* the USB flash drive?

I suppose the only way to really know is to go ahead and try whatever it is you want to do and see what happens.

Regards, Herman :)

---

### Post by texasjoehotdog42 on 2007-11-30
Well, that was just an idea he was throwing out there, he wasn't sure if it would work or not. He doesn't have a lot of experience with doing weird installs of Ubuntu, just fairly normal CD based ones. I was mainly just wondering if anyone had tried it and if it worked. 

I've been kinda trying to boot from an external USB CD rom drive. I have made a GRUB boot floppy, and don't know were to go from here. Another option I have is to copy the install CD files from a different computer to the HD ona different partion.  I have a desktop running 7.10 with a P4, and I have a laptop HD connector to IDE adapter so I can copy files to it from the desktop if need be. I also have a laptop HD connector to USB adapter and an iMac running Leopard, so any suggestions for either setup would be nice. Thanks again.

---

### Post by Herman on 2007-11-30
> I've been kinda trying to boot from an external USB CD rom drive. I have made a GRUB boot floppy, and don't know were to go from here.
Another option I have is to copy the install CD files from a different computer to the HD ona different partion. I have a desktop running 7.10 with a P4, and I have a laptop HD connector to IDE adapter so I can copy files to it from the desktop if need be. I also have a laptop HD connector to USB adapter and an iMac running Leopard, so any suggestions for either setup would be nice. Thanks again. I would think the easiest idea would be to remove the hard disk from the old laptop and plug it into another computer for now.
Then make a small partition in it and copy the Ubuntu 'Desktop' Live/Install CD's files into it, as explained in this link,[ Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux")
If you have the .iso file in the computer you use, you can follow that how-to and mount your .iso file, even if you have no Ubuntu operating system yet, because you should be able to use the LiveCD you already have made for the operating system, and mount the file system that contains the .iso file. 
The follow the link's insrtuctions about how to mount the .iso file, and copy the files to your small partition in your other hard disk, which you will also need to mount first.
You will probably need to modify those commands (file paths) to get them to work in your particular situation.

Then you will be able to put the hard drive back in the laptop again and boot your installer partition with a [Super Grub Disk CD]("http://sgd.benjamin-butschko.de/")
You would need to use  [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") from the Super Grub Disk CD to enable you to type in the right commands as given in the how-to,
```
root (hd0,0) # or whatever the right partition number will be #
kernel /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw
initrd /casper/initrd.gz
boot
```That way you will be performing the installation in the machine that the operating system needs to be set up for.


Another way to do it would be to just plug the hard drive from the old laptop into another machine and perform the installation from the other machine as if the hard drive was part of the other machine.
Just try to install GRUB to the right hard disk when you get to that part of the installation. If GRUB installs to the wrong hard disk's MBR, it won't matter, don't worry about it, you'll be able to restore the MBR of the other computer easily by one of the methods list in this page, [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")
When you put the hard disk back inside the laptop, Ubuntu would be set up wrong for the old laptop, it would be set up for the other computer's hardware. You could easily configure it by hand and get it working right. 
You would need to boot it with  [Super Grub Disk]("http://sgd.benjamin-butschko.de/") probably.
I would expect it to boot to a command prompt and not a GUI.
You'll need to run 'sudo dpkg-reconfigure xserver-xorg (for video, keyboard & mouse drivers, and associated settings) for the Xserver, [Xserver Page]("http://users.bigpond.net.au/hermanzone/p7.html").

Then edit your /boot/grub/menu.lst so it will boot by itself from then on.

You might need to re-install GRUB.  You can use Super Grub Disk to do that too.

Also edit your /etc/fstab file and delete entries for any file systems (partitions) that were included from the other computer. Make any other necessary corrections.

I think after that if there isn't anything I've forgotten, you'd be all set. It would just be the normal post-install stuff that you would be able to do at your own leisure. (Well, actually, you can do the whole thing at your own leisure, of course).

It would be about the same amount of work no matter which way you decide to do it, so you might just want to flip a coin to decide.

Regards, Herman :)

---

