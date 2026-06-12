---
title: "unable to find a medium containing a live file system - please help me.."
date: 2013-08-28
forum: Installation &amp; Upgrades
---

### Post by coolocelot on 2013-08-28
k so I know!! i could find like 3 posts similar to mine, there were more, but those won't apply to me!
I tried Ubuntu 12.04 64-bit and 13.04 and 13.10 all 64-bit, no luck with any of them! [URL="http://askubuntu.com/questions/15425/unable-to-find-a-medium-containing-a-live-file-system-error-when-installing"]
“unable to find a medium containing a live file system”[/URL]

So i went to the 32 bit 13.10 then 13.04, and surprize! Both worked perfectly! Now what from what I cant tell, as long as I don't need the 64-bit mode of the CPU I wont have problems, cause Ubuntu 32-bit can see my whole 8GB Ram, and I am happy, but still I don't like BUGS. In fact I hate BUGS. Even if it doesen't bother me..
So I tried changing to AHCI (I set it after Installing windows 7, cause it wouldn't install as AHCI so I changed it to IDE for the win7 installer's sake and then tweaked something in the registry so it will see the change, long story..) but I had no luck, same error! I dont have a UEFI ON/OFF switch in bios but i have this option at boot like
-UEFI: boot from USB
-boot from USB
so I tried both of them with no luck(one of them had a black screen at grub, the other the usual purple, can't remember which one of them)

How can I get the 64-bit version of Ubuntu to work? I have some linux experience, but I ain't that advanced to tweak it.. Since I can't find this error's cause..

Now the thing is I can't actually test it atm, cause my hdd went down, it's currently being replaced! (It wasn't broke at the moment of installing Ubuntu, then it was just 1 week old, and now it had almost 2 months)

System Specs:
-AMD FX X8 8350 4.0GHz
-RAM KINGSTON(2x4GB)
-GPU nVidia GeForce GT630 2GB
-MB it's a MSI (if you really need the model i'll look for it..)
-HDD SATA3 1TB Western Digital Blue 64bit buffer(2 windows partitions - 60/820GB , 1 ubuntu partition - 60GB)

Please tell me if you need something else and pardon my English :)

---

### Post by ubfan1 on 2013-08-28
Did you hashcheck (with md5sum or sha256) the 64 bit isos?  That's the most likely cause of such problems.  Never noticed any other 32 vs 64 bit installation issues.

---

### Post by coolocelot on 2013-08-29
I did not hash check them, but how could it happen that from 4 iso's, a  32-bit 13.04 and 12.04, 13.04 and 13.10 64-bit only the 32-bit one  worked? But you know what, I can try the iso's without the HDD! I'll  test this right away and return with the results!

And sorry for the other post..
NVM, Ubuntu 13.04 is up again.. Downloading it now..

---

### Post by coolocelot on 2013-08-29
It seems 13.04 wont boot from usb made by universal usb installer.. going to do it by ubuntu make startup disk.

---

### Post by coolocelot on 2013-08-29
Okay, now I'm confused, cause it worked... I suspect that the problem was the software I used for making the LiveUSB. I always used uNetBootin and/or Universal USB Installer.. But now I used the Ubuntu Startup Disk Creator, and it booted up in 5 secs from a usb3 port using UEFI so i'm just gonna thank you for your help! Now I just gotta figure out how to close this thread...
This may be usefull to other people too.. I prefer to think I'm not the only one that used Windows for the LiveUSB...

---

### Post by jeff19 on 2013-08-29
I had this problem and tried many of the solutions suggested which did not work. I have an older PC with an IDE DVD Drive. In BIOS the drive was configured as the secondary master (this was the only IDE device and there was no primary master). I changed the jumpers on the drive to make it the primary master. This solved the problem.

---

### Post by flipdazed on 2013-11-07
double post

---

### Post by flipdazed on 2013-11-07
This might help someone diagnose the issue...

I have 2x HD's and 1 SSD in my PC.
I have windows 7 installed on the SSD and a free partition on one HD that I am trying to install Ubuntu onto.

I receive the same error as above when all drives are connected. When I physically disconnect the SSD and other HD, I can install Ubuntu perfectly fine...

---

### Post by fabienwahl on 2013-11-24
Installing ubuntu from USB into Oracle VM. 
a/ use unetbootin-windows-585 to create a ubuntu 13.04 bootable usb disk (do not select a 64bit version, see end of post)
b/ create a virtual disk in VM pointing at the usb disk
see [http://www.pendrivelinux.com/boot-a-usb-flash-drive-in-virtualbox/](http://www.pendrivelinux.com/boot-a-usb-flash-drive-in-virtualbox/)
but correct the second command (remove quote/unquote around %userprofile%) to 
[COLOR=#333333][FONT=Lucida Grande]**VBoxManage internalcommands createrawvmdk -filename %USERPROFILE%\.VirtualBox\usb.vmdk -rawdisk \\.\PhysicalDrive**[/FONT][/COLOR][COLOR=#FF0000][FONT=Lucida Grande][B][B]#
[/B][/B][/FONT][/COLOR]c/ add a supplementary storage drive in the VM (where to install ubuntu). Make sure that this drive is after (in the order of boot) the usb disk. Typically, install it as a second sata drive, at port 1, while the usb drive is at port 0.
d/ start the VM and install ubuntu.

Note: the above did not work with a ubuntu 64bit version... I ended up with the message
ubuntu cannot find medium live file system
described in the posts

---

