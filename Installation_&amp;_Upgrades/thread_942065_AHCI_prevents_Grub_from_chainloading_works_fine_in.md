---
title: "AHCI prevents Grub from chainloading works fine in IDE mode"
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by Cetra on 2008-10-08
Hey Guys,

I am having an issue with triple booting OS X, Ubuntu and Windows XP.

Currently, I have 3 hard drives, all with their separate respective MBRs

C:\ contains the XP bootloader, with my NTFS partition, connected via IDE
H:\ contains Grub, with my Ubuntu partition, connected via SATA
N:\ contains Darwin, with my OS X HFS partition, connected vis SATA


Ok, so I initially just had XP and Ubuntu running, this worked a treat, I could chainload the xp boot easily.  Also I could boot into ubuntu and that worked.

Next, I installed OS X on my N:\.  I had to change the bios settings for my drives to work in AHCI mode, from IDE mode, as this is what is needed for OS X to work.

I had a few issues with grub and booting into OS X, I ended up copying the chain0 file into the /boot/grub/ directory to get it working because I couldn't chainload directly to the N:\, it just sat there. but that's now working with the chain0 file.

Now my next problem is that, from grub, I can't boot into windows XP.  If I set in the BIOS to operate in IDE mode, I can boot into windows from grub.  If I set it in AHCI mode, I can boot into windows xp by setting C:\ as the first boot, i.e, bypass grub.   But I don't want that.  I want grub to be able to boot into windows in AHCI mode.

Ubuntu boots fine, OS X works fine with that little fix, but I can't get windows to boot, it's as if grub can't chainload another drive when in AHCI mode.

I have done a plethora of tests and different configuration options, my current conclusion is that grub doesn't like talking to other drives when in AHCI mode.  I am wondering a few things:

[LIST=1]
[*]  Is this a problem with my motherboard and BIOS?

[*]  I installed ubuntu when the drive was in IDE mode, it's now working in AHCI, but do I need to reinstall/recompile grub to work correctly?

[*]  Are there any settings i need in menu.lst to change to get it talking to the other drives

[*]  Is there any way, inside of grub, to just read the MBR of a drive and display it in hex format so I can confirm that grub is reading it correctly?  (i.e, cat (hd2,0)+1)

[*]  Everytime I change anything in the bios, my hard drive order changes and i need to run sudo fdisk -l and compare that with the device.map file, is there a way of running a command inside of grub similar to fdisk -l, maybe even just get the sizes of the hard drives

[*]  Rebooting takes forever, is there a way of testing out grub within ubuntu?
[/LIST]

I'm pretty frustrated with it all, it should be working, but it isn't and I really don't know what I'm doing wrong.  Any help would be welcome.

---

### Post by caljohnsmith on 2008-10-08
> **Cetra said:**
> I am wondering a few things:
[LIST=1]
[*]  Is this a problem with my motherboard and BIOS?

[*]  I installed ubuntu when the drive was in IDE mode, it's now working in AHCI, but do I need to reinstall/recompile grub to work correctly?

[*]  Are there any settings i need in menu.lst to change to get it talking to the other drives

[*]  Is there any way, inside of grub, to just read the MBR of a drive and display it in hex format so I can confirm that grub is reading it correctly?  (i.e, cat (hd2,0)+1)

[*]  Everytime I change anything in the bios, my hard drive order changes and i need to run sudo fdisk -l and compare that with the device.map file, is there a way of running a command inside of grub similar to fdisk -l, maybe even just get the sizes of the hard drives

[*]  Rebooting takes forever, is there a way of testing out grub within ubuntu?
[/LIST]

I'm pretty frustrated with it all, it should be working, but it isn't and I really don't know what I'm doing wrong.  Any help would be welcome.
One thing you might want to keep in mind is that on start up, Grub sees the order of drives as the same as the BIOS boot order, not the same as the device order in Ubuntu's /dev directory; this is because on start up, Grub must use BIOS to access the drives. So the BIOS boot order has nothing to do with the device order in Ubuntu's /dev directory; Ubuntu's /dev directory is ordered by the type of device, so for HDDs they would be ordered by whether they are IDE, SATA, USB, and so on. 

So on start up, if you press "c" at the Grub menu to get the Grub CLI, you could type:
```
grub> geometry (hd
```
Then press TAB for tab-completion, and you should see a list of the drives Grub sees; (hd0) will be the boot drive obviously, and (hd1) and above will be the other drives. Then to see what the partition structure and size of the HDD is for (hd1) for example:
```
grub> geometry (hd1)
```
That should give you some big clues as to which drive (hd1) really is, and you can repeat the process for the other drives.

Also, as far as I know, reinstalling Grub is not going to change how Grub behaves under IDE vs. AHCI mode, and there are no settings in menu.lst that I'm aware of that will help your AHCI/IDE problem. 

But the above Grub geometry commands should hopefully help you troubleshoot your problem, but about an exact fix, I don't know as I've not encountered your situation before. Good luck, and if you figure out a good solution, please post it so everyone in the future can benefit. :)

---

### Post by Cetra on 2008-10-09
Well, I finally got it working!

caljonsmith's explanation of geometry in grub helped me out quite a bit, was rather handy to get some stats of hard drives within grub.  It allowed me to be sure that I was using the correct hard drive! (I have 5)

Anyways, here's an explanation of how I got my triple boot to work.  I'm guessing that it's probably different for every BIOS, but this might help someone else out along the track.  Here's how I configured bootloading for my systems:

**Ubuntu:**

This one was rather easy, just installed it and all went ok!  I had no drama getting into grub initially, apart from the fact that when I was swapping from IDE to AHCI and back it loved to shuffle my hard drive order around...

There were like 4 ubuntu startup options that I decided to get rid of.  I kept a backup of them that I can access from within grub just incase I do actually need to boot into recovery mode.  But they're not on the main boot menu currently.

**Mac OS X:**
The installation of Mac OS X is a pretty volatile excercise in itself,  I guess the only thing I did in the installation pertaining to this problem was install the bootloader to the MBR of the right drive.

Configuring it in grub was a bit harder.  I couldn't actually just chainload the drive directly, even with rootnoverify it was giving me nothing.  So I found another guide on the internet that suggested that you keep hd0,0 as root, and use the [chain0]("http://wiki.osx86project.org/wiki/index.php/Chain0") file that comes with the dvd.  What I did was copy it to the location /boot/grub/chain0 (using sudo of course) and then I got grub to chainload it.  The chain0 file actually searches all your partitions/drives for a HFS (0xab) drive, so this was good in that when I was changing from IDE to AHCI and my drive letters were playing musical chairs I didn't have to update this menu item at least.

**Windows **

So this was the hard part.  I had OS X and Ubuntu working, but Windows, although working in IDE mode, stopped working in AHCI mode.  As much as I'd like to do away with windows, I can't.   The first step was working out the correct drive, as I have 5 it is a bit of a hassle to work it out.  Luckily though, I could approximate the size of it and use the *geometry* function to work out which was which.  I was also making sure that grub could talk to other drives, or atleast read their MBR.  To do this I simply used cat and specified a block rather than  file.  For example *cat (h4,0)+1*

Then after I knew that I had the right drive and grub was reading it correctly I started trying out a few different configuration options.  Turns out that I had to add the *map* statements into the menu as it sort of loosely mentions in the grub manual.  This is strange as adding them in IDE mode breaks the windows bootup.


Anyways, thanks for the tips caljohnsmith, you sent me in the right direction!

Incase anyone is interested, I have included my menu.lst file.  Whether this will work for you I'm not sure, but it's currently working for me :)

> ####### MENU SETTINGS #######

default		saved
timeout		5

######### MENU ITEMS ########

title		Windows
savedefault
rootnoverify	(hd4,0)
map		(hd0) (hd4)
map		(hd4) (hd0)
makeactive
chainloader	+1

title           OS X
savedefault
root	        (hd0,0)
chainloader     /boot/grub/chain0

title           Ubuntu
savedefault
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-4-generic root=UUID=d6746cc5-98e8-4e3f-9423-f0732e597776 ro quiet splash
initrd          /boot/initrd.img-2.6.27-4-generic
quiet

---

