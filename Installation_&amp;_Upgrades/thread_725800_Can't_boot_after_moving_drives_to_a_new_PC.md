---
title: "Can't boot after moving drives to a new PC"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by MPH on 2008-03-16
I moved my drives with.the 7.10 desktop installed to a different PC.  Both PCs use Pentiums but the drives are connected on the new PC to a Highpoint IDE/ATA-compatible SCSI chip built into the motherboard.  After the POST finishes while booting, "GRUB" appears on my monitor and the system freezes.

When using the 7.10 Live CD, I can see my drives and folders and I have read-only access to my files.  When I ran "gksudo nautilus" from the terminal, I could edit and save files on my hard drive.

What can I do so that I don't have to reinstall 7.10 and lose my Samba setup, etc.?  -Thanks!

---

### Post by Peter09 on 2008-03-16
There is an application disk called Supergrub which I believe is capable of identifying non-booting operating systems and setting them up. I have never used it but it might be worth investigating.

PC

---

### Post by MPH on 2008-03-16
I used the latest version of Supergrub found at [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) and downloaded the latest CD-ROM ISO (0.9677) and burnt the ISO onto a CD.

The HELP on the ISO wasn't much help to a Linux Noobie so I tried what I thought was the most conservative approach... and I don't remember what option I selected but I think it said "boot".  It booted my system but said it couldn't detect my monitor's specifications.  It gave me the option to enter ViewSonic from a list of brands and then enter PS790 from a list of models.  The login screen looked OK but the resolution of the 7.10 desktop was 800 X 600 even though I selected 1152 X 870 for the PS790... like I usually use.  The upper icon panel was almost full at 1152 X 870 so at  800 X 600, the rightmost portion of the upper panel was all that showed so I couldn't even see the application menu to the left.  I created a new icon panel with the application menu and tried to change the screen resolution... but the only options were 800 X 600 and 640 X 480. :( I rebooted without the CD but Grub still didn't work.

I rebooted and tried the Supergrub CD again.  This time I choose GNU/Linux ==> "Fix *yadda  yadda  yadda"*.  After it finished, I rebooted without the CD and 7.10 booted with a few new Grub messages appearing.  The login looked OK but the desktop was totally skewed like the horizontal sync was off so that no text was readable, and icon and even larger images on the desktop were too distorted to recognize.  I stopped with Supergrub there.

After this, I couldn't recommend Supergrub to anyone.  The Supergrub's help sorta says "trust me"... but I shouldn't have.

I previously tried the first step offered in [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) but that didn't work... However, some of the sebsequent steps in that thread look more promising.  I also imagine xorg.conf is screwed up... I hope supergrub kept the previous version.

---

### Post by Herman on 2008-03-16
[Xserver Page]("http://users.bigpond.net.au/hermanzone/p7.html")   sudo dpkg-reconfigure xserver-xorg (video, keyboard & mouse drivers, settings)

Your problem has nothing to do with Super Grub Disk.
Super Grub Disk helped you boot and to restore GRUB, then I'm guessing   you messed up your own video driver settings, or they are still the old ones from your old computer. 
Ubuntu does keep a copy of your old xorg.conf file, so don't worry about that, but what you need to do is to boot again and run sudo dpkg-reconfigure xserver-xorg and that should fix it somewhat. [Xserver Page]("http://users.bigpond.net.au/hermanzone/p7.html")
You will also probably need to edit a few other files like /etc/fstab as well before you'll get your system working properly.

---

### Post by MPH on 2008-03-22
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) gave me the guidance I needed to fix Grub by running the Ubuntu 7.10 Live CD. Specifically, I followed the instructions that followed Catlett's quote that began:

> Mine was a slightly different story. I couldn't get grub to find the stage1 file or even recognize my drive. So I borrowed some knowledge I picked up while using Gentoo:
 In my particular situation, I mounted **/dev/hda1** instead of **/dev/sda6**.  I determined the correct device id to use for my PC by running LiveCD's Parttion Editor to view my 3 hard drives and to see Ubuntu's way of identifying them.

> Your problem has nothing to do with Super Grub Disk.  Super Grub Disk helped you boot and to restore GRUB, then I'm guessing you messed up your own video driver settings, or [COLOR="Red"]they are still the old ones from your old computer[/COLOR].

_Herman_, you were correct.  Xorg.conf was still configured for the previous video card. Thank you!

---

### Post by adrian15 on 2008-03-25
> **MPH said:**
> 
After this, I couldn't recommend Supergrub to anyone.  The Supergrub's help sorta says "trust me"... but I shouldn't have.

I am glad you have understood that this is not a super grub disk problem but a video card one. 

I am not lucky... if Super Grub Disk does not work for a particular case people do not recommend it for anyone! :( How can they be Super Grub Disk experts in such a short time? ;)

adrian15

---

### Post by MPH on 2008-03-25
> How can they be Super Grub Disk experts in such a short time? 

Indeed, I see your point, Adrian!

My system was inoperable and my only thoughts were to make it operable again rather than becoming a Super Grub Disk expert.  I think I spent all of 10 minutes with Super Grub Disk... not enough time to even qualify as a n00bie.

The reason I abandoned using Super Grub Disk so quickly was the concern that if the version of Grub on the Super Grub Disk didn't match the version of Grub that my version of Ubuntu uses, it might not work properly.  Hence, I decided on the spur of the moment to find a solution based on using the LiveCD to avoid the version issue.

I have since learned that fixing Grub for an intact partition is amazingly simple from a LiveCD's terminal...
> sudo grub
find /boot/grub/stage1 [COLOR="Green"]{to discover my drive and partition, (hd0,0)}[/COLOR]
root (hd0,0)
setup (hd0)
quit

Unfortunately, I since discovered that the HighPoint HPT366 ATA/66 controller chip on my Soyo SY-6BA+IV motherboard were corrupting Grub every time I used the HPT366's BIOS to switch boot drives.  Fortunately, Grub stage 1.5 is optional and by removing it, the corruption problem disappeared.

> I am not lucky... 
Ditto here... but if it weren't for bad luck, I'd never recognise the few occasions when  I am lucky. :)

---

