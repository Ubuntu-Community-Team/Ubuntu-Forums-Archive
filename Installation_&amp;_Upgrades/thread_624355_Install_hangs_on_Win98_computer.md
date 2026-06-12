---
title: "Install hangs on Win98 computer"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by hoosemon61 on 2007-11-26
I have an old PIII 550 Mhz unit, still running Win 98 SE and I'd like to try doing a dual boot with Gutsy.

I set the bios to boot from cd and can't get it to boot to the cd.

Additional facts:

2 CD drives Master CD-R/DVD Rom & slave CD/DVD rom - neither will boot to gutsy disk.

I've used the same disk (burned from iso) to run live on my XP box and have surfed and done other stuff - good disk.

Both CD drives can read the Gutsy disk when booted into windows.

When it tries to boot to the CD it hangs at the "Verifying DMI Pool Data" line.

I tried different combos of boot sequence and it always hangs if the cd is before the HDD.

Any ideas?

Thanks,

Hoosemon

---

### Post by brennydoogles on 2007-11-26
> **hoosemon61 said:**
> I have an old PIII 550 Mhz unit, still running Win 98 SE and I'd like to try doing a dual boot with Gutsy.

I set the bios to boot from cd and can't get it to boot to the cd.

Additional facts:

2 CD drives Master CD-R/DVD Rom & slave CD/DVD rom - neither will boot to gutsy disk.

I've used the same disk (burned from iso) to run live on my XP box and have surfed and done other stuff - good disk.

Both CD drives can read the Gutsy disk when booted into windows.

When it tries to boot to the CD it hangs at the "Verifying DMI Pool Data" line.

I tried different combos of boot sequence and it always hangs if the cd is before the HDD.

Any ideas?

Thanks,

Hoosemon

I am going to assume that you have 256mb of ram or less, in which case the live cd will not work. You can still install using the [alternate cd]("http://mirrors.ccs.neu.edu/releases.ubuntu.com/gutsy/ubuntu-7.10-alternate-i386.iso") . Hope this helps!!



:::EDIT:::

You may want to try Xubuntu on that computer, since it is a little faster on older hardware. Just a suggestion!!

---

### Post by hoosemon61 on 2007-11-26
I actually have 383 MB of RAM.  I also tried disks for Ubuntu 6.10, Freespire 1.0, Xubuntu 6.06.1, and even Damn Small Linux 3.0.1.  

All hang in exactly the same way.


:confused:

Hoosemon

---

### Post by nzadLithium on 2007-11-26
Having low amounts of ram should not cause it to crash there. First things first before we even try to install gutsy on it have u checked you have enough hard disk space coz theres no point in trying to get past this problem unless you have enough space and unless you bought urself a new hard disk i doubt ur pc is going to have enough space for 2 o/s. 

I would also like to say ubuntu will run extremely slowly on that computer i would recommend damn small linux or knoppix.

If you still want to install then i think what you will need to do is download a boot image from 
[http://sourceforge.net/project/showfiles.php?group_id=4185&package_id=4201&release_id=25481or](http://sourceforge.net/project/showfiles.php?group_id=4185&package_id=4201&release_id=25481or)

then download rawwrite from 
[http://www.chrysocome.net/rawwrite](http://www.chrysocome.net/rawwrite)
put a floppy in your floppy drive (hoping you have one otherwise we're gona have fun)
install rawwrite and run it get it to put the original file the smb.bin onto the floppy.

put the ubuntu cd in. 
Restart & pray.

---

### Post by hoosemon61 on 2007-11-27
I definitely have enough disk space, 2 partitions with a total of more than 60 GB free.

So, I download the boot manager group of 7 files from your 1st link and then download, extract and run rawwrite, which will make a boot floppy out of the bootmanager files?

Then I boot to that floppy with the Ubuntu CD in the drive?

Have I got it right?

Hoosemon

---

### Post by nzadLithium on 2007-11-27
you dont need to download all seven from first link only the smb.bin
apart from that yes.

essentially what we're trying to do is bypass booting from cd which is where your pc seems to be failing. So instead we are gona boot from the floppy which will tell it to boot ubuntu (hopefully) that way we dont need to use the cd booting because your cd rom or bios seems to have a prob with booting from cd.

---

### Post by hoosemon61 on 2007-11-28
I can't find smb.bin

Here's what I see when I follow the link from your earlier message:


  	btmgr-3.7-1.i386.rpm  Mirror 	327814 	11519 	i386 	.rpm
  	btmgr-3.7-1.src.rpm  Mirror 	195409 	2489 	i386 	Source .rpm
  	btmgr-3.7-1.tar.gz  Mirror 	193090 	8877 	i386 	Source .gz
  	sbminst  Mirror 	41220 	15956 	i386 	Other
  	sbminst.exe  Mirror 	69612 	35528 	i386 	Other
  	themes-3.7.tgz  Mirror 	30334 	3672 	i386 	.gz
  	user-guide-3.7.tgz  Mirror 	37796 	10058 	i386 	.gz


Sorry if I'm being dense but I'm missing something

Hoosemon

---

### Post by nzadLithium on 2007-11-29
[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)
this is a how to on how to make a boot disk follow that :D

yeah there isnt an sbm.bin there :S sry bout that i just looked it up and assumed it would be there.

---

### Post by Pointswest on 2007-11-29
I have successfully installed Ubuntu 7.10 on  a 500 Celeron and a 650PIII dell.  The new release solved the loading problem on these old machines.  Originally used 7.04 but could not load it without unpluging all drives except the one loading the new OS.  The 665 has a 10 G hd with a dual boot of win/ubuntu,   another 60 G hd for the swap files.  This seems to run at least as fast as win 98.  I'm pretty new at this but found this works for me.

Richard

Pointswest

---

### Post by hoosemon61 on 2007-11-30
OK...

I was able to create a floppy using rawwritewin and sbm.bin.  

1st try was a failure, but turned out I had a bad floppy...

2nd one said "Image successfully created"

I try to boot from it and I get "SBMK Bad!"

The computer even whips an exclamation point at me.

I'm starting to feel as though it's toying with me.

Just for Sh@#s and grins I also tried Pointswest's suggestion of unplugging all drives except the CD, but it still hung at "Verifying DMI Pool Data".

I did of course change the boot sequence in the BIOS for each of these tries.

I think I'll try making a second boot floppy just to see if it was a second goofy disk.  None of them are new (who buys floppies anymore?).

I'll let you know.  Meantime, if anything else occurs to anyone, feel free to chime in.

Hoosemon

---

### Post by hoosemon61 on 2007-11-30
Interestingly enough I've installed Linux about 10 times now on about 6 or 7 different computers and this is my first dead end.

I did have one weird install on an IBM where, after I installed an earlier version of Ubuntu, I could no longer get the thing to boot from the CD.  In that case I just stuck with the version I had...no biggy.

Hoosemon

---

### Post by hoosemon61 on 2007-12-01
Well...I found a floppy that didn't look too crappy and tried again.  This time it seems to have worked.

Thanks for the help folks!

Hoosemon

---

### Post by hoosemon61 on 2007-12-02
Spoke too soon.

The boot manager worked great and allowed me to boot from the CD.  It worked for each of the different versions and flavors of Linux I had.

Each one hung up during install however.

I don't get it.  This computer has never been particular quirky, I've installed Ubuntu on much slower computers with less memory.  Could something with AVG be screwing this up?

Hoosemon

---

### Post by nzadLithium on 2007-12-02
Ubuntu and Windows are completely seperate operating systems one should not effect the other in any way shape or form. Any program in windows will not affect ubuntu. any program in ubuntu will not effect windows. (unless these programs are repartitioning software and you repartition your hard disk or you start deleting operating system files)

Windows should not cause any problems with ubuntu. However ubuntu could cause problems with windows as windows is a bit stupid about where it puts its data (it chucks it everywhere). When you repartition the disk during installation so you can put ubuntu on it is possible you may wipe some data off your windows partition. So i would suggest before you even start the install you go into windows goto start, programs, accessories, system tools, disk defragmenter. Tell it to do its defragmenting. This should help to prevent data loss because it will try to move all data to the start of the drive. Once this is done you should not have any problems with data loss as long as you make sure all ubuntu partitions are at the end of the drive.

Can you try install using the 'alternate' cd? I'm assuming that when you say it 'hung' you mean it paused and stopped responding. This could simply mean that the proccessor is being fully used at the current time. Using the alternate cd since it is text based should speed it up because its not having to process any 'heavy' graphics. It will probably still pause often but just leave it to go for about 4 to 5 hours. It should be finished installing by then. If it is still at the same place where it 'hung' then you know you have a problem but i think it should be fine.

---

### Post by hoosemon61 on 2007-12-02
Looks like the alternate CD will work fine.  It gets through to the network and pertitioning stepa, which is further than any of the other steps.  

The other disks all stop responding before they even ask me the starting questions about language and keyboard layout.

I'm guessing it's something to do with the video card or the disabled graphics on the motherboard.  Just a SWAG.

I'm going to defrag before I continue the install.

Any advice about how to approach a dual boot?  I've never tried it before, always just wiped a system completely clean.  

I don't think we have any data left on this system that we haven't backed up to CD long ago, but we'd like to have a second Win system in the house just in case.

Thanks,

Hoosemon

---

### Post by hoosemon61 on 2007-12-03
OK...next episode of *"the little installation that wouldn't"*.

The alternate CD installed successfully with the smart boot manager (thank you very much!)

I now start at the boot menu and if I choose, win98, the computer operates just fine.  The partition is consistent with what I thought it should be although the Ubuntu partition doesn't show up anywhere when I'm in Windows (maybe I should have specified Fat32?).

Anyway, that's not of primary concern I don't think.

If I choose *Ubuntu 7.10, 2.6.22-14-generic* it starts to boot, I get the Ubuntu logo with the orange progress bar moving below, no text, then I get a black screen...I've left it for 20 minutes - no change.  This is the same exact behavior I got when trying to boot to the live CD.

If I choose boot option 2, which is the same as 1 but says (*recovery mode)* after it, it seems to boot fine to a command prompt.

Is this some kind of graphics incompatibility?

I'm currently running boot option 3 which is the Ubuntu 7.10 memtest.  

I figured it can't hurt.

I welcome anyone's advice...I am but a humble noob.

Hoosemon

---

### Post by nzadLithium on 2007-12-05
Ok. 

First the easy one :)

Windows doesnt detect the linux file systems because it is only written to support windows file systems (Fat16, Fat32, NTFS) i think thats all of them? and the cd file systems (the iso thing and the music one).

Yes this is a graphics driver issue. What graphics card do you have? (manufacturer and model).
Once i know that we can get the driver up properly. The autodetection probably didnt work properly and gave you the wrong driver either that or you have a really new card which i highly doubt (i dont see why anyone would put a nvidia 8800 into a pentium 3 :S) We should be able to get it going though :D

---

### Post by hoosemon61 on 2007-12-05
My graphics card is an ATI *Xpert @ Work* card  - info at this link: [B][http://ati.amd.com/products/ragepro/xpertwork/specs.html]("http://ati.amd.com/products/ragepro/xpertwork/specs.html")
[/B]
It's pretty wimpy, but the most I could install that wouldn't clash with the onboard graphics that I disabled.

I don't remember exact details, but I remember that the Intel 82810 chipset on the MOBO would not support games I wanted to play, so I upgraded.  

I was limited with how good a board I could install because the 82810 chipset was particularly flaky about conflicting with any graphics card that was added.


I should also tell you that last night I tried to follow this how to:  [B]  [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")    
[/B] by booting into command line mode.  

It seemed like it was going to work but I kept getting "*could not resolve us.archive.ubuntu.com*" and it would fail to fetch the packages need to update.

That made me think that maybe it wasn't seeing my network adapter (ethernet to DSL), which is working fine when I boot to Win98.  

This is gonna be so cool when we solve it...



Hoosemon

---

### Post by nzadLithium on 2007-12-06
Ok it seems your card doesnt have a lot of support under linux because at the time it was made ati did not support linux at all. It still may be possible to get it going though. 

run sudo dpkg-reconfigure -phigh xserver-xorg

if it asks you what driver you want put 'ati' (select is spacebar)
fill out any other questions

see if it goes now. (you will need to restart in the normal ubuntu mode)

If not then do nano /var/log/xorg.log and post contents here.

---

### Post by hoosemon61 on 2007-12-06
Ok I ran [I]sudo dpkg-reconfigure -phigh xserver-xorg
[/I]  

It didn't ask me any questions but did give me this: *FATAL: Error inserting battery (/lib/modules/2.6.22-14-generic/kernel/drivers/acpi/battery.ko) No such device*  

I got that twice followed by *xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etcX11/xorg.conf.20071206222106*

I rebooted and got the same result...I thought it ran the hard drive a little more before the screen went black, but it could have been wishful thinking.

I did *nano /var/log/xorg.log* and it opened a text editor but there was nothing shown on the screen except the command shortcuts at the bottom and a little box immeditely above those that says [new file].

Hoosemon

---

### Post by nzadLithium on 2007-12-08
ok try running the other command without the -phigh so like this:
sudo dpkg-reconfigure xserver-xorg

hopefully this time it will ask you some questions :S
once you've answered all the questions then restart pc boot into normal mode and see if it goes.
(when it asks you about the driver make sure before you procede that only 'ati' is checked no others)

my path to the xorg logs was wrong. It should be nano /var/log/Xorg.0.log
(case is important) and the 0 is a zero. (kinda looks like an o :D)

---

### Post by hoosemon61 on 2007-12-10
When I try that command it tells me that Xserver.org is not installed and no info is available.

I tried *sudo apt-get install xserver.org*  (Just guessing at the command really) and it did the following:

Reading package lists...Done
building dependency tree
Reading state information..Done
E: Couldn't find package xserver.org


Again, just poking around I opened up Aptitude (1st time I've seen this) and navigating blindly through the lists I found a group of xserver packages listed and they were highlighted.  I couldn't figure out how to get Aptitude to download them though.

I have a sneaky suspicion that based on earlier stuff I've tried, the system also isn't seeing my network card either, so it's not grabbing packages.

I tried again.  Aptitude has a list of upgradable packages all set to go.  

When I tell it to up date, I get a screen of red text, telling me nothing was downloaded because it "couldn't resolve the host us.archive.ubuntu.com"

The network connection works ok in Win98 but maybe this is a driver problem as well?

I have a Netgear FA310TX ethernet card.

Would you rather I just stuck to what you've asked me to do without these parallel attempts?

Hoosemon

---

### Post by hoosemon61 on 2007-12-10
Oh Yeah...

Even with the corrected path, the xorg log just brings up the same empty frame.

---

### Post by nzadLithium on 2007-12-11
your card is supposed to be supported under linux (the ethernet one)
run sudo apt-get install xserver-xorg
that should install / reinstall the xserver
if it fails (because of not being able to resolve or something along those lines) then post the output of lsmod (first letter is an L make sure its all lowercase many people seem to decide its ismod???) and i'll check its loaded the right drivers.

Your gfx card seems to be supposed to work with the 'ati' driver. its says it supports Mach, RAGE, Rage128, Radeon, and most firegl cards.

so post lsmod whether the network card works or not and i'll check for the right video module as well.

---

### Post by hoosemon61 on 2007-12-13
OK - results of sudo apt-get install xserver-xorg:

[I]Reading package lists...Done
Building dependency tree
Reading state information... Done
xserver-xorg is already the newest version
0 upgraded, 0 newly installed, 0 to remove and 96 not upgraded[/I]

I did lsmod and it fills the screen top to bottom, so I'm not sure if the beginning gets cut off or not.  I tried *man lsmod* but it didn't give me any kind of one-page-at-a-time type switch to add to the command.

Anyway, here's what I got from lsmo[FONT="Courier New"]d:

shchp                34580    0
pci_hotplug        32704    1 shpchp
i2c_i810              5982    0
i2c_algo_bit         7428    1   i2c_i810
i2c_core            26112    2   i2c_i810, i2c_algo_bit
evdev                11136    0
ext3                 133896    1
jbd                    60456    1   ext3
mbcache              9732    1   ext3
sg                     36764    0 
sr_mod              17828    0
cdrom                37536    1   sr_mod
sd_mod             30336    3
floppy                60004    0
tulip                   53792    0
uhci_hcd             26640    0
usbcore            138632    2   uhci_hcd
ata_piix              17540    2
ata_generic          8542    0
libdata              125168    2   ata_piix, ata_generic
scsi_mod          147084    4   sg. sr_mod, sd_mod, libdata
fuse                   47124    1
apparmor           40728    0
commoncap         8320    1   apparmor[/FONT]

Sorry I can't seem to format so it looks like what I saw.  It's all there, just harder to read.

That's it.

Is there a difference between booting into recovery mode as I am and actually running a terminal session?

During the boot sequence it does give me an [OK] for the *configuring network adapter* line.

Hoosemon

---

### Post by hoosemon61 on 2007-12-13
Just for grins,  decided to try booting to the Damn Small Linux (DSL) CD I have.  I haven't tried doing this since I created a smart boot manager floppy.

It worked great, surfs the net, all programs open fine, graphics look good.  

I got optimistic and tried the Ubuntu 5.10 live CD (back when the live and install CDs were separate) and it went way into boot process before it finally stalled on a black screen with a small white cursor in the upper left corner.  When it gets there nothing is blinksing, no drives are running and I waited 1/2 hour without a change.

I got the same resuly trying to load the live Xubuntu CD, even if I set the graphics to 640x480x16 during boot (it's an option).

ok, I'm done messing with it until your next instructions.

Hoosemon

---

### Post by nzadLithium on 2007-12-14
that is nowhere near the full output. do: lsmod | more
press enter to scroll down

your network card is fully configured and working 
It seems you can probably use the 'vesa' driver (thats what dsl uses i think) to get the gui up. i would not recommend this is an option though because your card is more capable than what you would get with the vesa driver.

i think if you get the right driver you should at least get full 2D acceleration you may even get half decent 3D accell but thats getting onto the overly optimistic side :D 

anyway post the full lsmod here 
if your typing it out then to reduce time I only need the first word in every line not the numbers or words following. (a word with an underscore in it or a hyphen if still a single word not two)

hopefully its just using the wrong driver which is easy enough to fix (usually) but we shall see from the output of lsmod :S

---

### Post by hoosemon61 on 2007-12-15
Darn. I should have tried that | more switch.  Was that an old DOS thing or do I remember it from the miniscule bit of UNIX I learned 20 years ago?

Anyway, here's the full output of lsmod:

[I]lp
loop
snd_intel8x0
snd_ac97_codec
ac97_bus
snd_pcm_oss
snd_mixer_oss
snd_pcm
snd_seq_dummy
snd_seq_oss
snd_mpu401
snd_mpu401_uart
snd_seq_midi
parport_pc
parport
snd_rawmidi
snd_seq_midi_event
analog
gameport
snd_seq
idi_event
snd_timer
snd_seq_device
di,snd_seq
iTCO_wtd
iTCO_vendor_support
intel_rng
pcspkr
i2c_i810
i2c_algobit
serio_raw
shpchp
psmouse
snd
soundcore
snd_page_alloc
pci_hotplug
intel_agp
agpgart
i2c_core
evdev
ext3
jbd
mbcache
sg
sr_mod
cdrom
sd_mod
floppy
uhci_hcd
usbcore
tulip
ata_piix
ata_generic
libata
scsi_mod
fuse
apparmor
commoncap
[/I]

That's it.

Thanks,

Hoosemon

---

### Post by nzadLithium on 2007-12-23
sry for slow reply

it looks like it is loading intel drivers to me???

run nano /etc/X11/xorg.conf
look for the line that says 
driver 
if it says anything apart from ati
change it to ati

restart see what happens.

---

### Post by hoosemon61 on 2008-01-03
Happy New Year!

Sorry for taking so long to get back.  I took a long vacation around the holidays.

There are several lines labeled "Driver" but the section that I'm guessing applies here reads as follows:

Section "Device"
          Identifier     "Intel Corporation 82810 CGC Chipset Graphics Control
          Driver         "Intel"
          Bus ID        "PCI :0:1:0"
End Section


Looks to me like it's loading drivers for the original on-board graphics, which I disabled in Windows when I installed the ATI card.  I did try plugging the monitor into the old monitor connector earlier - when trying to boot Ubuntu, but only got snow.

I don't know how to interpret the Bus ID but is it trying to use the ATI board plugged into the PCI bus using the driver for the MOBO graphics?

I'm making the change you suggested ("Intel" to "ATI") and we'll see what happens.

Take care,

Hoosemon

---

### Post by hoosemon61 on 2008-01-03
Nope...still get a black screen after the Ubuntu logo and progress bar...

---

### Post by hoosemon61 on 2008-01-03
two more tidbits:


My MOBO has 3 PCI slots, labeled PCI1, PCI2 & PCI3, and the ATI board is plugged into PCI1.

After failed boot to graphics mode, I booted to command line again and entered *nano /etc/X11/xorg.conf* and I found that the line I'd changed to "ati" was back to "Intel".

I changed it again and saved the file the same way, exited nano and went back in.  The line was still changed to "ati".

I just rebooted to graphics mode again and it still hangs but at a slightly different point now,   It stops with 4 lines at the top of the screen.  Tha last one reads as follows:

* Running local boot scripts  (/etc/rc.local)    [ OK ]


What's next?



Hoosemon

---

### Post by nzadLithium on 2008-01-10
you need to go into ur bios and disable onboard graphics. When you start ur pc up it will say either press f2 or del to get into bios
press whichever one it says. If it dont work jsut keep pressing each alternatively. never did me any harm :D

have a look through there. only disable onboard gfx dont touch anything else unless you know what you are doing.

---

### Post by nzadLithium on 2008-01-10
i think now it may be failing to start x at all because you're using the ati driver on an intel card. once you disable onboard gfx it should fix. (before x server was probably starting just not loading right coz u confused it with two dif gfx controllers :D )

---

### Post by hoosemon61 on 2008-01-10
This BIOS is really not very cooperative...

There's not a setting to disable onboard graphics really, there's a setting called "Init Display First" and that can be set to "onboard" or "PCI Slot".  

I have it set to "PCI Slot" - I remember I had to in order to get the ATI board to work.

There's another setting in the PnP/PCI Config area called "PCI/VGA Pallete Snoop".  That was enabled, but I tried it both ways and it didn't make a difference.

???


Hoosemon

---

### Post by Mze on 2008-01-10
Run this command in recovery mode and post results:

lspci

The ATI card should have a PCI # listing, which you could then correct in your xorg.conf file so that the right graphic card is loaded at boot.

---

### Post by hoosemon61 on 2008-01-12
There are two lines related where VGA controllers are mentioned:

00:01.0  VGA Compatible Controller (then lists the Intel on-board model info)

and later...

00:06.0  VGA Compatible Controller: ATI Technoligies...model info



So if I do nano /etc/X11/xorg.conf


The section with VGA driver info is currently as follows:

Section "Device"
Identifier "Intel Corporation 82810 CGC Chipset Graphics Control
Driver "ati"
Bus ID "PCI :0:1:0"

I should change it to what?

Sorry for being dense but I'm a major newb in this area.

Hoosemon

---

### Post by nzadLithium on 2008-01-21
sry for slow reply. i has been busy.

in this line

Bus ID "PCI :0:1:0"

change it to

Bus ID "PCI :0:6:0"

that should do it.

It would be simpler to just disable ur on board video then re-setup x 
(dpkg --reconfigure xserver-xorg)

then it would do it all automatically which would make less room for errors. Once you've done that just double check you've plugged monitor into right vga connection

---

### Post by hoosemon61 on 2008-01-21
No problemo on the slow reply...I appreciate the help.


Do I need to change the "Identifier" line or just the "Driver" and "Bus ID" lines?

I will look into how to disable the onboard video in hardware, but I think I looked into it when I added the PCI vid board and it couldn't be done.  I had a hotter video board to add but couldnt because it wouldn't co-exist with the Intel onboard.  I returned that bard and bought this one used.  It was the newest one that didn't clash.

Thanks again for the help.

Hoosemon

---

### Post by hoosemon61 on 2008-01-23
I made the change and it doesn't hang any longer but now ends up at a command line - at the root.  

I'm wondering now if the original installation was even successful.

I disassembled the MOBO enough to find the Model # - it's a Biostar.  There is no way to disable onboard video.  The closest thing is the BIOS setting to have it check the PCI bus first.

I hate to do it, but I think it's time to throw in the towel on this one.  This will be the first machine I've found that won't accept Ubuntu.  

Whaddya think?

Hoosemon

---

### Post by nzadLithium on 2008-01-29
Make sure you have it set to look for your agp one first then. Then run dpkg-reconfigure xserver-xorg

setup it up for your ati card. 

hopefully that might work :S

If it still dont work then post your xorg log file up here.

you should be able to bring the log file up by typing 
(after you have logged in)
nano /var/log/Xorg.0.log
(case is important)

---

