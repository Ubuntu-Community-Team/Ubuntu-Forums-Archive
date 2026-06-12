---
title: "GRUB installing to wrong drive"
date: 2007-10-14
forum: Installation &amp; Upgrades
---

### Post by sonik887 on 2007-10-14
I have 4 SATA hard drives in an nVidia nForce4 AMD motherboard (Asus A8n-SLI Premium).  The drives are as follows:

74gb Raptor (primary boot, XP installed here, NTFS)
750gb drive (data, NTFS)
300gb drive (data, NTFS)
300gb drive (for ubuntu)

I boot the 7.10 RC Live CD and run through the install.  It says the following for drive partitioning:

750gb drive is /sda
300gb drive (for ubuntu) is /sdb
74gb drive is /sdc
300gb drive (data, NTFS) is /sdd

So I do guided install for all of /sdb, it installs everything fine and puts Grub automatically onto "/hd0" which i'm assuming maps to the 750gb drive instead of the 74gb drive.

When I reboot, I get just XP booting and no grub.
If I tell my motherboard to boot from the 750gb drive, i get Grub but I get an "error 17".

I tried this with ubuntu 7.04 and did some research and dug into my grub config and it looks like the drive mappings during installation end up being different than the drive mappings when i reboot so i have to change around grub to help it get to the right drive.  

What do i need to do to get this to work right the first time (during install) instead of going in and hacking around in the grub config (which is a pain)?

thanks

---

### Post by Scunizi on 2007-10-15
I've had this happen with multiple drives and I think it has something to do with the order of the drives.... bear with me here.. If you have 4 sata connectors on the MB labeled 0-3 or 1-4 but your bios sets anything other than 0 or 1 as the main boot drive you can end up with issues.. 

The easiest grub solution that takes seconds to do is to follow the instructions on the link below.. one of the things I read on this page (after the 3rd read) is that putting grub on all your HD's can be useful if the primary drive goes down and you can't boot.   Just change the boot order to one of the other drives and viola, you're back into ubuntu (providing it's not installed on the dead drive :)  )

Check out.  [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by quandary on 2007-10-15
Hi!

I had a similar problem. I resolved it. Maybe it will solve yours, too.
The problem is that GRUB mixes up the HD numbers...

See my post (it's 9 pages, so i don't rewrite it here...):

[http://ubuntuforums.org/showthread.php?t=576648](http://ubuntuforums.org/showthread.php?t=576648)

---

### Post by Herman on 2007-10-15
I think if we investigated this objectively we would find it is not GRUB that 'mixes up the HD numbers' at all.

quandary, in your case Ubuntu installed GRUB correctly to your first hard disk, which is exactly what it is programmed to do. 
Ubuntu isn't primarily designed to be installed in USB drives, it's supposed to replace Windows in your computer, or be installed dual boot with Windows, so you can replace Windows with it later.

Ubuntu was never designed to be used as an accessory for Windows.

It's possible to get it installed in a USB drive, but as you found out it takes a little work. No surprises there. If you wanted to have control of where GRUB gets installed you should have used the 'Alternate' Ubuntu installation CD. In some of the Ubuntu Live CDs you can also choose where to install GRUB.

Actually I do have one Ubuntu installation in an external USB hard drive myself and I do find it quite handy sometimes, so I don't want to say Ubuntu in a USB drive isn't a good thing. Ubuntu in a USB drive is very nice and can be extremely useful  :)


sonik887, 
I agree with Scunizi, just install GRUB in all your MBRs, then you won't have any problems, 

But about GRUB installing to the wrong drive's MBR, where do these strange issues come from?
I have never had any trouble installing GRUB exactly where I want it, or replacing it with the IPL for any other boot loader or boot manager any time I want.

This is an interesting subject and there could be several possible reasons for GRUB getting installed in the wrong drive.

It always has been a little unpredictable what will happen when we have have IDE and SCSI or SATA drives plugged in to the same motherboard, (or a USB device. That's why we are provided with the /boot/grub/device.map.
                 Here is what the GNU GRUB Manual has to say on this subject, [15.3 The map between BIOS drives and OS devices]("http://www.gnu.org/software/grub/manual/grub.html#Device-map").
And here's what I've got on th so far, [**Editing GRUB's device.map**]("http://users.bigpond.net.au/hermanzone/p15.htm#device.map") (when you have SATA and IDE hard disk drives in the same machine, and Grub won't boot anything)

The odd thing about your problem, sonik887, is that you only have SATA drives, so it should have been simple for GRUB to be installed in your first hard drive.

Unless, as Scunizi suggested, your boot hard disk boot priority was scrambled up in your BIOS settings somehow maybe? [Changing the hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority").

In other case (not in this case), the reason why GRUB gets mixed up can be that we have a few people with IDE drives who sometimes maybe don't understand how to use master and slave jumper settings, or the difference between cable select IDE cables and plain ones, and where to plug in the different colored plugs. That's another cause of GRUB getting the drives mixed up, or rather, the user getting the hard drives mixed up,

What can be done about it?
Well if you want to be sure, probably you can install the IPL for GRUB to the Ubuntu partition's first sector and not to any MBR at all. 
Then when you reboot your computer, boot up with [Super Grub Disk]("http://supergrub.forjamari.linex.org/") and get a  [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and install GRUB anywhere you want from there.
If it goes to the wrong MBR then it's your own fault. :)

Or install GRUB to all MBRs like we already said. :)

Regards, Herman :)

---

### Post by maybeway36 on 2007-10-15
Sometimes GRUB doesn't like SATA :(
If you have a floppy disk, you acn try installing GRUB to that.

---

### Post by quandary on 2007-10-20
> **Herman said:**
> I think if we investigated this objectively we would find it is not GRUB that 'mixes up the HD numbers' at all.
Oh true. I've done some research.
Bug#32357:  	 
Description: Installer doesn't recognise SATA disks as primary. 
Project: grub-installer (Ubuntu)  	
Importance: High
Bug status: Confirmed
The problem is different detection of drives during the installation and after, ie. during the boot of the installed system. It has nothing to do with the hardware itself, rather than with (wild guessing) different kernel, different module loading/order and such from the installation disc compared to installed system.

> **Herman said:**
> 
quandary, in your case Ubuntu installed GRUB correctly to your first hard disk, which is exactly what it is programmed to do. 
Yes. I, after I saw hd0 under advanced, I know that. And I didn't even complain about that, although some important detail like this shouldn't be hidden behind a button...


> **Herman said:**
> 
Ubuntu isn't primarily designed to be installed on USB drives, 

I know that Ubuntu is not designed to be installed on USB drive. Neither is Windows. I did not expect the installation to be without problem. In fact I was surprised how easy it was.

> **Herman said:**
> 
it's supposed to replace Windows in your computer, or be installed dual boot with Windows, so you can replace Windows with it later.

Well, installing Ubuntu on an external HD because the internal HD is full with windows data is some kind of dual boot, isn't it? Or not?
Apart from that, hat's unrealistic. Ubuntu and Linux in general lacks USEFUL state of the art office software and printer drivers, not to mention drivers for special hardware. Windows has this. Windows was designed as a Desktop OS. Linux is a derivate of UNIX, and that was designed to be a server-OS, not a desktop-OS.

> **Herman said:**
> 
Ubuntu was never designed to be used as an accessory for Windows.

True, but it better would have been.

> **Herman said:**
> 
It's possible to get it installed in a USB drive, but as you found out it takes a little work. No surprises there. If you wanted to have control of where GRUB gets installed you should have used the 'Alternate' Ubuntu installation CD. In some of the Ubuntu Live CDs you can also choose where to install GRUB.

Yes, I used the 7.04 install CD, which is also a live CD. And it gives you control on where GRUB gets installed, it just hides it behind a button...
Didn't know about the  'Alternate' Ubuntu installation CD. Sounds interesting. Will check that out.

> **Herman said:**
> 
Actually I do have one Ubuntu installation in an external USB hard drive myself and I do find it quite handy sometimes, so I don't want to say Ubuntu in a USB drive isn't a good thing. Ubuntu in a USB drive is very nice and can be extremely useful  :)

Good ;-) I agree, it's extremely useful :)
Didn't you have any of the trouble I had?


> 
sonik887, 
I agree with Scunizi, just install GRUB in all your MBRs, then you won't have any problems, 

But about GRUB installing to the wrong drive's MBR, where do these strange issues come from?
I have never had any trouble installing GRUB exactly where I want it, or replacing it with the IPL for any other boot loader or boot manager any time I want.

This is an interesting subject and there could be several possible reasons for GRUB getting installed in the wrong drive.

It always has been a little unpredictable what will happen when we have have IDE and SCSI or SATA drives plugged in to the same motherboard, (or a USB device. That's why we are provided with the /boot/grub/device.map.
                 Here is what the GNU GRUB Manual has to say on this subject, [15.3 The map between BIOS drives and OS devices]("http://www.gnu.org/software/grub/manual/grub.html#Device-map").
And here's what I've got on th so far, [**Editing GRUB's device.map**]("http://users.bigpond.net.au/hermanzone/p15.htm#device.map") (when you have SATA and IDE hard disk drives in the same machine, and Grub won't boot anything)

The odd thing about your problem, sonik887, is that you only have SATA drives, so it should have been simple for GRUB to be installed in your first hard drive.

Unless, as Scunizi suggested, your boot hard disk boot priority was scrambled up in your BIOS settings somehow maybe? [Changing the hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority").

In other case (not in this case), the reason why GRUB gets mixed up can be that we have a few people with IDE drives who sometimes maybe don't understand how to use master and slave jumper settings, or the difference between cable select IDE cables and plain ones, and where to plug in the different colored plugs. That's another cause of GRUB getting the drives mixed up, or rather, the user getting the hard drives mixed up,

What can be done about it?
Well if you want to be sure, probably you can install the IPL for GRUB to the Ubuntu partition's first sector and not to any MBR at all. 
Then when you reboot your computer, boot up with [Super Grub Disk]("http://supergrub.forjamari.linex.org/") and get a  [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and install GRUB anywhere you want from there.
If it goes to the wrong MBR then it's your own fault. :)

Or install GRUB to all MBRs like we already said. :)

Regards, Herman :)
Good to see you get it working.

You were right, it is not GRUB that mixes up the HD numbers.
> 
The problem is different detection of drives during the installation and after, ie. during the boot of the installed system. It has nothing to do with the hardware itself, rather than with (wild guessing) different kernel, different module loading/order and such from the installation disc compared to installed system.

It's not GRUB, that "mixes up" the HD numbers. It's the kernel, but the result is the same...
So you have to correct in GRUB, for what the kernel does wrong...
And that's what I experienced.

---

### Post by Herman on 2007-10-21
Well I'm disappointed.
I have been working on a computer with seven hard disks to see if GRUB would install wrong so I could learn something new. 
I have three IDE hard disks and two SATA hard disks and I plugged in another two external hard disk for good measure and tried some Gutsy Gibbon installations and everything worked perfectly.

I didn't learn anything at all. What a waste of time.

I already had Feisty Fawn in an IDE disk. I installed Gutsy Gibbon in an IDE drive, a Sata hard drive and in a USB hard drive. Not a problem.
Well the USB drive didn't boot but I didn't expect it to, the computer I'm using doesn't have a BIOS that supports booting a USB drive.

My laptop can't boot a USB directly either, but I can start GRUB in the  laptop and chainload the USB's GRUB from the laptop's GRUB.
I don't have any trouble installing Ubuntu in a USB drive at all, I just install it the regular way. It doesn't bother me too much where the IPL for the boot loader ends up. My method is to install [Super Grub Disk for USB]("http://supergrub.forjamari.linex.org/?section=download#usb").  Then I just add an entry in the Super Grub Disk for USB's /boot/grub/menu.lst to boot Ubuntu in the USB. 

I don't know why people have so much trouble with GRUB. I can simulate GRUB problems by doing things wrong on purpose, like switching my hard drives around in my BIOS, or plugging in my IDE drives wrong. That doesn't really prove anything. It makes me think probably that's why sometimes GRUB gets installed wrong, but I can't be sure of that. Everyone's computer is different.

Well, I suppose I can try editing GRUB's device.map file wrong a few times and booting to see what error messages I get, error 17 probably.

ho-hum, so ends another day...

---

