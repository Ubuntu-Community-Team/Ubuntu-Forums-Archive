---
title: "end_request error starting the Ubuntu 8.10 Setup"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by SupaBeast on 2008-10-30
Ok, tried to get help on irc, without any luck. So i hope i can get some answers so i can get going here.

Anyways.

My computer is setup with 2 OS'es Vista and Ubuntu 8.04LTS. These are on different harddrives. (Vista on haddrive 1 and Ubuntu on harddrive 2.)

Then i have 1 Partition for Files on harddrive 1 and 1 Partition for Games on harddrive 2. (And one external harddrive 3 for just about anything.)

So, now i want to make a clean install of Ubuntu 8.10. So i boot of the Ubuntu CD and choose language and then select install. Ubuntu starts the loading process, but after some minutes the loading bar dissapears and i got this screen with 
"End_request: I/O error, dev sr0, sector (some sort of number combo here)
Buffer I/O error on device, sr0 logical block (then some number)"

These messages appear one after another all with different numbers. (Same errors if I try to start Ubuntu of the cd without doing any changes.)
 
So any help would be welcome, cause i don't have much knowledge on the Linux OS'es. (Started using it cause i feel that i want to learn something new after using Windows for many years.)

---

### Post by null_pointer_us on 2008-10-30
I and someone else had similar problems. (I used a flash drive instead of the live CD.)

What hardware are you running?

---

### Post by mythik on 2008-10-30
> **null_pointer_us said:**
> I and someone else had similar problems. (I used a flash drive instead of the live CD.)

What hardware are you running?

I had this same problem when I tried installing Sabayon Linux (variant of gentoo) on my old computer.  In fact, having this problem is the reason why I started using Ubuntu with Fiesty Fawn.

I have scsi hdds (two of em) not raided at all.  core 2 duo, so I have the amd64 iso (yes that's the right cd eventhough it's an intel chip) and 8 gigs of ram.

Really gotta fix this.  It's unbearably slow.

---

### Post by SupaBeast on 2008-10-30
Intel Core 2 Quad Q6600 (B3) 2,4Ghz (Watercooled)
Gigabyte 965P-DS3 rev3.3 (Watercooled Northbridge)
Corshair XMS2 PC6400 4x1024mb [5.5.5.18]
BFG Nvidia 8800GT 512mb OC (Zalman VF1000)
Samsung Spinpoint F1 750GB 32mb cache
Western Digital 250GB 8mb cache
Western Digital 500GB External USB
Samsung TSSTcorp CD/DVDW SH-S182D ATA
Creative X-Fi Extreme Music
Thermaltake Kandalf LCS Chassi
Windows Vista Buisness 64bit SP1 Regular use
Linux Ubuntu too hopefully

Maybe i could try the flashdrive installation, just have to get a flashdrive first. (I have one...in a locker in school ;P)

---

### Post by null_pointer_us on 2008-10-31
> **SupaBeast said:**
> Samsung TSSTcorp CD/DVDW SH-S182D ATA

I have nearly the same drive (SH-S182L) -- maybe it's a drive issue?

> Maybe i could try the flashdrive installation, just have to get a flashdrive first. (I have one...in a locker in school ;P)

Flash drive installations are *really* fast (USB 2.0)!

I'm not burning any more Linux setup CDs...ever. :)

---

### Post by SupaBeast on 2008-10-31
<3 Old Hitachi CD reader did the thing :)

Finally I succeeded installing Ubuntu 8.10.

Seems that it must be some sort of driver error or something similar, but I tried Ubuntu 8.04LTS and that one worked fine, so it's something with 8.10 for sure. Well atleast it works now.  Switched back to my Samsung again after and it seems to work.

Thanks for all help.




(For others having this problem reading this post, solution is try another cd reader, or use a flashdrive to install.)

---

### Post by deputyjones on 2008-10-31
Awesome. Just awesome. Great new release I have been waiting for. Gives me great confidence that it won't even support my cd drive.

---

### Post by elgreek84 on 2008-11-01
haven't been able to do this? how do you do it? thanks! also have two sh-s182l drives

> **null_pointer_us said:**
> I have nearly the same drive (SH-S182L) -- maybe it's a drive issue?



Flash drive installations are *really* fast (USB 2.0)!

I'm not burning any more Linux setup CDs...ever. :)

---

### Post by ftmichael on 2008-11-01
I'm having the same exact problem myself - is it indeed a CD drive issue, or might it be some other hardware?  I got this computer secondhand and didn't even check the hardware before attempting the install, since I've never had any trouble with an install before.

**ETA:** The computer in question has two optical drives, one of which seems to be a DVD drive and the other of which seems to be a CD drive.  I had been using the DVD drive; using the CD drive eliminates the errors, so it must be an issue specifically with the DVD drive here.

Of course I still have another huge problem, outlined [here](http://ubuntuforums.org/showthread.php?t=966726) ...

---

### Post by null_pointer_us on 2008-11-01
> **elgreek84 said:**
> haven't been able to do this? how do you do it? thanks! also have two sh-s182l drives

You mean install from a USB flash drive?

Download the Ubuntu live CD iso and then follow the instructions here:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I opted for UNetbootin, which is an app that runs in Linux or Windows.

The three optional steps...

> (optional) If you need to activate the original Ubuntu livecd boot menu, for example if you want to disable the framebuffer or read the Ubuntu livecd HELP screens and cheatcodes, please make these changes to your USB drive after your UNetbootin installation is completed:

1) Delete the SYSLINUX.CFG file or rename it to be SYSLINUX.OLD

2) Enter the ISOLINUX folder and rename the ISOLINUX.CFG file to be SYSLINUX.CFG

3) Move up to the top level and rename the ISOLINUX folder to be SYSLINUX 

...made the boot menu work fine for me.

Finally, you'll probably need to change a BIOS setting -- plug in the flash drive before loading the BIOS -- to make the BIOS boot from the flash drive before the hard drive and any other boot devices.

---

### Post by marcon00 on 2008-11-02
I got same problem mates ...  I got TEAC DV-W28SLCTF ATA Device. Will try now USB install :)

---

### Post by marcon00 on 2008-11-02
i take that back for now.. i checksum-ed my iso.. ehem.. wasn't exactly the same ...

---

### Post by phat_penguin on 2008-11-07
I was able to resolve this by burning the iso onto a DVD instead of a CD.  I had the problem with a few CDs that I tried and on a whim I tride a DVD+R and was able to install.

Inconsequently I am installing Mythbuntu 8.10 on a new AMD phenom 9550 box I just built.

---

### Post by Parama on 2008-11-08
Just wanted to confirm that writing the 700MB iso to DVD instead of CD works! :D

The CD media I used are rather good quality Verbatim and the DVD's are cheap no-names, so I honestly didn't believe that burning the 700MB iso to these DVD's would make any difference.
Especially after having burned the amd64 iso 2 times and the i386 iso 1 time.

FYI: My optical drive is a NEC ND-3540A (connected to a ASUS M3A32-MVP Deluxe with a AMD Phenom 9850 Quadcore)

---

### Post by pormogo on 2008-12-04
I use a lite on optical drive (DVD/CD burner) and I've been running into the same issues. I've tried using both gnomebaker and ImgBurn (running through wine) burning with both my laptops Matshita burner (857G model) As well as a pioneer DVD-115D burner in an external encolsure. None of them seem to be turning out anything that my Desktops lite on is able to read. 

I've tried authoring in auto mode, in doa mode (which does not seem to be supported by either of these drives under gnome baker). I've tried burning the amd64 .iso to a DVD and then using that but it doesn't seem to want to boot. Using a CD I get the same error reading the same sectors of the disk everyone else is reporting. It has to be something that went on with 8.10 because 8.04 still installs just fine...

I think I may have to run out and buy a USB stick in order to get this thing installed :(

My experience with 8.10 so far has been pretty poor. Upon doing the update from 8.04 to 8.10 a mis spelling in a config file for geexbox DNLA server (which I was not actually running anymore) caused the updgrade to hang and left me with a broken system. Now getting the OS installed from "scratch" using 8.10 is turning out to be quite the project :(

---

