---
title: "LiveUSB install to same USB?"
date: 2008-09-19
forum: Installation &amp; Upgrades
---

### Post by bigAPE on 2008-09-19
Forgive me, I'm a Windows user.

I had a couple of spare hours yesterday in the home office and a spare 4GB Sony Micro Vault USB chip (the one the size of your fingernail) sitting around, so I decided to try out the "running Linux from a USB stick" technique.

I used an approach using UNetBootin recommended by LifeHacker.com.au. It was simple as hell.
[COLOR="DarkRed"][LIST=1]
[*]Download the ISO image from the Ubuntu website.
[*]Download the UNetBootin app.
[*]Stick the USB in the PC and run UNetBootin
[*]Point it to the USB drive and the ISO image
[*]It will unpack the ISO image to the USB stick and make the USB stick bootable
[*]Make sure your PC BIOS supports booting from USB before the Primary HD
[*]Reboot
[/LIST][/COLOR]
So here we are, I have Ubuntu (which actually looks really quite nice) running on a chip I have in my wallet and it only took 15 minutes. I can take a Linux box where ever I want!

Only ONE problem, it boots up in LiveCD mode which seems to mean that the damn thing doesn't store any changes I make to the Linux filesystem when I'm logged in! So I guess I have to now do some further "install"

There is an option to "install", which I think is what I need to do next but by default it targets the main partition of the Laptop which I obviously don't want to wipe as it's one of my dev machines running Vista. It has a Manual option which will allow me to select the USB as the destination but it says it will overwrite the entire chip with some linux partitions and filesystem, which is not what the tutorial says would happen (I don't think)

So my question is:
[COLOR="DarkRed"][LIST]
[*]Can I continue the "install" from the USB to the USB and have it overwrite the USB.. ??
[/LIST][/COLOR]
Al

---

### Post by Herman on 2008-09-19
If you had an 8 GB USB you could probably partition it and have the room to install Ubuntu in the other partition(s), but I don't think a 4 GB USB is quite big enough for two Ubuntu installations. 
You might just be able to sqeueeze them both in, but it will be a tight fit.
You will need to partition your USB first with some kind of partition editing software, (from some other operating system), because the partition would need to be unmounted when you resize it.
(Just as you can't change a flat tire on your car while you are still driving in it, you need to unmount your partition (file system), and use software running from some other system to work on it).

If you have another 4 GB or larger USB flash memory stick you might be able plug them both in and use your first Ubuntu flash memory stick to install Ubuntu in your second one.

In my opinion we can safely just install Ubuntu in a good quality flash memory stick and it will last for a long time. That's what I do. 
Reiserfs is the best file system to use in flash memory sticks.

Most other people prefer to follow the instructions at [Pendrive Linux.com]("http://www.pendrivelinux.com/"). The method used there is supposed to reduce the chances of wearing out the flash memory. It also results in a nice fast system.

---

### Post by bigAPE on 2008-09-19
Thanks for the advice Herman. 

So to sum up, no you can't run the install from a LiveCD on USB targeted at itself because it would overwrite the LiveCD in the process ? Makes sense to me.

I have a few of the older 120GB WD Passport USB HD laying around, I guess I could use one of those, install from this LiveCD/USB to the WD ? Just so that I understand, once that's done I could always reformat the WD Passport back to FAT32 using Windows at a later date is that right ?

Also, I was getting a load of error messages (don't have them to had) when trying to update/install apps using the Syntec Package Manager (spelling?). I did a lot of research and performed lots of "sudo apt-get ..." commands and a couple of "sudo dpkg --configure -a" commands but it still didn't resolve the error which seems to be related to the kernel. I assume that this was due to it running in LiveCD type mode.

Al

---

### Post by bigAPE on 2008-09-19
Thanks for the pendrivelinux.com link, an excellent resource. I think I get it now. 

What I am after is a full Ubuntu install onto a USB device, either one of my WD Passport USB HD's or a cheap 8GB USB stick. This would give me the inherent persistence that I was expecting to get by booting into the LiveUSB. 

I'm a little confused as to why anyone would use a LiveCD or LiveUSB for anything but demo purposes if the changes/data are not persistent without having to go through the complex list of command line statements listed on the various articles.

I think I'll go out an buy a cheap 8GB USB and go from there.

My only concern is the reference in [this article ]("http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/") that says:
> Important: Physically disconnect ALL internal hard drives before booting from the CD and performing the install. this will eliminate the possibility of installing to the wrong device and overwriting your MBR. Reattach the drives after completing this tutorial.
Sounds a little unsure of the ability of the installer not to bugger the other disk. Is this really an issue. Providing I point it at the 8GB USB surely I won't fry the MBR on the Primary Windows HD ?

Al

---

### Post by Herman on 2008-09-19
> I have a few of the older 120GB WD Passport USB HD laying around, I guess I could use one of those, install from this LiveCD/USB to the WD ? Just so that I understand, once that's done I could always reformat the WD Passport back to FAT32 using Windows at a later date is that right ?Yes, you could do that. :)
The only thing I worry about with an external USB hard drive is the fact that they have no fans, I don't know how they keep cool when running an operating system except by conduction maybe.
Heat is a killer for hard disks, but flash memory seems to suffer less from heat and even work faster as it warms up. I haven't actually had any heat problems running Ubuntu in an external USB hard disk, but I don't use it as my full-time operating system either.
My favorite external hard drive caddies have an aluminum housing for good heat conduction. I have one of those WD Passport USB exernal hard drives too, but so far I have only used it for data. It has a black plastic case. It doesn't seem to support S.M.A.R.T. monitoring either, so I can't check its temperature with hddtemp. It's up to you, probably it will be okay, especially if it's only for a while or to be used occasionally.
It would be simple to delete Ubuntu when you're finished and convert the hard drive back to FAT32, yes.

---

### Post by Herman on 2008-09-19
> Also, I was getting a load of error messages (don't have them to had) when trying to update/install apps using the Syntec Package Manager (spelling?). I did a lot of research and performed lots of "sudo apt-get ..." commands and a couple of "sudo dpkg --configure -a" commands but it still didn't resolve the error which seems to be related to the kernel. I assume that this was due to it running in LiveCD type mode.That's probably right, we can install software, (temporarily) when running a Live CD, the software is stored in RAM and can be run from there. I don't know for sure what happens when we try to get an update.

With a regular install of course, you can do everything the normal way. :)

---

### Post by Herman on 2008-09-19
> Thanks for the pendrivelinux.com link, an excellent resource. I think I get it now.  Yes, those are excellent, as long as you are able to follow those instructions you should be able to have a lot of fun with one of those kinds of installations.
They should be as safe as you can get from the point of view of reducing wear on your flash memory. 
It's a bit more complicated to follow all those steps, they're easy enough if you're already a Linux veteran, but if you're new to Linux they can be a challenge. You probably only need to copy and paste them though.
> I think I'll go out an buy a cheap 8GB USB and go from there.If you buy a cheap USB flash memory, then Pendrive Linux is the best.

If you shop around and take your time you can probably get a good quality flash memory for the same or only a little bit more than a cheap one and just do a regular install in it.
Look for one that supports 'ReadyBoost' so you can make your swap area in it. Some flash memory devices now have write speeds in excess of 20 MB/S and over a million erase cycles per cell before they even look like wearing out.

---

### Post by Herman on 2008-09-20
> My only concern is the reference in [this article ]("http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/") that says:
 	Quote:
 	 	 		 Important: Physically disconnect ALL internal hard drives before booting from the CD and performing the install. this will eliminate the possibility of installing to the wrong device and overwriting your MBR. Reattach the drives after completing this tutorial.  	 	 
Sounds a little unsure of the ability of the installer not to bugger the other disk. Is this really an issue. Providing I point it at the 8GB USB surely I won't fry the MBR on the Primary Windows HD ?Well, they can't be sure what kind of users are going to be trying out their instructions, maybe kids or people who don't use English as their main language, so they want to be extra careful.
If you do accidentally write some code to your MBR in your first hard disk that you didn't want there, it's pretty simple to write the code you do want back again.
'Fry' is a bit of a dramatic term. LOL. :)
It's actually quite trivial to change the code in the MBR to make it point to whichever boot loader you like. If  someone doesn't know how then I imagine it would be a little bit scray for them the first time. After you get used to it, it's no problem at all.

---

