---
title: "Cannot install Ubuntu Server 10.10 on new custom computer"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by davidtlc on 2011-03-18
alright gang, this problem is driving me nuts.
I built a computer the other day (I'm a newb at all this, so I'm not ruling anything out here)

Specs: 

4 GB (2x2GB) Corsair Ram Kit 1066MHz
1TB Western Digital 'Green' HDD (a couple of years old, but I think it's still good - see below)
Gigabyte GA-G41MT-D3 Motherboard
Intel Xeon X3330 Processor
Antec 750W psu
LG Blu-Ray/DVD/CD Reader/Writer w/Lightscribe and all the goodies

Alright, so I put all the components together, and took a look at the Bios, everything looked fine, all the components were recognized, so I shut down, took a freshly created bootable USB stick with Server 10.10 on it, (and yes, I already checked the MD5 from the download). I was 100% able to install it on my Acer Aspire Laptop no problem, and it's still running fine now.

Plugged the USB into my new computer, and booted from it no problem. Part way into the install (and it would vary every time) a file would report being corrupt or not found. 

Recreated the USB stick from the install of Ubuntu I did with the original one, and tried again, same problem. This is when I definitely started to come up with the theory that it's the hardware in my new rig. 

the first thing I suspected was the RAM. I had 4 sticks kicking around, so I tried a memtest on all of them individually and in the different slots, they all checked out as being fine - ruled that out

then I thought it might be a bad PSU (the one that came with the case was 275W) - got the new one, and still hitting the brick wall.

the next variable to eliminate was the Blu-Ray drive (because in the mean time, I burned a disc that checked out on the Acer laptop I burned it from, no issues, but still wouldn't install). I have a SATA - USB enclosure that the hard drive originally came in (I took it out to increase my Acer Home Server and it's worked fine the last year and a half), so I hacked it a little (removed the PCB from the hard-drive cage and used it to power/interface my Blu-Ray Drive with my laptop (again with Ubuntu Server). Ran the disc verification tool on the disc (and it had failed in the new computer - only change was putting it through USB to another computer)), but miraculously it passed in the new disc drive, so I eliminated that from the equation.

The last check was the Hard Drive. I couldn't get any O/S installed to it in the new rig, but when I plugged it in via usb to my laptop, I could install Ubuntu to it without issue and boot to it with no hassle. When I got this drive back in to the new rig, weird errors started to pop up. the repositories randomly became corrupted, the permissions on files changed radically, and it got to the point it would be too unstable for me to get anything I needed set up done. I repeated this process, including formatting it to a few files systems, and still ended up with weird bugs (all of which seemed Random).

The only things left are the CPU and Motherboard. I tried installing the Ubuntu Desktop from the LiveCD, but while it worked flawlessly on my acer laptop - and burned with the same LG unit that was to install it in the new computer, however I ended up with a busybox initramfs terminal and was unable to do anything.

It seems like I've thrown every combination at this thing trying to make it work (even unsuccessfully tried to install Windows (XP, Vista, 7), which all came up with various errors, usually around the file extraction stage of the install wizard.

Any help would be greatly appreciated, this issue has driven me nuts for the last 2 days...

One other thought - The processor supposedly fits into the Intel 3210 Chipset, however the Board is built around the Intel G41 Chips - but both are LGA775 sockets - is that an issue? and how can I test my hardware if I can't get any OS installed?

If I think of anything else important, I will let you guys know. 

Cheers

---

### Post by targets on 2011-03-18
i have been going thru the same punishment so i cant help you, just commiserate

---

### Post by carolinabranden on 2011-03-18
If your able to access your bios, then I highly doubt it is the critical hardware components. 

[LIST] 
[*]**Have you listened to your case speaker?**
*You might have to call technical support to get the definitions. Gigabyte provided them, but ASUS didn't for me. Your case speaker could tell you what is going on. Sometimes it is something simple causing the system not to kick in.*
[*]**Cleared CMOS?**
[*]**Tried other HDDs/SSDs?** 
   **Have you tried RAID 0 or 1?**
*Hakunka might be onto something here. I've read that people have had problems running Linux server with AHCI.* 
[*]**Does the ISO match with the hardware?** 
   **Which distro are you using?**
*It happens. Linux can run on just about any computer, but you still have to match everything up. Years back an old computer of mine could neither run KDE nor GNOME without problems. Not trying to insult you because we all make mistakes.*
[*]**Have you test driven non-Linux OSs such as Windows or BSD?**
[/LIST]

---

### Post by mörgæs on 2011-03-18
Have you tried some other distros like Puppy and Knoppix? I know that the chances are slim, but it is an easy test.

---

### Post by Hakunka-Matata on 2011-03-18
> The last check was the Hard Drive. I couldn't get any O/S installed to  it in the new rig, but when I plugged it in via usb to my laptop, I  could install Ubuntu to it without issue and boot to it with no hassle.  [COLOR=Magenta]When I got this drive back in to the new rig, weird errors started to  pop up. the repositories randomly became corrupted, the permissions on  files changed radically, and it got to the point it would be too  unstable for me to get anything I needed set up done. I repeated this  process, including formatting it to a few files systems, and still ended  up with weird bugs (all of which seemed Random).[/COLOR]

The only things left are the CPU and Motherboard. I tried installing the  Ubuntu Desktop from the LiveCD, but while it worked flawlessly on my  acer laptop - and burned with the same LG unit that was to install it in  the new computer,[COLOR=Magenta] however I ended up with a busybox initramfs terminal  and was unable to do anything.[/COLOR][COLOR=Magenta]

[/COLOR]BIOS: - SATA disc controller settings maybe?  AHCI (is a problem on my machine,) - Large - SATA standard?

Boot to Ubuntu install USB and choose "Try Ubuntu" maybe.  That will obviate the requirement of installing to Hard disc.  The USB stick is the hard disc in that configuration, and memory on your Main Board is used, but not the drive.  If it works like that, you would then have a stable Ubuntu platform from which to check out the drive, GParted, etc.

---

### Post by davidtlc on 2011-03-18
> **carolinabranden said:**
> If your able to access your bios, then I highly doubt it is the critical hardware components. 

[LIST]
[*]**Have you listened to your case speaker?**
*You might have to call technical support to get the definitions. Gigabyte provided them, but ASUS didn't for me. Your case speaker could tell you what is going on. Sometimes it is something simple causing the system not to kick in.*
[*]**Cleared CMOS?**
[*]**Tried other HDDs/SSDs?** 
   **Have you tried RAID 0 or 1?**
*Hakunka might be onto something here. I've read that people have had problems running Linux server with AHCI.*
[*]**Does the ISO match with the hardware?** 
   **Which distro are you using?**
*It happens. Linux can run on just about any computer, but you still have to match everything up. Years back an old computer of mine could neither run KDE nor GNOME without problems. Not trying to insult you because we all make mistakes.*
[*]**Have you test driven non-Linux OSs such as Windows or BSD?**
[/LIST]


Well, the case speaker has given nothing but a single beep on startup, so nothing has gone catastrophically wrong there, and I have cleared the CMOS, and checked the battery level of the CR2032 on the board, and it seems to be good (~2.8V).

I don't have another hard drive to test on, but I might just pick one up on my way home to test on, but I had my BIOS set the drive automatically, and I'm pretty sure it defaulted to Large, but I will check that as well.

Also, Hukunka, I didn't even get the option to run the live disc. The ubuntu logo came up and started to load, but it got to the busybox console before I could get to a menu.

I have also tried to install windows (I have XP, Vista, and 7) and all versions failed. I've never done any of this before, so maybe I have to load some drivers for the board or something (the board is advertised as Win7 ready), but being a Newb, I have no idea what to do there, so any help is appreciated.

I've only tried 10.10 (server and desktop edition), but I will give another distro a shot as well and report back if anything changes.

Cheers

---

### Post by Hakunka-Matata on 2011-03-18
[LIST]
[*]BIOS SETUP:  **DISABLE ON CHIP SATA CHANNEL **if you suspect SATA configuration or missing drivers for your hard disc are screwing up the LiveCD installer.  This will allow your LiveCD install USB, PXE, DVD, or CD to boot w/o concern for Hard Disc requirements.  It might help some of you get by the busybox initramfs errors.
[*]Then, if it will boot and run a Live system using only the Install medium and RAM, you've proven something.
[*]Then go back into BIOS SETUP and turn on **ON CHIP SATA CHANNELL**, (**ENABLED**)
[*]**ON CHIP SATA TYPE **choices for my AMI BIOS are : **SATA, RAID, AHCI = CHOOSE SATA **(or equivalent if your BIOS presents different choices)
[*]**ACPI 2.0 SUPPORT, **mine is enabled and works, yours may not.
[*]**ACPI APIC SUPPORT, **mine is enabled and works, yours may not.
[*]>                      Originally Posted by **carolinabranden**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10573092#post10573092")
[/LIST]
>                   [I]If your able to access your bios, then I highly doubt it is the critical hardware components. 

[LIST]
[*]**Have you listened to your case speaker?**
*You might have to call technical support to get the definitions.  Gigabyte provided them, but ASUS didn't for me. Your case speaker could  tell you what is going on. Sometimes it is something simple causing the  system not to kick in.*
[*]**Cleared CMOS?**
[*]**Tried other HDDs/SSDs?** 
   **Have you tried RAID 0 or 1?**
[LIST=1]
[*]*Hakunka might be onto something here. I've read that people have had problems running [COLOR=Red]Linux server with AHCI.  [/COLOR]*
[/LIST]
 
[*]**Does the ISO match with the hardware?** 
   **Which distro are you using?**
*It happens. Linux can run on just about any computer, but you still  have to match everything up. Years back an old computer of mine could  neither run KDE nor GNOME without problems. Not trying to insult you  because we all make mistakes.*
[*]**Have you test driven non-Linux OSs such as Windows or BSD?**
[/LIST]
[/I]
    
[LIST=1]
[*][COLOR=Red] AHCI affects 10.10 32bit Desktop LiveCD installer also, not only Server[/COLOR][COLOR=Red].  RAID 0 or 1 will break the 10.10 32bit LiveCD installer - [won't find disc?, or just won't find partitions?, don't remember exactly - need to find a thread detailing it][/COLOR]
[/LIST]
 

[LIST]
[*] > [COLOR=Indigo]Also, Hukunka, I didn't even get the option to run the live disc. The  ubuntu logo came up and started to load, but it got to the busybox  console before I could get to a menu[/COLOR].
[/LIST]

[LIST]
[*][COLOR=Indigo]davidtlc:  Hit ESC key when you first see purple screen[/COLOR]
[/LIST]

---

### Post by davidtlc on 2011-03-18
I will give those a shot later this afternoon, but I have to wonder: why would the disc integrity verification pass on two different computers using 3 different drives (one in each of my laptops and one that i am going to be installing in this server when I get it running), yet fail when I run it on the same disc drive on my new hardware? (the error that always  comes up is usually a failed check of Packages.deb - md5 checksum does not match).

are any files being written to the hard drive during this test?

---

### Post by Hakunka-Matata on 2011-03-18
One Possibility is because the BIOS and Disc Controller hardware & firmware are part of the motherboard, nothing to do with the disc itself.

That's the reason for Disabling the SATA controller, (& thereby of course any discs attached to it) and seeing if the the rest of the hardware is happy with the Installation.

If you disable the SATA Disc controller, assuming you're working with SATA drives, you'll notice when the machine boots BIOS will report NO hard drives are present.  So it does not even attempt to control them.

Divide and Conquer

---

### Post by carolinabranden on 2011-03-18
[quote="Hakunka-Matata"]AHCI affects 10.10 32bit Desktop LiveCD installer also, not only Server. RAID 0 or 1 will break the 10.10 32bit LiveCD installer.[/quote]

Software/Hardware Raid 0, 1 are possible. I've ran a rig with it, but that's just me. (^_^) 


[list]
[*][Advanced Installation](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html)
[*][InstallationSoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
[*][How to install software RAID](http://ubuntuguide.org/wiki/Ubuntu:Feisty/Hardware#How_to_install_software_RAID)
[*][Hardware RAID 1 on Ubuntu](http://codeghar.wordpress.com/2007/11/26/hardware-raid-1-on-ubuntu)
[/list]

---

### Post by Hakunka-Matata on 2011-03-18
[LIST=1]
[*]> [COLOR=Red]AHCI affects 10.10 32bit Desktop LiveCD installer also, not only Server[/COLOR][COLOR=Red].   RAID 0 or 1 will break the 10.10 32bit LiveCD installer - [won't find  disc?, or just won't find partitions?, don't remember exactly - need to  find a thread detailing it][/COLOR]
[/LIST]
> Software/Hardware Raid 0, 1 are possible. I've ran a rig with it, but that's just me. (^_^)  
[LIST=1]
[*]@ carolinabrandon:  Last thing I want to do is confuse the OP.  So tell me what release?, 32 or 64 bit, and what installer, LiveCD or Alternate did you install a RAID 0, & RAID 1?  If I'm wrong, I'm wrong,
[/LIST]
thanks for the input, HK

---

### Post by carolinabranden on 2011-03-18
I did on a past rig: Gigabyte mobo, Pentium 4 570J (32-bit), Seagate 500GB HDD and etc... while I was experimenting with different distros. It is not worth it for general purpose computers. Now maybe for Windows gaming, but other than that it is not going to make much of a difference anyhow. The rig I am using right at the moment is in my signature. Using a 500GB Western Digital instead of a Seagate. Had a Seagate HDD become  corrupted in Windows and had to throw it away. That's one of the reasons why I am becoming more keen toward Linux or Unix-based OSs. I had mentioned raid to see if it could help his rig work. lol It is near about impossible to accurately diagnose someone else's computer without actually being there. Still don't mind helping nonetheless. :popcorn:

---

### Post by Hakunka-Matata on 2011-03-18
My reason for being on this thread is to help (if I can) davidtlc get his system up and running.  Sorry for digressing............

@carolinabranden.
You haven't said anything about version numbers, alternate or liveCD, Desktop or Server. 

example of some of the different RAID types, lots of variables.
> From Official Ubuntu Website:

There are three ways to create RAID: 

[LIST=1]
[*]Software-RAID: Where the RAID is created by software.
[*]Hardware-RAID:  A special controller used to build RAID. Hardware RAID is generally  faster, and does not place load on the CPU, and hardware RAID can be  used for any OS
[*]FakeRAID:  Since RAID hardware is very expensive, many motherboard manufacturers  use multi-channel controllers with special BIOS features to perform  RAID.
[/LIST]


---

### Post by davidtlc on 2011-03-18
Alright, update.

I bought a new Hard Drive (never a bad thing to have in any case) - a 1Tb Western Digital Caviar Black.

After I installed it, I booted the computer, switched SATA off, and then rebooted to USB (I have one of the server distro and 1 of the desktop, both Maverick (10.10). The desktop usb would give me the menu, but when I selected to run the live version, it hung on the Ubuntu loading screen with 5 dots (dots were moving, but nothing happened) - I hit escape and it threw a number of errors regarding being unable to mount or access Packages.deb. I ran it again, this time with SATA enabled, and it hung again, this time throwing an error (glib-warning getpwuid_r failed due to unknown user id(0) or something).

I also burned a live cd of 9.10 on my laptop at the slowest speed using Xfburn, but it showed 10 errors when I verified it, and the live option is hanging, with the CAPS and SCROLL lock lights on the keyboard flashing

I've basically eliminated everything but a FUBAR motherboard, or CPU... I have a (more) compatible CPU coming in the mail, but if I keep getting these errors, I'll have to RMA the motherboard

---

### Post by Hakunka-Matata on 2011-03-19
Looking @ gigabyte.com/support on CPU list for your 
     Socket 775 - Intel G41 - GA-G41MT-D3 (rev. 1.3)

Main Board, and I do not see your CPU listed.
[http://www.gigabyte.com/support-downloads/cpu-support-popup.aspx?pid=3476](http://www.gigabyte.com/support-downloads/cpu-support-popup.aspx?pid=3476)

Check it out

---

### Post by davidtlc on 2011-03-19
Yeah, I noticed that too (it had the same specs as the Core 2 Quad 9400) I think, so I tried the Xeon chip.

I have an order in transit for a Core 2 Quad Q8400, which is on the list.

thanks for helping me troubleshoot this, and hopefully the right processor will fix all these issues.

Cheers

---

### Post by Ranko Kohime on 2011-03-19
> **davidtlc said:**
> ...and checked the battery level of the CR2032 on the board, and it seems to be good (~2.8V).
~2.8V on a 3V battery is DEAD.  I wouldn't think that the CMOS battery would have an effect on the system, but it can't hurt to swap it out, or even run without it.

Voltages on a 3V battery should be more like 3.2-3.3V

---

### Post by davidtlc on 2011-03-23
Well, I got the new CPU in the mail, and tried it out. I seemed to have better luck making its way through various o/s installs, but they would all fail or hang (Win XP and Vista, Ubuntu 9.10 desktop, 10.10 desktop, 10.10 server), and I tried on 2 different optical drives and various USB flash drives. I'm running out of ideas here outside of something on the motherboard being toast, but I can't see any glaring problems that would indicate a hardware issue... this is driving me insane

---

### Post by Hakunka-Matata on 2011-03-24
Hey, sorry to hear you're going crazy, at least you're being driver though, that's the easy way.  I drove myself crazy.



[LIST]
[*] maybe some leads can be found in the log files?
[*]Have you tried all sorts of different BIOS settings?
[*]Have you checked for BIOS updates?
[*]Have you found any evidence of your MOBO being a piece of (*#&$ on the interweb?
[/LIST]

---

### Post by davidtlc on 2011-03-25
Good News! I swapped out my motherboard with a new ASUS P5G41T-M-CSM, and it works perfectly now. thanks for all your help guys :D

---

### Post by Hakunka-Matata on 2011-03-27
Well Done, keep on Ubuntuin!

---

