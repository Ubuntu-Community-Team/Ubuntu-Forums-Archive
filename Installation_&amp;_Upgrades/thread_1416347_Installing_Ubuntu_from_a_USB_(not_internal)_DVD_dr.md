---
title: "Installing Ubuntu from a USB (not internal) DVD drive"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by PeterChris on 2010-02-26
Is there any problem with installing Ubuntu from a USB optical drive  versus an internal one connected directly to the motherboard?

I just put together a new computer (Intel Atom D510 motherboard,  no operating system yet, brand new hard drive and NO optical drive).   

I'm trying to install Ubuntu on this new, unformatted hard drive.   (I've tried UnetBootIn but it doesn't work---I have another post about that).

Thanks.

---

### Post by mikewhatever on 2010-02-26
If you are using an Ubuntu installation cd with a USB optical drive, it should work. What baffles me is the notion of Unetbootin. What do you use that for?

---

### Post by PeterChris on 2010-02-26
Before I realized I had an external USB DVD drive available, I had only thought of trying to install Ubuntu via a USB flash drive (I think people often use the term "USB Stick"----I have a 2GB Crucial Gizmo, among others).

I used Unetbootin to create a bootable USB stick but could never get past the initial menu screen on the new pc.    In theory, I really liked the idea of Unetbootin as I'm not crazy about burning CDs.    But, I could never get Unetbooin to do anything other than display a menu screen and even that required manually renaming files/folders. 

I should have built this pc with an optical drive as Ubuntu seems to install better that way.

---

### Post by darkod on 2010-02-26
It should be fine installing from usb cd. I'm only not sure if you have to go into BIOS and set it in the boot device order. In some BIOSes you have separate name as USB-CDROM or similar, while on others I guess it would go under the same CDROM category as internal drives.

As for unetbootin, I also like the idea of not burning cds. The menu unetbootin is trying to set up can be messy. Usually I get rid of it and enable the main ubuntu menu. When creating the stick use the standard Disk Image option, after it's done ignore the question to reboot, just close unetbootin. Then open the stick and do:
1. In the root folder rename syslinux.cfg to syslinux.old
2. In the folder isolinux find and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
3. Go back and rename the whole folder isolinux to syslinux

That will enable the main ubuntu menu just like booting from the cd, so you'll have Try Ubuntu, Install Ubuntu, etc.

---

### Post by PeterChris on 2010-02-26
Hi darkod,

Thanks for the reply.   I had stumbled on one of your prior postings on just how to do what you outlined here----renaming the files/folder on Unetbootin.    After doing that, I was able to see the Ubuntu logo and menu options.  From the menu,   I tried both running it Live and also doing an Install but each time, I would get a black screen.    

I'd really like to get Unetbootin to work for me as it seems an elegant solution instead of burning a CD.   But, I wonder how stable Unetbootin really is, especially given that you have to rename a bunch of files/folders just to get it to work, and even doing that doesn't get it to work for me.   I didn't see anything about renaming the files/folders on their Sourceforge page.   

My goal is just to get Ubuntu installed on this new PC I've built (onto it's new, unformatted hard drive).   I'm not interested in running it in memory.   I'd really appreciate it if you could lead me in the right direction of getting Unetbootin working.

---

### Post by ubunterooster on 2010-02-26
turn on pc and hit key to choose boot device(one of mine requires me to press esc another F9 another F11). see if the cd drive is there.

---

### Post by darkod on 2010-02-26
> **PeterChris said:**
> Hi darkod,

Thanks for the reply.   I had stumbled on one of your prior postings on just how to do what you outlined here----renaming the files/folder on Unetbootin.    After doing that, I was able to see the Ubuntu logo and menu options.  From the menu,   I tried both running it Live and also doing an Install but each time, I would get a black screen.    

I'd really like to get Unetbootin to work for me as it seems an elegant solution instead of burning a CD.   But, I wonder how stable Unetbootin really is, especially given that you have to rename a bunch of files/folders just to get it to work, and even doing that doesn't get it to work for me.   I didn't see anything about renaming the files/folders on their Sourceforge page.   

My goal is just to get Ubuntu installed on this new PC I've built (onto it's new, unformatted hard drive).   I'm not interested in running it in memory.   I'd really appreciate it if you could lead me in the right direction of getting Unetbootin working.

Unfortunately not being able to run live usually means video driver issue. Boot again and at the menu hit F4 for more options, select Safe Graphics, and after that Try Ubuntu if you need to. See if that will load the live desktop.

Yes, unetbootin is far from perfect. But it seems the easiest way to create bootable ubuntu usb stick from windows, so we have to accept its faults. That small procedure allows you to enable the ubuntu menu and all should work fine after that. I'm pretty sure your issue is not with unetbootin.
The thing is unetbootin was not designed for ubuntu only. It takes a bootable ISO and creates bootable usb stick so they had to cover ISOs for other OSs too. I guess that was the reason to try to create simple menu that should start the installation. But the work around is much better because it enables the selection of Try too.

---

### Post by PeterChris on 2010-02-26
Darko,  I just tried hitting F4 when I see the menu but nothing happens.  The menu just stays on the screen.   The menu I'm seeing has the Ubuntu logo at the top and below that is says: 

Installer boot menu
Try Ubuntu
Install Ubuntu
Check disc
... and several other options.    

I was only able to see this menu AFTER I did your trick of the renaming files & the one folder.    If I just run the USB Stick exactly how Unetbootin made it for me, I'd see another, simpler menu with only three options (Default, Help and oem install----all of which, when chosen, made the screen go blank).   

There is a 30 second count down happening at the bottom of this menu.     If I choose either of the first two options (Try or Install), it starts loading some "casper" stuff and then the screen goes blank.   If I do nothing and wait 30 seconds, it does the same thing. 

How would I get that F4 display option to appear?

---

### Post by darkod on 2010-02-26
I'm sorry, it seems there is a small difference because it was created by unetbootin. Now I remember someone else also saying the F4 option were not displayed at the bottom of the screen under the menu.
So I guess that procedure with renaming the files only allows to get the main menu, but not more advanced options.
Maybe burning a CD and using the external drive is the right way to go in this situation.
Unless you can actually create the usb stick on another ubuntu computer where you can use the USB Startup Disc creator in System-Administration. That will be with full options.

---

### Post by recluce on 2010-02-26
Just a quick reminder: booting from an USB CD-ROM is entirely at the mercy of your BIOS. It will either work or it won't. If it doesn't, there may be BIOS settings that can be changed or there may be a newer BIOS. For example, my Dell Latitude D830 needs BIOS A15 to support booting an external optical drive.

---

### Post by ubunterooster on 2010-02-26
Not "entirely"; some few are not bootable

---

### Post by PeterChris on 2010-02-26
Thanks guys.   I decided to take Darko's advice and forget Unetbootin.   I used InfraRecorder on my Windows XP machine to easily burn a CD using this I/O Magic external USB DVD drive I've had for a few years.    It worked perfectly the first time. 

I then plugged the USB DVD drive into the new pc (onto a motherboard USB slot, not a case slot), booted (I hit F10 for boot options but not sure it was necessary) and it pulled up a far more comprehensive Ubuntu menu, including the options along the bottom (I had not seen any of that over the last few frustrating days of trying to get Unetbootin to work).   I hit F4 and chose the reduced display options (or whatever it said) and everything during the installation went fine.    I did NOT change any BIOS settings from what I had set for trying to boot with the USB stick made with Unetbootin.   I suppose that's because, even though I'm using a CD now, I'm still using booting using USB.   

Thanks very much for the help.

For anyone struggling with a USB stick installation, I'd recommend just getting an external USB DVD drive and do the installation from a CD.   You'll then have the external drive to use for other things later.

---

### Post by recluce on 2010-02-26
> **ubunterooster said:**
> not "entirely"; some few are not bootable

:?: :?: :?:

---

### Post by ubunterooster on 2010-02-26
@recluce: been recntly reading up on old usb connected cd drives. the idea's been around quite a while, some older ones were not bootable
[the ones were USB type1] you never know what sombody's using 'till they tell you

---

### Post by recluce on 2010-02-27
> **ubunterooster said:**
> @recluce: been recntly reading up on old usb connected cd drives. the idea's been around quite a while, some older ones were not bootable
[the ones were USB type1] you never know what sombody's using 'till they tell you

OK, that makes it easier to understand. So basically, there are some (ancient) USB bridges out there that don't work. Actually, I don't find that surprising...

---

