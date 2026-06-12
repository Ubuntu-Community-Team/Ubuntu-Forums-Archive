---
title: "Multiboot USB..."
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by OpEn_SoUrCe_RoCkS on 2010-09-01
Hey all? Big one for you...

I have a 16GB USB Flash drive.

I want:
Ubuntu 10.04 installed on it
The ability to choose, at boot, whether I boot Ubuntu, or some rescue utilities that i will also put on there
Ideally I would like to be able to keep them in iso format simulate a cd on the fly...

But all my attempts have not panned out, resulting in either kernel panic after some editing of the grub files (:D) or simply nothing...

What is the best way of accomplishing this? 
Using what? 
Grub2? Grub4DOS? 
Which should I install first ? 
Which one chainloads the other more easily???

I am going half crazy over all this... It shouldn't be this hard... Oh well. I've got time. :popcorn:

Any help is going to be appreciated. .
Thanks!

---

### Post by oldfred on 2010-09-01
With a 16GB flash you just do a standard full install of Ubuntu as if it is a second drive. Just be sure to install grub using the advanced button to the USB drive.

Then you can install as many ISO as you want and loop mount them.

[http://members.iinet.net.au/~herman546/p24/022f.png](http://members.iinet.net.au/~herman546/p24/022f.png)
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1 
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

Then you can install ISOs. You already have grub2 installed and just need to copy the ISO to a location and modify grub.cfg to loopmount them.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)


A few ISOs do not loop mount. If you only wanted a USB flash with ISO this script automates it. But you can look at script to see how to mount any of the ones it will set up.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644) 

If you put them in a different partition then it is more like a hard drive.
Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864&highlight=ISO](http://ubuntuforums.org/showthread.php?t=1535864&highlight=ISO)

---

### Post by OpEn_SoUrCe_RoCkS on 2010-09-01
Thanks for the quick answer! Believe it or not, i had actually read through pretty much all of the pages you lniked to... Still can't get it to work though... 

I think the best possible setup would be this one:
Ubuntu on partition (grub2 on flash drive)
Unetbootin on other partition 

Grub2 calls on Unetbootin when I ask it to, otherwise boots into Ubuntu...

Is it possible to boot Unetbootin from within Grub2?
What does the menuentry look like?

Thanks

---

### Post by oldfred on 2010-09-01
Not sure you can boot Unetbootin from grub2, although it seems grub2 can boot just about anything.

I installed several Ubuntus, gparted, system rescue, parted magic and one or two other ISOs to my 4GB flash drive which I also use to install since it is real easy just to copy the ISO to the flash, update grub.cfg and install.

I then installed Ubuntu to a 16GB flash with two partitions, root & /home. It had enough room left I realized I could add the ISOs to that flash drive also but have not yet.

What issues are you having? A few seem to have flash drives that just do not seem to want to work. I used no name MicroCenter generic flash drives and they work. Does the grub2 install and let you boot the flash?

---

### Post by OpEn_SoUrCe_RoCkS on 2010-09-03
UPDATE: 

I now have a working setup... Sort of.

5GB storage on first partition of drive.
Ubuntu installed on second partition of drive.
And Grub4DOS on last partition of drive, calling different live ISOs on that partition...

I've gotten Parted Magic, Offline NT Password and Registry Editor, Ophcrack, UBCD, and F-Secure AV to work... 

Now I'm experiencing problems with Knoppix, BitDefender Rescue CD (which is based on Knoppix, so not relly surprising...), Kon-Boot, and Backtrack 3.

I really want the BitDefender... 
And Kon-Boot would be cool too, but something tells me that Grub doesn't like the idea of booting a floppy from an ISO...

Backtrack has a problem with being not contiguous, so I should be able to fix that...

But anyone have ideas for BitDefender and Kon-Boot?
And do you have any more "Rescue CD"-type ISOs that you particularly like?

---

### Post by C.S.Cameron on 2010-09-04
For automated grub2 iso install check:
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)


Oops, I think Old Fred mentioned this one already.

---

### Post by OpEn_SoUrCe_RoCkS on 2010-09-11
Hey guys!
I finally got it right!

I think I'm gonna do a tutorial soon on Multibooting a USB with ISOs and Ubuntu using Grub2 and Grub4DOS.
It's not that hard, but it's also not very well documented...

Thanks for all your help!

---

