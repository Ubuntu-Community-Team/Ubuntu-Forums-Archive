---
title: "Install FROM hard drive?"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by Sarke on 2007-10-13
Hi, I have an old laptop that currently is running Win XP on it and I want to install Xubuntu.

The problems are as follows:

- I can't use the regular LiveCD or the alternate cd (text mode) because the CD drive will not work once the install loads up.  It says it can't mount it.

- I can't use the netinstalls because the wireless USB adapter doesn't work in the installer, and if I try to install from Windows with Wubi it doesn't let me because I don't have 4 GB free.


What I have to work with:

- A fully functional Win Xp system
- Both the CD and the wireless work fine in Windows.
- No floppy.
- Bootable CD.
- No bootable USB.
- FreeDOS and Linux-from-Scratch both boot fine from the CDs.
- I can also get into the virtual command prompt from the alternate CD.
- I don't plan on keeping Windows installed on the machine.


So, how do I do this?  Is there a way to copy the files to the hard drive in Windows (I have partition magic lying around somewhere I think), then boot up and install them from there?

---

### Post by Herman on 2007-10-13
Hello Sarke,

Can you boot a [GParted -- LiveCD]("http://gparted.sourceforge.net/") ?

Can you boot a [Super Grub Disk]("http://supergrub.forjamari.linex.org/")?

I think I have an idea, based on this how-to, [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

You would be able use a GParted LiveCD to make a small partition for your install, that shouldn't be any problem.

Then you'd mount your Windows partition and mount your .iso file in GParted LiveCD ready to copy the files from the .iso file.
Then you'd mount the new install partition and transfer your Ubuntu files into it.

You'd reboot and swap CDs for the Super Grub DIsk.
You'd get a Super Grub DIsk [Command Line]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").
Then you would type something similar to the following into Super Grub's CLI, (but replace the example partition numbers with your own if applicable),
```
root (hd0,1)
kernel /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw
initrd /casper/initrd.gz
boot
```That should boot the Ubuntu files in your install partition and they should run as if they were a LiveCD. From there you will be able to do whatever you like.

Based ion that excellent how-to I already linked you to that should work, I have tried that how-to out the normal way. I have also tested it with a few variations of my own too and it works fine working from an installed Ubuntu operating system. The trick will be getting it to work using GParted LiveCD for your Linux operating system. You will need a moderate amount of Linux skills or some detailed step by step help probably. Or maybe you can figure it out okay already?

What do you think?

Regards, Herman  :)

---

### Post by rsambuca on 2007-10-13
What are your system specs?

---

### Post by Sarke on 2007-10-14
Herman, thanks for the informative post.  I can run both GParted and SGD.  I also tried Knoppix, but it has the same problem as the ubuntu installer.  It mounted hda ok (the hard drive), but when it tried to mount the CD as hdc it failed and the CD didn't work like the other times (CD eject doesn't even work).

I've created  1GB ext3 on the hard drive now and I'm in the process of trying to do what you suggested.

> **rsambuca said:**
> What are your system specs?

It's a Dell Latitude CPi D266XT, P2 266MHz, 128 MB ram, 6 GB hd.
[http://support.dell.com/support/edocs/systems/pmojav/specs.htm](http://support.dell.com/support/edocs/systems/pmojav/specs.htm)

---

### Post by Pumalite on 2007-10-14
Try: Zenwalk, DSL or Puppy.

---

### Post by rsambuca on 2007-10-14
Definitely the LiveCD will not work, since you don't have enough RAM.  With those specs, I think your best bet may be a minimal installation.  [The instructions are here.]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

---

### Post by Herman on 2007-10-15
Sarke,
I have been trying to do the same thing as you, and taking rsambuca's excellent advice into account, I am trying with the 'Alternate' CD, hoping to be able to give you exact instructions, but so far I haven't been successful.

I am able to boot GParted LiveCD and make a small partition for the installer files, and mount Windows 98 and mount the Ubuntu Alternate .iso.
(To simulate your situation I have placed my gutsy-alternate-i386.iso in Windows 98 SE as if I downloaded it there).
I have mounted the install partition and copied the files from the .iso to the partition.
Then I rebooted GParted LiveCD and got a GRUB command line form the GParted LiveCD (it uses GRUB to boot with too), and I have booted up and started the installer.

I am using my [PC Chips 'BookPC']("http://herman543.googlepages.com/bookpcgetsbigpowersupply2") with 400 Mhz Celeron CPU and 64 Mb RAM (I have more but I took some out for this experiment). It isn't the lack of RAM that is stopping me, the 'Alternate' CD is working fine on that amount of RAM.
It begins okay, detects the low RAM and goes into low memory mode, then takes me through keyboard and language selection and so on until it gets to '[!!]' Detect and mount the CD-ROM', and that's as far as I can get. I have tried twice, I'm not sure how to get around this problem.
It seems as if it's looking in the CD-ROM drive for the CD, that wasn't a problem for some reason when I used the same method with the Ubuntu Live CD installer. I know that how-to does work with the LiveCD installer because I have installed that several times already. 

So looks like the 'Alternate' CD might not be able to be used in this manner, or there is something more I have to learn to get it to work. 

How did you get along?

It looks like Pumalite's advice might turn out to be the best. 

Regards, Herman :)

---

### Post by Sarke on 2007-10-15
Both DSL and Puppy booted, but both had problems with the graphics.  It's something that I could probably sort out, but meh.

I also tried installing Zenwalk, but it failed during install as well.


Herman, I already tried the alternate install CD from the HDD, and yes, it still looks for the CD-ROM.  I tried the regular live CD as well, but that froze once it had booted up and wouldn't load the installer.


What I ended up doing was trying an old Ubuntu 5.10 CD I had lying around, and that worked!  It didn't have the CD drive becoming inoperable as the other ones did.  Maybe the newer installers try to do something with the CD-ROM drive that makes it power down.


So now the problem is to update my Ubuntu 5.10 to Xubuntu 7.04.  First I need to get the D-link wireless USB adapter to work.  It's detected, but I'm not sure how to connect it.



As for installing Ubuntu from the hard drive, it doesn't seem like it wants to do that.  It would be really useful if the alternate install offer the option to just specify the location and skip the CD-ROM detection.

---

### Post by Herman on 2007-10-16
>  I already tried the alternate install CD from the HDD, and yes, it still looks for the CD-ROM. I'll try experimenting with that in another computer and see if it's any different, but maybe we can only use the Live CD to install from hard disk witt and maybe the 'Alternate' CD isn't suitable for that, I'll see if I can find out anything more about that though, it might take time.

> What I ended up doing was trying an old Ubuntu 5.10 CD I had lying around, and that worked! It didn't have the CD drive becoming inoperable as the other ones did. Maybe the newer installers try to do something with the CD-ROM drive that makes it power down.
 I don't know. 
One thing I forgot to suggest to you, but that I have been advising people a lot lately and does help some people (it helped me), is to  try cleaning the optical lens in the CD/DVD drive with a Qtip (cotton bud) and some denatured alcohol (methylated spirits). If you have a type of CD/DVD that has the optical lens sliding out with the CD/DVD drawer, it's easy. Most CD/DVD drives need to be taken apart to clean the lens, which can be a big job.

> So now the problem is to update my Ubuntu 5.10 to Xubuntu 7.04. First I need to get the D-link wireless USB adapter to work. It's detected, but I'm not sure how to connect it. I'm sorry, I wish I could help, but networking is not my strongest field of expertise, you would be best advised to start a new thread about that in the Networking and Wireless section of the forum and try to attract the attention of someone who knows more about the subject than I do.
Here's how I got help with mine, [Setting up my Acer Aspire Notebook for Wireless Networking in Ubuntu]("http://users.bigpond.net.au/hermanzone/p11.htm#wireless_network_configuration")

> As for installing Ubuntu from the hard drive, it doesn't seem like it wants to do that. It would be really useful if the alternate install offer the option to just specify the location and skip the CD-ROM detection.Yes, I agree. I wonder if it's something simple to change to enable that or of it's very complex, or if it's something I'm doing wrong myself. That how-to I linked you to earlier was really for using a Live CD, nit the Alternate CD, but I changed the boot options to suit the Alternate CD myself, so I'm doing something outside of what that website was really about. Normally these CDs use Syslinux as their boot loader, and when I look in the configuration file for that inside the CD, I can see a list of different entries with various boot options there.  I'm trying to use GRUB, which should be okay but I should study and learn more about boot options, maybe that will help somehow.

I was wondering if it would help some people to put a CD in the drive and see what happens, maybe in some computers the CD doesn't boot, but it still might be possible for the CD to be read, and might help to complete the installation then. I would need to repeat the same experiments again and try that. However, that might not prove much, because my computer has a working CD drive anyway.

Anyhow, congratulations and well done getting Ubuntu installed at all, and good luck updating it to the latest and greatest! :)

All the best,
Regards, Herman :)

---

