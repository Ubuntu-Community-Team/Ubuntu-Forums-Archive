---
title: "Bootable USB Problems"
date: 2012-01-09
forum: Installation &amp; Upgrades
---

### Post by mechanid72521 on 2012-01-09
Hey all!  

I'm brand new here.  I have used Ubuntu in the past, and with no problems.  I've been thinking about switching over to Ubuntu use full time, but this recent bit of history has pushed me over the edge to make the switch.

I acquired a laptop running Windows XP.  It belonged to my step-sister's father and it came chalk full with viruses.  I decided to wipe it all and use an XP home edition black disk to rebuild the machine.  After trying to jump through the maze of Windows Service Packs and .net Framework versions, I got fed up and decided to switch on over to Ubuntu for good.  

I followed the necessary steps off of the main Ubuntu website to create a bootable USB.  The USB had the U3 Launch Platform which I promptly removed with the SanDisk U3 remover.  I then used the program suggested from the main site and wrote the .iso image to the USB (F: drive).  Checking the USB drive, it is labelled as "Install Ubuntu" and has all the files necessary on it.  I restarted the computer and went to the boot menu and chose to boot from my USB.  The screen went dark for a few seconds, showed the little underscore flashing, and then went right to the XP Home Edition splash screen.  It completely ignored everything on the USB!  I tried again with UNetbootin, and this time, Windows decided to check the drive, and told me there were no problems with it... but then proceeded to load Windows XP again.  

Any fixes for this?  Any help would be much appreciated.

Thanks!

---

### Post by mechanid72521 on 2012-01-09
Please?  Anyone at all?

---

### Post by Basher101 on 2012-01-09
did you set your BIOS to boot from USB? it does not matter what device is attached, if the BIOS is not configured to boot it, it wont do so.

note: your laptop may not support USB boot, in that case you must use a (much slower) CD.

---

### Post by mechanid72521 on 2012-01-09
Ah, yes.  The first thing I did was to set the boot order to USB drive first.  It gives the same results.  As a side note, I am trying to run Ubuntu 11.10.

edit: It gives me to the option to boot from USB.  I'm assuming that doesn't necessarily mean it will do it.  Are there drivers for this?  Or is CD the only option?

---

### Post by Basher101 on 2012-01-09
thats odd...what version of ubuntu do you want to install? 32 or 64 bit? if you have the 64 bit version it might not boot. Try it with the 32 bit version and use the Universal USB installer from [www.pendrivelinux.com](www.pendrivelinux.com) i have never had any problems with it whatsoever.

---

### Post by mechanid72521 on 2012-01-09
I downloaded the 32-bit version.

---

### Post by mechanid72521 on 2012-01-09
As of now, I am reformatting my USB drive, and applying Ubuntu 11.10 back to it using the Universal USB Installer again.  That was my first attempt, but we'll see if it goes better this time.

---

### Post by Basher101 on 2012-01-09
> **mechanid72521 said:**
> As of now, I am reformatting my USB drive, and applying Ubuntu 11.10 back to it using the Universal USB Installer again.  That was my first attempt, but we'll see if it goes better this time.

hopefully. if it still does not work, try a different USB stick perhaps?

---

### Post by mechanid72521 on 2012-01-09
That may be the ticket.  We'll see what happens.  Thank you very much for your suggestions!  I'll post back here with an update.

---

### Post by mechanid72521 on 2012-01-09
Well, it turned out to not work on my computer.  What I don't understand is why I could have a USB boot option and it ignores it.  

So, I got suspicious.  I plugged the USB drive into my girlfriend's laptop and went to boot from USB.  Sure enough, it worked.  This is a Toshiba Satellite A105.  Dates to around 2004, if I'm correct.  I don't have high speed USB ports, nor do I have most of the windows updates because of just how ridiculous they are to obtain and I just wiped everything in an attempt to rebuild the machine.  Like I mentioned above, I can't get the updated Service Packs without the updated .net Framework, which requires the same Service Pack I'm updating the .net Framework to get.  

I don't much care about that, but if it's required that I update that just to get my USB to work as a bootable device (which like stated above, works on a different laptop) then I'm probably SOL.  

Any necessary drivers I can get away with that will allow me to boot from USB?

---

### Post by mastergkage on 2012-01-09
Since your trying to install Ubuntu into an old laptop maybe the usb port is broken? keep usa posted.

---

### Post by kurt18947 on 2012-01-10
I don't know if this will help you but here is my experience.  I created different live USB installs on different USB drives using Unetbootin and Ubuntu's Startup Disk Creator.  They would boot fine on most machines, they would not boot on my desktop.  I'd get a "boot error" message or other failure.  Tried deleting and recreating the FAT32 partition using GPARTED, made no difference.  

Googled around and found that certain BIOSs would only boot from Windows formatted USB drives. I then formatted the USB drive in Windows 7 and  used Unetbootin to create a live USB.  Restarted and the USB drive booted.  I'm not knowledgeable enough to be able to determine what is different between a Windows FAT32 formatted USB drive and a GPARTED format but there is *something* different.  One posting indicated that the Award Modular BIOS boot portion was written by Microsoft and if true, who knows what undocumented changes are there.

---

### Post by varunendra on 2012-01-10
@mechanid72521,

Is there a specific reason why you can't (or don't want to) try a cd?

If the laptop in question does not have high speed usb ports (aka USB-2), then most probably its BIOS does not have the capability to boot from a USB flash drive. The 'USB-boot' option may only be sitting there for generic USB devices like USB-Floppy drive / hard-disk drive or USB CD drive. I believe even a modern USB flash drive 'emulates' one of these devices while being detected as a 'bootable drive', but the BIOS has to be capable of reading and understanding that 'emulation' (but this is my assumption only, I don't have any authentic source to backup this theory).

Having said that, let's try a step-by-step solution:

> **mechanid72521 said:**
> Well, it turned out to not work on my computer.  What I don't understand is why I could have a USB boot option and it ignores it. Sometimes, even if the BIOS can boot from a USB flash drive, the drive may get listed under other catagories (like Hard Disk, floppy etc. - due to its 'emulation-type' I believe.). For example, most of my bootable flash drives get listed under hard-disk drives catagory in BIOS of most of the motherboards. Accordingly, press the shortcut key for the boot menu while booting (apparently it is F12 for your laptop as per a quick google search), and check each catagory to see if your USB drive is listed there by its brand/model name. If not, do a 'hot reboot' to retry at least once for each category. (Sometimes, the detection time for a usb flash drive exceeds the time BIOS can wait for it. A hot reboot most often solves this).

If the above attempts fail permanently (suggesting the BIOS is incapable of booting from a usb flash drive at all), you may wish to try '[Plop]("http://www.plop.at/en/bootmanager.html")'. Download its latest boot-manager zip file from [here]("http://www.plop.at/en/bootmanagerdl.html"), then:

[LIST=1]
[*]extract the iso file from the zip file
[*]burn it to a cd (as told [here]("https://help.ubuntu.com/community/BurningIsoHowto"))
[*]boot from the cd
[*]plug-in the usb flash drive
[*]select to boot from the USB
[/LIST]
But since the above method also involves burning and booting from a cd, you will be better off with burning a cd for ubuntu itself and installing from it.

 

Oh, and about your question about xp updates/drivers:
> **mechanid72521 said:**
> I don't much care about that, but if it's required that I update that just to get my USB to work as a bootable device (which like stated above, works on a different laptop) then I'm probably SOL.  

Any necessary drivers I can get away with that will allow me to boot from USB?
No!
As a matter of fact, all those updates/drivers come to the scene AFTER the OS loading process has already been started/finished. So they have nothing to do with the initial boot stages where the BIOS selects the device to boot from. It is same for all operating systems. (Even Plop is no exception to this. It just acts as a temporary intermediate boot-loader program with suitable drivers/device-configuration to allow loading of the OS from a USB drive even though BIOS does not support it).

Hope you find it helpful.

---

### Post by mechanid72521 on 2012-01-10
Thank you all for your suggestions and help!  As it turns out, I was able to get a hold of a blank CD and just burned the .iso image to it, and it booted just fine.  I am now running Ubuntu 11.10.  I don't know why I was so gungho to get the USB to work.  Maybe it was because I was at my wits end already dealing with Microsoft hoops and mazes that I just wasn't really ready to handle another problem, especially one I can't do anything about at this time (age of computer).  

You guys were a big help though, and I appreciate it!  I'll see you guys around the forums!

---

### Post by Basher101 on 2012-01-10
> **mechanid72521 said:**
> Thank you all for your suggestions and help!  As it turns out, I was able to get a hold of a blank CD and just burned the .iso image to it, and it booted just fine.  I am now running Ubuntu 11.10.  I don't know why I was so gungho to get the USB to work.  Maybe it was because I was at my wits end already dealing with Microsoft hoops and mazes that I just wasn't really ready to handle another problem, especially one I can't do anything about at this time (age of computer).  

You guys were a big help though, and I appreciate it!  I'll see you guys around the forums!

so in the end the usb did not work eh? at least you got it running^^ CD may be alot slower, but is easier to set up (e.g. burn)

have fun with ubuntu!

---

### Post by Mark Phelps on 2012-01-12
Since you got it working OK, please use the Thread Tools at the top of the thread to mark this as SOLVED.  thanks

---

