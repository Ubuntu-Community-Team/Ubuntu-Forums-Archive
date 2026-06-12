---
title: "boot winXP or win7 install cd from grub ?"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by zonemikel on 2010-04-01
I have a usb HDD and i have made separate partitions, one @ 3.7gig and another at 100mb on these partitions I copied over the files from the windows 7 install cd and microxp install cd respectivly. 

How can i get grub to boot these partitions ? My goal is to make one external usb hdd where i can install multiple operating systems. Oh while we are at it how can i get grub to boot the ubuntu cd if i copy it over like i have done with the windows install cd s 

```

Disk /dev/sdc: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00f200f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        3655    29351616    7  HPFS/NTFS
/dev/sdc2            3656        7296    29246332+   5  Extended
/dev/sdc5            3656        4662     8088696   83  Linux                    <---- ubuntu install
/dev/sdc6            7141        7296     1253038+  82  Linux swap / Solaris
/dev/sdc7            6583        7140     4482103+   b  W95 FAT32         <---- windows xp (actuall OS)
/dev/sdc8            4663        4675      104391    6  FAT16                    <--- micro xp install cd
/dev/sdc9            4676        5172     3992121    7  HPFS/NTFS         <---- win7 install cd 



```

---

### Post by conradin on 2010-04-01
what version of grub are you using?

---

### Post by Mark Phelps on 2010-04-01
Maybe I'm misunderstanding your question ... but no version of GRUB is able to actually boot MS Windows OS's.  

What they all do is hand over control to an MS Windows boot loader.  
For XP, this was NTLDR.  For Vista and Win7, it is BOOTMGR.  

Unless those files are present on your drive, any attempt to boot either MS OS will fail.

---

### Post by bpalone on 2010-04-01
Another issue you are going to face is getting Windows to Boot from an external drive, especially USB.  If my memory is correct, some people did have some success, but they had to do several things in order to get there.  Do a Google on "Boot Windows from USB" and you will some idea of what you are facing.   I had looked into it some time back for other reasons and finally decided it wasn't worth the fight.  But, I was looking at getting Win2K to run off of a USB memory stick.

Good luck.

---

### Post by zonemikel on 2010-04-01
> what version of grub are you using? 	 

i have menu.lst so i think its the one that was around before 2 ... whatever the latest one was before they came out with 2

> Maybe I'm misunderstanding your question ... but no version of GRUB is able to actually boot MS Windows OS's.  

What they all do is hand over control to an MS Windows boot loader.  
For XP, this was NTLDR.  For Vista and Win7, it is BOOTMGR.  

Unless those files are present on your drive, any attempt to boot either MS OS will fail. 	  	

Ya i dont want to boot the OS i want to boot the install cd ... i copied the files over into a partition on my external usb drive. So i want the grub menu to be like 

ubuntu
install XP
install Win7
install Ubuntu

where it would load the installation files loaded on the partition that i have the files from the cd on. For instance i have one 4 gig partition that has these files from the windows 7 install cd 
file:///media/disk-1/SETUP.EXE 
file:///media/disk-1/BOOTMGR 
file:///media/disk-1/AUTORUN.INF 
file:///media/disk-1/UPGRADE 
file:///media/disk-1/System%20Volume%20Information 
file:///media/disk-1/SUPPORT 
file:///media/disk-1/SOURCES 
file:///media/disk-1/EFI 
file:///media/disk-1/BOOT 

but how do i get grub to "hand over" the control to that cd ? 

> 
Another issue you are going to face is getting Windows to Boot from an external drive, especially USB. If my memory is correct, some people did have some success, but they had to do several things in order to get there. Do a Google on "Boot Windows from USB" and you will some idea of what you are facing. I had looked into it some time back for other reasons and finally decided it wasn't worth the fight. But, I was looking at getting Win2K to run off of a USB memory stick.


I have already done it with just a 4 gig usb stick and windows 7. You have to tell it to load windows boot loader thing to the usb stick though, thats the one step i cant do on my usb drive without loosing grub. 

Also you can easily run XP off a usb drive just use MicroXP for usb .... its recommended you use usb hdd not flash because it will eat up your flash. 

i've tried update-grub and it does not find any other os's on the hdd (even though there is a xp partition with the xp os on it also) ...

i'm at a loss and have no time

---

### Post by oldfred on 2010-04-01
This is for XP
Copy Windows XP to usb
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

How to install ubuntu on USB drive and carry entire computing system in pocket? 
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)
With details on some of the ccaveats, std install.
[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

But I do not know if you can combine windows & olinux on one USB.

---

### Post by zonemikel on 2010-04-01
> **oldfred said:**
> This is for XP
Copy Windows XP to usb
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

How to install ubuntu on USB drive and carry entire computing system in pocket? 
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)
With details on some of the ccaveats, std install.
[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

But I do not know if you can combine windows & olinux on one USB.

I can run windows and linux on the same usb drive fine. What I'm trying to do is get grub to boot the windows install cd instead of ubuntu. Its really close to the last link about booting directly from iso's but what would be the menu entry to boot from a windowsXP setup disk iso ? Or from a windows 7 setup iso ? 

Thanks for all your help so far, I'm going to add the ubuntu iso's to the grub menu and see if i can get them to work. I'm pretty sure i can get grub to load a xp or windows 7 cd if i could just add a menu entry and point it to the right directory.

---

### Post by zonemikel on 2010-04-02
well i was going to install grub2 to load all the neat stuff you pointed out in the link 
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
and installing it it found all this !! 

```

Updating /boot/grub/grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.28-18-generic
Found initrd image: /boot/initrd.img-2.6.28-18-generic
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Microsoft Windows XP Professional on /dev/sdf1
Found Windows Vista (loader) on /dev/sdf9
done

```

I'm gonna restart and see what happens when i load them ?

---

### Post by Mark Phelps on 2010-04-02
Text removed ... looks like you got update-grub working.

Good Luck.

---

### Post by zonemikel on 2010-04-02
Partial Success !!! 

had all kinds of nightmares with grub2, mainly weird remnets of grub 1.96 still installed and not being able to boot because grub2 wiped it out. If you have this problem before you run sudo update-from-grub-legacy be sure to edit your devices.map file and make the hdd where you want grub to to load in the bootloader be hd0. 

anyway after grub2 is installed if i load the partition that has the files extracted from the windows 7 cd it will load the windows 7 install cd. the menu entry looks like this

```

menuentry "Windows Vista (loader) (on /dev/sdf9)" {
    set root=(hd0,9)
    chainloader +1
}

```

I extracted the files from the windows 7 install disk to that partition. 

as for xp it says this is not a bootable disk .. i think i need to tell it what folder to look in or something.

---

### Post by zonemikel on 2010-04-02
Well i take that back, the windows 7 installation crashes after a while saying it cant read the files. 

With the xp partition i tried to dd the iso directly to the partition and that didnt work at all. I also tried to extract the files to the partition then move the ntldr and some other files to the root directory and that still gives "invalid boot disk or disk error". I think i need to load the drive on a machine running XP and then sys F: or something. 

Maybe its all impossible, it really seemed like i had got the windows 7 install to work, oh well.

edit --------------------
i could do something like this [http://myeeeguides.wordpress.com/2008/11/15/winsetupfromusb-install-windows-xp-from-usb-flash-drive/](http://myeeeguides.wordpress.com/2008/11/15/winsetupfromusb-install-windows-xp-from-usb-flash-drive/) but at this point why bother. I think i'm going to opt for just dd'ing a version of windows to the target drive, that might carry some extra baggage but i should be able to get a nice install of microxp with everything i want then just dd it to a xp.dump then from there boot ubuntu off my usb drive and dd that xp.dump to the target drive on the pc i'm trying to install xp on. Same goes for ubuntu also ... i'm going to install it get all the upgrades and then make a dump of it so later i can just dd it to target devices without having to do tons of upgrading after installing. Is this a good idea ?

---

### Post by zonemikel on 2010-04-03
Well i got grub2 to boot the ubunut iso's ... but when it loads xubuntu alternate it says it cant find the cd ? 

Any idea how i can go to the console and somehow mount the cd so i can tell the installer where the files are ?

---

### Post by theozzlives on 2010-04-03
This is like feeding oats to a dead horse. I've tried to install Windows to USB, it don't work!!!

---

### Post by zonemikel on 2010-04-04
> **theozzlives said:**
> This is like feeding oats to a dead horse. I've tried to install Windows to USB, it don't work!!!

Well there is a microXP usb version out there that works. It will install to usb and work on *some* computers if you have tweeked the bios right, if not it will give stop 0x7b error. I wasnt trying to install xp to a usb drive though i was trying to have the setup cd on my usb hdd then install on computers with normal hdd. Basically instead of having a cd to install xp i would have a usb drive. 

Its a dumb nightmare. I think i might be able to get win7 install to work from usb but xp is hopeless. 

I wanted to have some usb hdd that i boot and grub greets me with a menu like 

install ubuntu
install kubuntu
install xubuntu
install win7
install winxp
rescue disk

but i keep thinking to myself, whats the point ? Unless your puter does not have cdrom this is dumb.

---

### Post by ttanev on 2010-10-20
It's very useful to have an XP boot cd on USB flash, especially when  there's no CD or DVD-ROM to boot from. Many times the NT file system is  corrupted from a lot of consequential power shortages which exhausted  the UPS and the system stops booting starting with > "Windows could not  start because of the following file missing or corrupt: ..... You can  attempt to repair this file by starting Windows Setup using the original  Setup CD-ROM.
Select 'r' at the first screen to start repair."Often  this type of problem is recoverable only with setup XP CD. I already  tried Hiren's Boot CD and System Rescue CD over such problems. The  systems that I have the obligation to administrate have an Rack Mount  and no CD or DVD-ROM, so the USB GRUB installer is really preferable.  I would also ask if someone knows how to setup starter for Hiren Boot  CD or System Rescue CD beside Ubuntu's USB version in it's GRUB, if it  is possible of course.

---

### Post by Mark Phelps on 2010-10-20
> **ttanev said:**
> I would also ask if someone knows how to setup starter for Hiren Boot  CD or System Rescue CD beside Ubuntu's USB version in it's GRUB, if it  is possible of course.

Well ... if you REALLY want help, you would do a LOT better starting a new thread with the proper title -- not resurrecting a 6-month old thread that is unrelated to what you want to do.

---

