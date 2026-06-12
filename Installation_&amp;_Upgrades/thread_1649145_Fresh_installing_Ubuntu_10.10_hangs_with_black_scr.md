---
title: "Fresh installing Ubuntu 10.10 hangs with black screen"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by AngelFire_91 on 2010-12-19
Hey guys,
     I'm trying to install Ubuntu 10.10 from a Live CD. I can get to the Menu where I get to choose "Try without installing","Install Ubuntu","Test Disk," etc...

After hitting ANY of the options, it hangs on a black screen, sometimes with a cursor blinking in the upper left, sometimes not. From all the research I've been able to dig up it seems it's a graphics card issue, but I haven't been able to find anything exactly like my problem as most everything I've been able to find say's theirs continues to install but then causes problems later, or they're trying to load on a dual boot system. I can't seem to get past that first "Install Ubuntu" selection. As soon as I hit enter it goes black.

Here are the specs on my computer:
Everything is brand new, just finished putting it together a couple days ago so it's TOTALLY from scratch.
Mainboard is a MSI NF980-G65
AMD Phenom II 6 core processor
8GB DDR 3 Ram
1 Samsung Solid state hard drive
2 Samsung 1TB HD setup in RAID
Samsung iHAS424 DVD/CD drive
I'm using the on-board graphics which is Nvidia GeForce 8 series


Here is what I have tried:
All downloaded md5's match, and I wrote at the slowest speed I could.
I've tried V10.10 64bit, V10.10 32bit, V10.10 64bit alternate, V10.04 64bit
I've selected nomodeset using F6
I've set nomodeset manually by changing the boot line at the bottom of the load screen
I've changed my BIOS from Internal Graphics priority to PCI graphics priority and back, (Even though I don't have a PCI graphics card).
I've also changed it from RAID to standard HD's and back to RAID.


I'm wondering if I can't load the nvidia drivers from a command line before I attempt to install from the live CD, but I don't know how to do that. I have the .run file downloaded but don't know where to go from there.

---

### Post by sikander3786 on 2010-12-20
Welcome to the forums :-)

Sound like a graphics issue but 'nomodeset' didn't work for you.

There are 6 boot parameters under the F6 menu. I would recommend to try all of them one-by-one and any of them might work magically. Speciall acpi=off or noapic ;-)

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

---

### Post by AngelFire_91 on 2010-12-20
Thanks for the Reply...

Sorry, I forgot to include that in my first post.

I have tried going through each boot option one-by-one and still nothing. 
I have also moved my monitor cable from the VGA to DVI and back, still nothing.
I do not have a mouse hooked up yet if that matters?

I have used this same disk to load Ubuntu on an Aopen, Core 2 system. So I know the disk is good.

---

### Post by sikander3786 on 2010-12-20
The disk might be good but what about the disk drive? Are you sure it is ok?

If you've got a USB drive, you can try booting from that and see if it makes any difference.

And you sure all the other hardware is in good health?

---

### Post by AngelFire_91 on 2010-12-20
USB drive didn't even load to the splash screen. After BIOS runs through and it goes to boot from the drives, the USB light blinks like it's reading for about 5 seconds and then blank screen with blinking cursor in the upper left, can't go any further. Md5 all verified on the USB drive, and it boots fine from another computer. I also changed the boot order so the USB drive is first.

Everything in the computer is brand new, and I can't tell for sure everything is working since I don't have an OS, but everything is recognized in BIOS and giving information. All lights come on appropriately and flash like they should. Hard drives spin up, self test ok in BIOS and everything else. This is about the 8th computer I've built from scratch in my life so I would hope I'm good there...  

As a side note: I'm seriously about to pull what little hair I have left out. I've installed and used Fedora, Ubuntu, and others before and never had a problem... EVER! Now this one is stumping me and it's really starting to eat at me. lol.

---

### Post by Quackers on 2010-12-20
You mention that your 2 1TB drives are in raid. What type of raid and what controller? Are these the drives you want to install Ubuntu on?

---

### Post by AngelFire_91 on 2010-12-20
Thanks guys for your responses.

I am not installing Ubuntu on the RAID drives. Ubuntu is going onto the SSD, and the RAID drives were going to be used for storage only. 

They are set up in RAID 1 (Mirroring) using the onboard controller. I've tried installing Ubuntu with no RAID arrays setup in BIOS and with them setup just as normal drives. Still no go.

I was going to try and disconnect them all together and see but haven't gotten there yet.

---

### Post by ronparent on 2010-12-20
When the boot menu appears, edit the boot line by erasing 'quiet splash'. This allows the boot commands to scroll on the screen. Where the script stops gives some clue as to what your problem may be. Post the last few lines displayed.

---

### Post by AngelFire_91 on 2010-12-20
I've already modified the boot line like that. It just goes to a blank screen, no output, nothing.

---

### Post by ronparent on 2010-12-20
That is something. It is not the graphics. It is something before any post show up. Any ideas guys.

---

### Post by AngelFire_91 on 2010-12-21
Anyone? 

Don't make me go the "W" route! lol.

---

### Post by sikander3786 on 2010-12-21
> **AngelFire_91 said:**
> Anyone? 

Don't make me go the "W" route! lol.
Try 10.04 from a Live CD/USB and see if that behaves the same way.

If Ubuntu doesn't work, you definitely need some other OS and that is entirely up to you. Choose the one that works better and satisfies you ;-)

---

### Post by AngelFire_91 on 2010-12-21
Ok guys.... I've made a break through! I still don't have linux installed, but I have more information.

I went to try and install Windows Vista (the only other operating system I had laying around, just to see if it was a hardware problem). After the BIOS boots, it says "Loading windows files." after it gets done with that it stops at an Error.. Only thing is says though is "Error: STOP! 0x0000005C"

After digging around the internet, I found that this is a BIOS setup problem. So I started to tweek BIOS according to what had worked for other people.. I eventually got the computer to wrap it self into a rebooting loop, so I reset the CMOS using the jumper...

BLAM!!! Ubuntu will now get past the selection part. I have to select ACPI=off and after removing quiet splash I get stuff to start spitting out. However, now it hangs while trying to check the PCI cards it looks like, however, I have no PCI cards what so ever in this computer.

Here is a screen shot:

---

### Post by ronparent on 2010-12-21
The pci bus will be checked nonetheless. Checking my own dmesg log I get:
```
[    0.744399] ACPI: WMI: Mapper loaded
[    0.744399] PCI: Using ACPI for IRQ routing
[    0.744399] PCI: pci_cache_line_size set to 64 bytes
[    0.744399] pci 0000:00:00.0: no compatible bridge window for [mem 0xe0000000-0xffffffff 64bit]
[    0.744399] reserve RAM buffer: 0000000000091400 - 000000000009ffff 
[    0.744399] reserve RAM buffer: 00000000cf780000 - 00000000cfffffff 
[    0.744399] NetLabel: Initializing
[    0.744399] NetLabel:  domain hash size = 128
[    0.744399] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.744399] NetLabel:  unlabeled traffic allowed by default
```
 following the  usbcore lines. It seems to me a recent model MB should not need to disable acpi. That keys into the first lines printed above. Just a possibility that Ubuntu is not yet operable on a six core system? We need some feedback from some real expert!

---

### Post by Mark Rose on 2010-12-31
I'm having the exact same issue with the Ubuntu 10.10 AMD 64 alternate CD:

Biostar TA890FXE motherboard
AMD Athlon II X640
8 GB DDR3
1 OCZ Vertex II SSD
4 1TB SATA drives (Hitachi/Seagate)

I was able to get the memory test and CD check to work, but the install results in a blank screen, sometimes with a _ in the top left.

No RAID is configured.

---

### Post by Mark Rose on 2010-12-31
Just got the install working!

I remove "splash" and added "noapic nolapic acpi=off" to the boot prompt and I was golden.

---

### Post by Highlander01 on 2010-12-31
I ended up having similar problem but slightly different fix then previous person...   I had ubuntu with 5 pulse dots and then screen would go blank.  To fix this I had to hit F6 on boot and then go to F6 again select "nomodest" and hit enter in order to get "x" to show up next to my selection.  I then ran install and I am now going thru the install... currently at copying files... 45% and looks good.

---

### Post by Highlander01 on 2011-01-01
My previous notes helped me get thru the install.  after install was done it reverted though.

permanent fix:
-  I was still able to boot up and then do ctl-alt-F1 and get a text terminal window.
- Then I had to run "sudo vi" editor thru text terminal on the "grub.cfg" file
-  In the grub.cfg file I had to erase "quiet splash" and put in "nomodeset"
-  My grub.cfg file was located in the "/boot/grub" folder
-  Ref... I hacked my way thru sudo vi by pulling up a web page that had a list of basic vi commands.

After I did the above I restarted and things now work!

---

### Post by ronparent on 2011-01-02
Nice work. It's a time consuming pain, but, sometimes you have to test all the permutations of those boot parameters to find the essential ones. And yes, you do have to edit preferably /etc/default/grub file to make your changes permanent. Editing the grub.cfg works but editing it is discouraged plus your edits will be erased the next time grub update is run!

---

### Post by Highlander01 on 2011-01-03
Oh, yep, i did some updating/installed linux-rt and things reset.  How do I get this "nomodeset" to stick more permanently?

---

### Post by ronparent on 2011-01-03
I hink I said it!
> And yes, you do have to edit preferably /etc/default/grub file to make your changes permanent. 
Good luck.

---

### Post by Highlander01 on 2011-01-04
I believe I figured out how to make things more permanent.  I am using the newer Grub 2 that comes with Ubuntu 10.04.  There is no longer a menu.lst and some other things have changed  The following web page is very helpful [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
 
The primary configuration file for changing menu display settings  is */etc/default/grub*.

---

### Post by Highlander01 on 2011-01-04
Oh, thank you RONPARENT.  I am a little slow i see:-)  I was hung up on Grub and did understand the difference that comes with Grub 2.  (which is version 1.98 = grub 2 for me/confusing that they did not make it version 2 when they did it.)  Clear now!  Thank You,

---

### Post by AngelFire_91 on 2011-01-17
I got all my problems solved guys! I'm up and running, typing this on the new machine!

After digging around trying everything from Ubuntu, OpenSUSE, to Fedora with no go, I finished ripping my hair out so now I'm totally bald. However, I finally got it working!

Turns out the BIOS version that is installed on my Motherboard does not support 6 core processors even though it says it does. After re-flashing my BIOS with the most recent update, everything worked beautifully with no problems what so ever!

Thanks for all your help guys!

---

### Post by AngelFire_91 on 2011-01-17
double post for some reason

---

