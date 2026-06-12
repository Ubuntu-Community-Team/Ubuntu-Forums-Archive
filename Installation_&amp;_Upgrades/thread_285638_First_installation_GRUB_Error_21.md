---
title: "First installation: GRUB Error 21"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by SanguineIllusion on 2006-10-27
I have somewhat limited linux experience (I used redhat a while ago) and decided today that I'd go ahead and set aside some space on my main drive and give Ubuntu a shot. I thought I'd be done in an hour or so and all would be well, but boy was I wrong. 

Heres my situation: I have 3 SATA hard drives. I have 2x200gb maxtors that are RAID-0 through my mobo chipset (nforce4) and 1 primary SATA drive, a 320gb seagate. I have windows xp installed on the seagate and because I heard some horror stories about installing ubuntu on nf4 RAID, I shrunk the XP partition down by 20gb for Ubuntu.

I chose to manually edit the partitions during installation because the automatic way only gave the the option to completely format the drive, which I cannot do. I set apart about 1GB for swap and 19GB for /. The first time I installed Ubuntu, it seemed to go off without a hitch, but upon rebooting, there was no boot loader and it just went straight to windows.

I tried a couple more times and now I believe that I have ubuntu installed, but grub not only can't load it, but can't load windows XP :mad: No matter what I select, I get Error 21: Selected disk does not exist.

My 2x200gb drives show up during installation as /dev/sda and /dev/sdb, and I don't touch them. The drive I want ubuntu on is sdc and the root's partition is sdc3. Accordingly, grub seems to be set to boot from (hd2,2) for ubuntu and hdd(2,0) for XP. Still no go.

I can't for the life of me figure this out, guys, but I now have a computer that can't boot to anything. I would appreciate any and all help you guys could offer. :confused:

---

### Post by Herman on 2006-10-27
Hello SanguineIllusion,
You could try pressing your 'c' key on your keyboard when your Grub menu is up in your monitor. That will give you Grub's [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"). Follow the how-to in the link I just gave you and see if Grub will find your hard disks, partitions and Linux kernel, and boot your operating systems manually. 
If you can do that, then you should alter your /boot/grub/menu.lst with the same commands your just used to boot up with.

If you cannot get a command line from your hard disk, you can use a [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php"), it can be used in GUI mode or Command Line mode or in, just press 'c', the same as for your installed Grub.

I hope that will be of some help to you. I have never tried RAID myself, so I don't know what it is like.

Regards, Herman :D

---

### Post by SanguineIllusion on 2006-10-29
I was able to fix this error the other day. For some reason, all I needed to do was edit the root in GRUB to (hd0,2) for Ubuntu and (hd0,0) for Windows and everything was hunky dory.

---

### Post by hardwarecompugeek on 2007-06-10
So how do you edit /boot/grub/menu.lst.

If I call /boot/grub/menu.lst
then super disk opens.

I don't know how to open for editing...


I think I know what is wrong with grub.

When I installed ubuntu, it said that all of my Hard Drives were SCSI, but they are actually IDE. Plus, grub wants to boot from hdc (or sdc) and that disk does not exist!!! 


I have 2 40 GB IDE Hard Drives, Primary = Windows   Secondary = Linux

Thanks!

---

### Post by SanguineIllusion on 2007-06-10
> **hardwarecompugeek said:**
> So how do you edit /boot/grub/menu.lst.

If I call /boot/grub/menu.lst
then super disk opens.

I don't know how to open for editing...


I think I know what is wrong with grub.

When I installed ubuntu, it said that all of my Hard Drives were SCSI, but they are actually IDE. Plus, grub wants to boot from hdc (or sdc) and that disk does not exist!!! 


I have 2 40 GB IDE Hard Drives, Primary = Windows   Secondary = Linux

Thanks!

What do you mean call it? I would just do alt+f2, gksudo and then in that menu type gedit. This will run gedit as root (or is it super user?). Then just open that file. I'm not sure why but sometimes ubuntu says scsi when it isn't. In my laptop I have an IDE hard drive and it shows up as scsi or on a scsi controller, I'm not sure why.

I'm probably the wrong person to ask but I think you can find which disk you need to use for sure by doing:
sudo lshw -C disk

---

### Post by labinnsw on 2008-05-09
Again I guess I am late.

But here is how I solved this problem.

First I got ¨The Official Ubuntu Book¨ and made sure everything was done as laid out there.

This fix was done in three stages so be patient and you might be rewarded.

**Part 1**

1. Reboot with Alternative CD
2. Select *Rescue a broken System line* and press enter.
3. Select your language and Keyboard. (You could auto detect this but it takes longer)
4. Let the computer detect the network. (It is OK to use the default host name *Ubuntu*.
5. Note carefully which disk and which partition your Ubuntu installation is on.
6. Select it and press enter
7. At the command prompt type *mount -a*
8. At the next prompt type *df*
9. Look for the single character /, it should correspond with something like /dev/hda2
10. At the prompt type *grub-install /dev/hda* omitting the 2 and replacing the rest with your partition.
11. When the process is finished, type *exit* at the next prompt.
12. Eject the CD and reboot.

**Part 2**

This alone works for some people but it did not work for me.

Taken from [http://www.linuxquestions.org/questions/ubuntu-63/grub-error-21-when-loading-ubuntu-for-first-time-394165/](http://www.linuxquestions.org/questions/ubuntu-63/grub-error-21-when-loading-ubuntu-for-first-time-394165/)

At the grub menu type c to get a grub prompt

Follow instructions below

grub> root (hd0,0)
-> or what every disk you want to install grub on.
then

grub> setup (hd0)

then "quit" grub and reboot.

I did say it was a cheeky fix, but it works!
Job done!

Again this was enough to make others happy. My problem was deeper. In fact I think I got an error something to do with the disk does not exist.
[B]
Part 3[/B]

1. Reboot with a live CD. I used Hardy Herron but Knoppix should do the trick
2. Open a Terminal Applications>>Accessories>>Terminal
3. Type "Sudo nautilus" and select "/boot/grub/device.map" file on the broken system.
4. Save as device.map.bak close and open "/boot/grub/device.map" again.
5. Make sure that the entries are pointing where they should 
e.g. (hd0)	/dev/hda
(hd1)	/dev/hde
6. Save and close
7. Select the file "/boot/grub/menu.lst" on the broken system.
8. Save as /menu.lst.bak close and open "/boot/grub/menu.lst" again.
9. Pay particular attention to lines similar to those in bold below.
10. Make any necessary corrections.
11. Note in particular the lines at the bottom after *savedefault*. If  you have these lines, comment them out as shown with #.
12. Save, close and reboot without the live CD and it should be smooth sailing.

If it doesn't work, you can always restore your files from the ones you saved at steps 4 and 7. But it worked so well for me I wanted to make a note of it so that I can use it in the future if necessary.

I am no expert so while part 3 worked for me, I cannot provide any guarantees or support so be meticulous about backing up unless you know what you are doing. The other stages were borrowed so I do not take responsibility for them either.


## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
**root		(hd0,1)**
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=90711277-cc71-4f24-aabf-65b69410e4b3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
**root		(hd0,1)**
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=90711277-cc71-4f24-aabf-65b69410e4b3 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
**root		(hd0,1)**
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
**root		(hd0,0)**
savedefault
[B]#map		(hd0) (hd1)
#map		(hd1) (hd0)[/B]
chainloader	+1

---

