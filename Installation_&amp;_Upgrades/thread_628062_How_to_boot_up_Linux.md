---
title: "How to boot up Linux"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by Takman on 2007-11-30
I have installed the latest linux 7.10 and it removed my boot menu (i also have vista and windows xp installed) so i fixed it using vista dvd. I cant get liux to appear on the boot menu or xp even using easyBCD the boot menu has completely dissapeered. I have to use a floppy to boot into xp. I want to make a floppy to boot into linux is there anywhere i can download a file to make one from xp or vista. I tried using the ubuntu live cd and following lots of instructions of how to make a boot floppy or install grub on the HDD but all i get is errors with every method i try. Does anyone know how i can get my boot menu back or a way to boot into linux?

---

### Post by PmDematagoda on 2007-11-30
I suggest that you use [SuperGRUB]("http://supergrub.forjamari.linex.org/?section=download") to reinstall GRUB into the MBR.

---

### Post by Herman on 2007-11-30
I agree with PmDematagoda in the post just above here, GRUB is the best boot loader of all!   :)

If you want to know another way, there is also [GAG Boot Manager]("http://gag.sourceforge.net/") which works really, really well from floppy disks.
GAG is a 'graphical boot manager' so it's easy to configure, there are no files you need to manually edit, or commands you have to learn. 
GAG Boot Manager boots Windows quite readily, and all you need to do to make Ubuntu bootable from GAG is install GRUB to Ubuntu's boot sector, because unlike Windows, Linux's boot sectors are normally left empty by default.
I have a page about how to use GAG with Ubuntu, that will explain things more, here: [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm").

Happy booting! :)

Regards, Herman :)

---

### Post by Takman on 2007-12-01
I have 10 partitons in total on my computer and 5HDD's but when i boot GAG from a floppy and and add a new operating system i only get two options that are both windows and both lead to vista boot menu. Why is is not working correctly?

---

### Post by Herman on 2007-12-01
If you open your GAG_4.9 folder and look inside it you'll see a folder called docs.
Open docs and insdie that there's a file called index.html that opens with Firefox  web browser.
In the 'Index' page, you will of course find links to the other documentation pages for GAG. I like to open them all in tabs.
In the 'Configuring and Using GAG' page, you'll find this,
> To see the partitions in the second hard disk you must press the key '2'. To see the partitions in the third hard disk, just press the key '3', and so on. Is that what it is you missed?

You should be able to boot all of your operating systems that are in your computer.

There is something peculiar about the way Windows sets up a dual boot though, and they don't warn you about it. 
You should have installed GRUB or GAG before you installed your other Windows and use either of those 'third party boot managers to 'hide' the earlier Windows installation.
This is done to prevent Windows from setting up a dual boot by the 'Windows default method', by which the bootloader files from one operating system are copied to the other operating system. It sounds ridiculous, I know, and it would be hilarious if it wasn't such a pain it the butt.
Here's a link to a great website about that problem, [    Understanding MultiBooting and Booting Windows from an Extended Partition]("http://www.goodells.net/multiboot/index.htm") by Dan Goodell.
Did you set up your WindowsXP - Windows Vista dual boot the 'Microsoft way', or everyone else's way?

Regards, Herman :)

---

### Post by Takman on 2007-12-01
If i select my linux boot partition on GAG it says it cant find boot so i went into linux live cd and typed "grub-install /dev/sda" which is where linux is installed. it just went to the next line as if nothing happened and it did not install it. Is there something i can do so that when i try and use GAG to boot it will boot from the linux partition?. I dont want to re-install vista or xp because it will take too long to put all my settings and programs back as they were. If i cant get this to work with using GAG i will just unintall it because it is not worth any more messing around.

---

### Post by Herman on 2007-12-01
Well you could try installing LiLo or GRUB to the boot sector of your Ubuntu partition if you haven't done so already.

 "grub-install /dev/sda" would install GRUB to MBR of whatever hard disk your system calls 'sda'.
If you want to install GRUB to the first sector of a partition you would add a partition number after the hard disk name, like  "grub-install /dev/sda2" or something like that. (Whatever hard disk and partition number is appropriate for your system).  :)

To be honest with you, even though using Linux is free, it does take a little bit of time and patience to read the documentation and learn to use it.

You don't need to do anything to uninstall GAG, just overwrite it with whatever you install to MBR instead.

Regards, Herman :)

---

### Post by Takman on 2007-12-02
I tried to install grub on the linux partition from the live cd using "sudo grub-install /dev/sda2" but it says "Could not find device for /boot: Not found or not a block device" it says this wherever i try and install it. I also tried re-installing linux to the same partition but i still cant boot it up. Is there any other way to install grub to my linux partition? so i can boot it up using GAG?

---

### Post by Herman on 2007-12-03
You can use 'sudo grub-install /dev/hdx,y' in a hard disk installed operating system. The advantage is it's quick, you only need to type one command, and it also refreshes your GRUB files in /boot.
The grub-install command runs the grub-install script in the operating system.
You can use use [Super Grub Disk]("http://supergrub.forjamari.linex.org/") to boot into operating system that doesn't even have a boot loader at all, and run the grub-install command.

The other way to install GRUB is done from GRUB itself. It can be from a GRUB shell in a terminal in a Live CD, or from  [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").

Here is a Ubuntu Forums thread where I explained it, [HOW-TO install boot loader from Ubuntu]("http://ubuntuforums.org/showthread.php?t=609548").
Here is another explanation of the same method in my GRUB Page, [                                                                  Re-install GRUB with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") eg; with Live CD.
There are several other good Grub how-tos floating around the forums too.

You can also use [Super Grub Disk]("http://supergrub.forjamari.linex.org/") to re-install GRUB and do quite a lot of other work with  booting and boot loaders even if you don't know any Linux commands yet. It's menu based. 

Regards, Herman. :)

---

### Post by Takman on 2007-12-04
I followed the how to on GRUB and it didn't work so i setup GRUB on every disks MBR and when i rebooted i got grub ERROR 17. I followed the tutorial of editing device.map I got to the bit that said "Run grub --device.map=device.map" and that command did not work it said that it was not a proper command so i edited the device.map using "alt+F2, gksudo nautilus" when i went to edit menu.lst the hard drive numbers were already correct so i left it as it was.

Also on this part:

"""10) Type "root (hd1,0)" (where hd1,0 is your Linux boot or root partition using the BIOS order)
11) Type "setup (hd0)" (where hd0 is your first boot drive, almost always hd0)""""
when i tried typing in root(hd4,1) it says does not exist but that is what my root partition is called in GRUB.

 I restarted and it still said error 17 so i tried super grub disk and it kept on coming up with "error 17" or "file not found"

When i tried to use the GAG floppy it says "sector boot not found or invalid"

I have tried re-installing linux several times and it is all the same

What is causing this error 17?. Would installing linux on a different partition help?

---

### Post by Herman on 2007-12-04
Please post the output you get back from the command 'sudo fdisk -lu' and if you can, the bottom half of your /boot/grub/menu.lst file in Ubuntu.
You might need to use your Ubuntu Live CD and mount the Ubuntu file system to get that. Here's how, [                                  Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD").

Installing GRUB to every hard disk's MBR is a good thing to do, I do that too, but it won't help you to boot Ubuntu from GAG Boot Manager.
To boot Ubuntu from GAG Boot Manager, you need GRUB installed to the boot sector of your Ubuntu partition ,not just to a hard disk's MBR.

---

### Post by Takman on 2007-12-05
I installed Ubuntu on a different partition and it said error 22 so i fixed it using the super grub disk. When GRUB booted i changed the partition number for Ubuntu now now it works!!. The only problem i have now is that when i try and install Wine it says:

[B]The following packages have unresolved dependencies. Make sure that all required repositories are added and enabled in the preferences.
wine:
 Depends: binfmt-support (>=1.1.2) but it is not installable
 Depends: ia32-libs (>=1.6) but it is not installable
 Depends: lib32asound2 (>1.0.14) but it is not installable
 Depends: libc6-i386 (>=2.6-1) but it is not installable[/B]

Why is this happening?. Where can i get these files?

---

### Post by Takman on 2007-12-05
also how to i navigate to desktop?

i tried "cd ~/desktop"
but it says "bash: cd: /home/thomas/desktop: No such file or directory"

---

### Post by Herman on 2007-12-05
```
cd Desktop/
```

---

### Post by Takman on 2007-12-07
All seems to be working OK now, thanks for all your help Herman.

---

