---
title: "Problem Dual booting Fedora Core 6 with Ubuntu"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by ryanmbeal on 2007-02-17
I'm a linux nOOb trying to get a laptop setup to experiment with Ubuntu and Fedora. My Ubuntu installation went well, but now I can't boot the previous Fedora installation. I've gone through a lot of posts here and elsewhere but have yet to get anywhere. 

I partitioned my disk as follows: 

	/dev/sda1    - /boot   200MB  ext3  
	/dev/sda2    - /data    40GB    ext3  
	/dev/sda3    - swap    1.5GB   swap 
	/dev/sda4    - Extended partition
	/dev/sda5    - /          20GB   ext3    - For Fedora
	/dev/sda6    - /          20GB   ext3    - For Ubuntu

I installed Fedora C6 first on sda5 and got it working. I'm not positive that I actually got GRUB installed to /boot like I had hoped to do. I can still mount the sda5 drive and see the files in /boot/grub/

Then i installed Ubuntu 6.10 and got GRUB installed to /boot everything works fine for booting Ubuntu but I can't seem to get Fedora booting again despite trying a bunch of mods to the GRUB install in /boot. 

The entries added automatically during Ubuntu install look like this: 

	# This entry automatically added by the Debian installer for an existing
	# linux installation on /dev/sda5.
	title        Fedora Core (2.6.19-1.2911.fc6xen) (on /dev/sda5)
	root        (hd0,4)
	kernel        /boot/xen.gz-2.6.19-1.2911.fc6  
	savedefault
	boot

But when I try to boot to this option with GRUB i get the following: 

	(XEN) Command line: /boot/xen.gz-2.6.19-1.2911.fc6
	(XEN) FATAL ERROR: dom0 kernel not specified. Check bootloader configuration

I'm unsure why these are set to go to /boot/xen... instead of /boot/vmlinuz...

I've also tried making a link between the /boot vmlinuz and initrd files on /sda5/boot (Fedora) and /sda1/boot and adding the following entries in menu.lst. 

	# Added for Fedora Boot
	title Fedora Core 6 boot
	root (hd0,0)
	kernel /boot/vmlinuz-2.6.19-1.2911.fc6xen root=/dev/sda5 ro quiet splash
	initrd /boot/initrd.img-2.6.19-1.2911.fc6xen.img
	boot

	# Added for Fedora Boot
	title Fedora Core 6 noboot
	root (hd0,0)
	kernel /vmlinuz-2.6.19-1.2911.fc6xen root=/dev/sda5 ro quiet splash
	initrd /initrd.img-2.6.19-1.2911.fc6xen.img
	boot

With these options I don't even seem to get as far with the automatically added additions. 

	Error 15: File not found 

I saw suggestions for trying 

	title Fedora
	rootnoverify (hd0,4)
	chainloader +1

But I get: 
	Error 13: Invalid or unsupported executable format

Can anyone help me get this Fedora install dual booting with Ubuntu? 
 Thanks in advance.

---

### Post by Herman on 2007-02-18
> I installed Fedora C6 first on sda5 and got it working. I'm not positive that I actually got GRUB installed to /boot like I had hoped to do. I can still mount the sda5 drive and see the files in /boot/grub/

Then i installed Ubuntu 6.10 and got GRUB installed to /boot everything works fine for booting Ubuntu but I can't seem to get Fedora booting again despite trying a bunch of mods to the GRUB install in /boot. Hello ryanmbeal,
If you are using Ubuntu's Grub to boot with, you just need to edit the Ubuntu grub's menu.lst with a configfile boot entry. A configfile boot entry is a lot easier, and not only that, with a configfile boot entry, your Ubuntu's grub will look up Fedora's Grub menu. You will boot Fedora from it's own menu, therefore Fedora will be in charge of keeping it's own menu updated when it gets a new kernel in an update.
Just make an entry like this at the bottom of your Ubuntu grub's menu.lst,
```
### END DEBIAN AUTOMAGIC KERNELS LIST
                                                                     
# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root
                                                                     
                                                                     
# This entry automatically added by the Debian installer for another linux OS
# on /dev/sda5
title        Fedora Core 6
configfile       (hd0,4)/boot/grub/menu.lst
``` Just check to make sure Fedora's grub has a /boot/grub/menu.lst file. Some distros might have something different like a /boot/grub.conf or some other such equivalent, in which case you would need to change the command a little to make it fit the situation.
I think (hope) that will work for you,
Regards, Herman :)

---

### Post by adromidon on 2007-05-01
If you have FC 6 installed already and do not want to ax it then when you install Ubuntu should i switch the drive order in order to make your suggestion of the menu.list option work? or can i possibly go in the opposite direction and do this with the Fedora Grub

---

### Post by pinoytechie on 2007-05-01
sorry, i've got confused...

where (partition) exactly are "vmlinuz-2.6.19-1.2911.fc6xen" and "initrd.img-2.6.19-1.2911.fc6xen.img" files located?

---

### Post by adromidon on 2007-05-01
the first one VMlinuz is a  Xen compiled kernel of Linux and the Intrid.img is the loading image for Linux on FC i think

i could be off but i have used FC6 for some time and I think those lines are conducive to a Fedora Install that is compiled for XEN and partitioned as an LVM setup

I am wrong sorry :(

---

### Post by pinoytechie on 2007-05-01
yeah I know about those files, but where can you find these files?

vmlinuz-2.6.19-1.2911.fc6xen
initrd.img-2.6.19-1.2911.fc6xen.img

sda1,2,3...?

---

### Post by Herman on 2007-05-01
Hello adromidon :)
 I would just install normally if you have a normal FC install, but I don't know anything about LVM or RAID.  :)

pinoytechie, you can use  [Grub's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") to find out.

Regards, Herman

---

### Post by adromidon on 2007-05-01
do a gedit /etc/grub.conf

and it will show you i think

---

### Post by adromidon on 2007-05-01
Ok thanks for the suggestion I will do that and if it turns out my grub conf gets scrubbed by ubuntu then i think i can manage to get Fedora added to the list/ :)

---

### Post by Herman on 2007-05-01
Okay, I think Fedora has a /boot/grub/menu.lst like Ubuntu has because I went and checked a post in their Web Forum about it, but I could be wrong, here's the link, [Post grub menu list for Fedora 7?]("http://fedoraforum.org/forum/showthread.php?t=154071")

There is no logical reason to think that Ubuntu will interfere with anything on any other operating system's partition (filesystem). Rumors like that are spread around by superstitious folk who don't really understand too much about the processes of booting and operating system installation. Just ignore them. Ubuntu will write the IPL for Grub in the first 446 bytes of your Master Boot Record, or if you want, you can use the 'Alternate' CD to install your Ubuntu Grub's IPL to the first sector of the Ubuntu partition. It's normally quite a trivial matter and it will make no difference which OS's grub is 'in MBR.' Either you configure Fedora to boot Ubuntu or the other way around. It makes no real difference at all.
Ubuntu will probably add Fedora to its menu.lst automatically during installation, but it will be a direct kernel boot entry. You can change that to a configfile entry later sometime, that's what I would do.
If you are using LVM or RAID then I don't know.

Regards, Herman :)

---

### Post by adromidon on 2007-05-02
I was not saying it would corupt Fedora just wanted all the distros to play nice with each other and have one unified installer.

I now on one machine have Ubuntu 7.0.4 Mandravia free 2007 and two Fedora versions  FC6 and F7T4 (Fedora 7 Test 4)

I just want Unbuntu to be the grub master so to speak lol

---

### Post by Herman on 2007-05-02
Oh, okay, cool! :)  :guitar:

---

### Post by adromidon on 2007-05-02
btw I managed to get all of the distros working by adding the following lines

```

title Fedora Core 6 
rootnoverify (hd0,x)
chainloader +1

```

While x= the partition number of the distro's root

this methode will pass the booting on to the next bootloader in this case Fedora's Grub. You can then select any kernels on this list or other options you may have setup on this distro's grub 

if you use an additional hard drive then starting with the second drive (hd0,x) would become (hd1,x) or 2,3,4 what ever the # of your HD is. 

Also for me anyway if you put more then one space after rootnoverify then it will not load the next grub

also the chainloader +1 line must only have one space after chainloader also.

I had this fail numerous times when i used more then one space in these lines

---

### Post by Herman on 2007-05-02
Yes, the chainloader command is very useful for booting all kinds of other operating systems.
The chainloader command will work even if the other operating system has a different bootloader, like Lilo  or Windows NTLDR.
In order to use the chainloader command though, the other bootloader must have a stage1 (IPL) copied to the bootsector of a partition. Windows always has that. With Linux most often you have to do that yourself, unless you installed it like that.

The configfile command, doesn't require you to do anything to the other Linux operating system you are trying to boot up, but you are restricted to being able to boot only other Linuxes that use Grub.

Either of those two methods are good for booting other Linuxes, especially when the other Linuxes will be automagically updating their grub menus. If it's another Linux that does not have any ability to update its own grub menu, then there is no advantage in the chainload or configfile boot methods.

The direct kernel boot method has the advantage of being a lot faster, because one step is left out, and you boot the other Linux directly.  The direct kernel boot method will work even if the other operating system has a mistake in its menu.lst file and it can't boot by itself.

All three of these methods are useful to know and are best used on different occasions. Grub is an amazing bootloader and it can be a lot of fun learning about Grub and playing with Grub. Grub comes close to being a small operating system itself.

Regards, Herman :)

---

### Post by adromidon on 2007-05-02
> **Herman said:**
> Yes, the chainloader command is very useful for booting all kinds of other operating systems.
The chainloader command will work even if the other operating system has a different bootloader, like Lilo  or Windows NTLDR.
In order to use the chainloader command though, the other bootloader must have a stage1 (IPL) copied to the bootsector of a partition. Windows always has that. With Linux most often you have to do that yourself, unless you installed it like that.

The configfile command, doesn't require you to do anything to the other Linux operating system you are trying to boot up, but you are restricted to being able to boot only other Linuxes that use Grub.

Either of those two methods are good for booting other Linuxes, especially when the other Linuxes will be automagically updating their grub menus. If it's another Linux that does not have any ability to update its own grub menu, then there is no advantage in the chainload or configfile boot methods.

The direct kernel boot method has the advantage of being a lot faster, because one step is left out, and you boot the other Linux directly.  The direct kernel boot method will work even if the other operating system has a mistake in its menu.lst file and it can't boot by itself.

All three of these methods are useful to know and are best used on different occasions. Grub is an amazing bootloader and it can be a lot of fun learning about Grub and playing with Grub. Grub comes close to being a small operating system itself.

Regards, Herman :)

One issue the only distro i am trying to use that is not playing nice is Mandravia. I have this installed on an logical partition on a second HD when i try to point to it ethier through chainloader or configfile is says the partition does not exist

it is on a secon physical drive the other distros are on the same physical drive so i am not sure if this has anything to do with it

---

### Post by adromidon on 2007-05-02
Damn i fixed my issue again.

I will post what i did here incase someone else had the same issue

My Mandrabia was on my second HD and this could not be booted to because in the bios of my computer the second hard drive was not set to be detected so as far as the coputer knows i have only one HD until the OS loads and can probe for it.

I changed my bios settings to reflect this and not i am able to use the chainload command to load Mandravia

---

