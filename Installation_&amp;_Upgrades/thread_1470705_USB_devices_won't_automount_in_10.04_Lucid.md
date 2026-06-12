---
title: "USB devices won't automount in 10.04 Lucid"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by Catiline on 2010-05-03
When a USB device is attached to the laptop 10.04 does not automount the device.  i.e. the device, be at an external drive, memory stick or iPod does not display with the correct icon on the desktop.

However, if one looks under Places|Computer there they all are with the correct icons.  The devices can then be mounted from there.

This issue seems to be related to these other posts:
[http://ubuntuforums.org/showthread.php?t=1468755]("http://ubuntuforums.org/showthread.php?t=1468755") and
[http://ubuntuforums.org/showthread.php?p=9167961]("http://ubuntuforums.org/showthread.php?p=9167961")

This is really disappointing given that 10.04 was promoted on its iPod friendliness!  Does any one have an idea how to fix this?

System: IBM Thinkpad T41; Pentium-M 1.6GHz; 1Gb RAM

---

### Post by Catiline on 2010-05-03
I've had a good look at Launchpad and found this related bug [#539515]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/539515").

> Bug Description

This causes long desktop session startup delays when the kernel detects a floppy drive which is not actually physically present, just enabled in the BIOS.

WORKAROUND: Disable floppy in BIOS

ProblemType: Bug
Architecture: i386
Date: Tue Mar 16 12:08:10 2010
DistroRelease: Ubuntu 10.04
ExecutablePath: /bin/mount
InstallationMedia: Ubuntu 9.10 "Karmic Koala" - Release i386 (20091028.5)
OmitPids: 2368 2401 2402
Package: mount 2.17-0ubuntu3
ProcCmdline: mount /media/floppy0
ProcEnviron:
 LANG=de_DE.utf8
 SHELL=/bin/bash
ProcVersionSignature: Ubuntu 2.6.32-16.25-generic
SourcePackage: util-linux
Title: does not terminate at computer shutdown
Uname: Linux 2.6.32-16-generic i686

I just disabled the legacy floppy in BIOS; problem solved!  Still irritating though.  This didn't happen under previous versions in my experience.

Hopefully this will help others.

---

### Post by cpg100 on 2010-05-04
I've tried disabling the floppy on BIOS but it didn't work.
My USB flash drive automounts OK but my Canon Camera doesn't.

Both of them used to mount automaticaly on Karmic.

Can anyone help me?

---

### Post by garvinrick4 on 2010-05-04
Try ALT/F2 and when box opens type in gconf-editor hit run button.
When Configuration Editor opens go to Apps to Nautilus to Preferences
to media_automount and check, to media_automount_open and check.
See if that helps your media mount.

---

### Post by Hero of Time on 2010-05-05
I believe this happens because HAL is not installed by default now. I have the same issue on Xubuntu and it will only work if I install thunar-volman (Gnome has a different package that does the same) and it depends on HAL for auto-mount. It's quite possible that the gconf option depends on HAL too.
Install HAL and things should be working.

---

### Post by cpg100 on 2010-05-05
I really apreciate your help but it is still not working.

garvinrick4: I had already checked media_automount_open for Nautilus on gconf-editor.

Hero of Time: I have HAL installed but didn't work too.

I don't know if this will help, but when I plug the camera the only messages about it on dmesg are:

```

32987.536026] usb 1-1: new high speed USB device using ehci_hcd and address 7
[32987.679366] usb 1-1: configuration #1 chosen from 1 choice
[32988.092055] usb 1-1: reset high speed USB device using ehci_hcd and address 7

```

So I tried:
```
sudo modprobe ehci_hcd
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module ehci_hcd not found.

```

Any ideas?

I forgot to mention that the camera appears on lsusb:
```

$lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 006: ID 046d:c525 Logitech, Inc. 
Bus 003 Device 004: ID 5543:0003 UC-Logic Technology Corp. Genius MousePen 4x3 Tablet/Aquila L1 Tablet
Bus 003 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 011: ID 04a9:314d Canon, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by crchtiger on 2010-05-07
disabling the floppy in the bios did it for me

---

### Post by archer123 on 2010-05-08
I have recently upgraded from Lucid from Hardy. Before the upgrade all worked fine. After the upgrade I have the same problem to [cpg100]("http://newyork.ubuntuforums.org/member.php?u=736658")l. USB drives are automatically detected but my USB Canon camera is not, though it is listed under lsusb. After some google searching I have discovered that if I connect the camera and turn it and then start my computer it is detected. I have already tried disabling the floppy drive in the BIOS but this made no difference.

Any help greatly appreciated.

---

### Post by alexlittle on 2010-05-09
I'm having the same issue as archer123. Running Lucid on 2 different machines (desktop and laptop), one the laptop my camera is detected fine, but on the desktop it will only appear if the camera is on and plugged in before I boot up. In the BIOS on the hard drive and CD/DVD are listed as possible boot drives (no floppy).

---

### Post by archer123 on 2010-05-10
An update to my original post.

I stated that my Canon camera is not detected, this was a mistake it is an Olympus camera which is not working. However a have also tried a Samsung camera which works fine.

I have also discovered that my Olympus camera will be detected if I connect it before I logon.

---

### Post by marcosL79 on 2010-05-10
Hi, since i upgraded from 9.10 to 10.04 my sandisk and kingston memory sticks stop beign automounted, if i do lsusb, they appear, and they had never appear in the  Places|Computer, only my dvd and HD are available, does the usb work so different now?? 

one thing i noticed is that once im logged in, if i reinstall mountusb from synaptic my memory sticks get recognized and automounted, any ideas how to solve this frustrating behavior?.:confused:

I've made a strong evangelization in my home to make them use ubuntu but now they are all complaining because of this. :-({|=

---

### Post by shelterit on 2010-05-10
Problems here, too. My devices that doesn't seem to work anymore;

- WD external 320Gb HD
- Sharp Zaurus 5500 (yes, remember those? :)
- Tevion MP3 player (crap, but always mounts everywhere, except now)

None of these mount nor come up in Nautilus, but the WD comes up in lsusb but under a different name "Initio Corporation" (which is the controller chip maker). Odd. Could that be part of the problem?

I cannot turn floppy support off (not in BIOS, but there's no floppy for booting anyways). Auto-login isn't on, nor does rebooting, in out and in login work. I'm a bit stumped and surprised. I'm not sure what to do as my searches are coming to an end of what to do next. Aargh.

(I also can no longer watch any video, no matter the codec, but that's a different thread)

---

### Post by Ron O on 2010-05-10
Disabling auto login did it for me in Xubuntu Lucid. But what is strange is that my usb devices auto mounted to the desktop WITH auto login for about a week, then stopped working. I guess I can live with logging in- probably should anyway.

Thanx all for posting. Who would have ever thunk that auto login could be the culprit?

I have always had usb issues with Canon cameras, even in Windoze. I just remove the SD card and plug it into a $5 reader.

This USB thing was causing me more severe problems. Just before the desktop loaded up I was getting a halt where I had to press the S key to skip the mounting problem and continue loading Lucid. Luckily I had made an image file of my system about an hour before these issues arose. I reloaded the system image and THAT problem went away. The rest of the fix came from your posts. 

Slightly off topic, but I HIGHLY recommend downloading the Parted Magic live cd (boot cd) and burn as an iso. It comes with an app called CloneZilla which is awesome- on the idea of Norton Ghost, only more reliable. To use, all you have to do is set the bios to boot from CD, hook up a usb hard drive, and make an image of your ubuntu partition onto the external hard drive. Since it does not image free space, it is very fast (5-10 minutes to back up or restore) and the restores are flawless. Every time my system is running perfectly, I make an image, then restore it if I have issues that I or the community cannot solve quickly. But follow the directions exactly since a few items may be counterintuitive- like you define the target first (external hard drive) and the source (your ubuntu partition) second. And you select save parts (system partition) rather than the entire disk. This program saved me 2 days work of another fresh install with all the tweaks to Firefox etc.
I just had to send them a donation.

---

### Post by Mostly.Harmless on 2010-05-22
Heaps of people have the same problem, including me. 

I just got over waiting so I went out and bought a cheap card reader, solves the problem in a roundabout type of way.

---

### Post by teedubb on 2010-05-30
[solved]

running xubuntu 10.04 had the same problem as a couple of posts earlier where automount worked for about a week then quit working.  soon as i disabled auto login it started working properly, not sure if anyone has filed a bug or not?

---

### Post by alcarola on 2010-05-31
Hi! 

I have the same problem. Disabling the floppy in BIOS makes automount work once for every time i boot my computer. If I insert a USB disk a second time, it doesn't get automounted.

Regarding IPOD, i have the same problem on an old 512MB ipod. It gets automounted once and only once per boot since i removed libgpod-common as suggested in:

[http://ubuntuforums.org/showthread.php?t=1473082](http://ubuntuforums.org/showthread.php?t=1473082)

Any clues why my disks get mounted only once?

Thanks,
Mikael

---

### Post by erikla2002 on 2010-06-02
I also have problems with automounting my SD card on my ANdroid phone. Worked perfectly in Karmic.

---

### Post by distortedstar on 2010-06-06
Not sure why this started happening to me, but it did after a recent update in Lucid (to the x.32 kernel or something). Disabling the non-existent floppy in the bios did the trick, thanks!

---

### Post by no0ne on 2010-06-07
Funny enough, most of my usb devices work just fine, had to change one firewire HD to usb in order to get it connected. eSATA also fails consistently.

What really makes me wonder though, is that iPhone 3gs mounts fine when I'm running nautilus (on a Kubuntu Lucid x64 alternative, both clean and upgraded installs,) with KDE 4.4.4 (as the default and open desktop for the moment), but not on dolphin. 

There's apparently something wrong with the way KDE automounts devices, they get listed in ls* commands, so the kernelside is playing nice, but using nautilus I can mount all media. I suspect theres something wrong with the daemon (hdparm).

One system runs on an Asus P7P55D with ICH10 chipset, another on an Asus P6T Deluxe V2 with the ICH9 chipset and finally an Acer 6920G with ICH8. All are running the latest Kubuntu Lucid x64, kernel 2.6.32-22.36. All systems have AHCI enabled with AHCI APIC 2.0 enabled, since not having these settings caused some external devices to go into a connect/disconnect loop. (eg. the iPhone 3gs and an older WD external HD).

---

### Post by efflandt on 2010-06-07
Errors polling for a non-existing floppy in 10.04 interfered with suspend/hibernate, and auto mounting USB mass storage, on an old Dell Inspiron 8200.  BIOS already showed floppy "Not Installed" and removing it from boot order did not help.  But it has a hot swap drive bay, so Linux was still looking for a floppy.

I could not **sudo rmmod floppy**, because it said it was in use.  But the following resolved it:


[LIST=1]
[*]Add **blacklist floppy** to /etc/modprobe.d/blacklist.conf (or in a new file there using sudo for your editor or gksu for gedit).
[*]Run: **sudo update-initramfs -u**
[*]Reboot
[/LIST]

---

### Post by brucemmartin on 2010-06-09
Thanks! I had the same problem on my Dell Inspiron 8200, and that worked.

---

### Post by jtgd on 2010-06-24
I have no mounting of USB (auto or otherwise) and no mount of eSATA.

I would be delighted to disable the floppy from the BIOS, but my ASUS P6X58D BIOS makes no mention of floppy *anywhere*.

What do you do in this case?

I tried the initramfs trick and the modprobe trick with no effect.

---

### Post by ghlargh on 2010-06-24
The funny thing is, it doesn't work on my laptop that i upgraded from 9.04->9.10->10.04, but everything works on my other laptop that i ran a clean 10.04 install on.

In fact, all functionality seemed to drop with each update of the older laptop, so i'm inclined to believe that i should only run clean installs in the future.

---

### Post by alcarola on 2010-07-07
See this post: [https://bugs.launchpad.net/ubuntu/lucid/+source/udisks/+bug/536670/comments/16]("https://bugs.launchpad.net/ubuntu/lucid/+source/udisks/+bug/536670/comments/16")

---

### Post by deadman62 on 2010-07-11
hello all;

has anyone ever found a fix for this?  usb mounts on boot, but will not automount.  can mount manually or with a reboot but will not automount.  thanks

---

### Post by SpyderBite on 2010-07-12
> **deadman62 said:**
> hello all;

has anyone ever found a fix for this?  usb mounts on boot, but will not automount.  can mount manually or with a reboot but will not automount.  thanks

You're luckier than me.. I can't get a mount on boot or manually or automount. I've tried every proposed fix I've found on on Google and have spent about 6 total hours in IRC on 6 different networks trying to figure this out. Nearly ready to go back to Karmic just because this stupid little bug is bothering me so much.

---

### Post by old_man0 on 2010-07-12
I have a similar problem with an umts device. After it abortes anormally on reconnect  there is the same problem.
It has to do with ehci_hcd driver.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/88746](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/88746)

[http://benbloggt.blogage.de/entries/2008/6/7/Externe-Festplatten-werden-unter-Linux-staendig-ausgeworfen-ehci_hcd](http://benbloggt.blogage.de/entries/2008/6/7/Externe-Festplatten-werden-unter-Linux-staendig-ausgeworfen-ehci_hcd)

---

### Post by deadman62 on 2010-07-13
applied all updates last night including proposed, problem still remains.  have tried majority of suggested fixes, but am still working thru the list.  sad that something this major made it into a lts release.  will post here when and if i find fix.  good luck.

---

### Post by deadman62 on 2010-07-15
update:  ok after much loading and unloading of stuff with no luck i  threw in the towel and applied this work around suggested elsewhere in  this forum. 

Open etc/modules with admin rights.

Add the following lines and save:

usb_storage
usbhid

hald is installed along with pmount and libpmount0.0, not sure if pmount  stuff is needed.

after applying the above both usb's and cd's automount and unmount and  remount without issue.  

recap:
stock install of ubuntu 10.04 on a 10yr old hp pavilion 5445 model.  it  has a built in floppy (yeah it's that old) but no way to disable floppy  in the bios as some have suggested, floppy is last in boot order.

usb  will load and mount correctly if it is in at boot up. it will NOT  automount after system has been started or if user logs off then back  on.

lsusb sees the usb flash drive and assigns the ehci_hcd to it in dmesg,  however mount makes no reference of the usb at all.  i do have a d-link  650+ wireless card loading the ndiswrapper in etc/modules to get the rf  nic working.  i've not uninstalled the ndiswrapper as some have  suggested the use of the ndiswrapper is what breaks automount.  ndiswrapper is listed before the above workaround in etc/modules.  

maybe  it's the old 1.0 usb ports in the laptop, heck maybe it's the position  of the moon.

hope this saves a few steps, time and some effort  for some folks. 

now just don't close the lid while it's  running.  good luck to all.

---

### Post by technoholic on 2010-07-25
See: [http://ubuntuforums.org/showthread.php?t=1468755&page=3](http://ubuntuforums.org/showthread.php?t=1468755&page=3)

post #25 maybe it will help

---

### Post by Krzysiek_PL on 2010-08-15
I have had the same problem since after install Ubuntu 10.04, but none of solutions explained here doesn't fixed my problem. 
After installation Ubuntu doesn't "see" neither USB storage nor DVD device, but I noticed that when system starts with pendrive plugged to USB port after Login Ubuntu has properly detected all devices (including windows partition and optical drivers)

---

### Post by eval- on 2010-08-17
> **deadman62 said:**
> update:  ok after much loading and unloading of stuff with no luck i  threw in the towel and applied this work around suggested elsewhere in  this forum. 

Open etc/modules with admin rights.

Add the following lines and save:

usb_storage
usbhid

hald is installed along with pmount and libpmount0.0, not sure if pmount  stuff is needed.

after applying the above both usb's and cd's automount and unmount and  remount without issue.  


WOW, this worked!  So WHY, after some sort of synaptic/kernel update, did usb_storage/usbhid stop getting loaded?!!?  My god, the number of people whose usb sticks are now useless in Lucid (I'm using Xubuntu) and will have no idea about modprobe ... =(

---

### Post by arseniuss on 2010-08-18
Hi i had same problem.
I used ndiswrapper for installing wifi and its destroying usb, i dont know why, but when ndiswrapper is in use i cant access to usb: sticks, mp3 etc.

Just install wifidriver with ndiswrapper (and also wifi-tools etc.) and when you get internet access just uninstall ndiswrapper. Of course restart computer!

Its helped, for me ;)

---

### Post by cypeng on 2010-08-24
I had a similar problem as Arseniuss.  The solution I found was to type on the command line:

   sudo modprobe -r ndiswrapper

Unplug/re-plug the USB device.  Then, do:

   sudo modprobe ndiswrapper

You do not have to reboot.

:)

---

### Post by Peter Veltmans on 2010-09-01
Actually, things are much more simple to solve (really !).

Just install usbmount, like so :

$ sudo apt-get install usbmount

then just plug in your usb device and... it mounts ;-)

No reboot is necessary.

HTH !

---

### Post by profdreamer on 2010-10-17
> **Peter Veltmans said:**
> Actually, things are much more simple to solve (really !).

Just install usbmount, like so :

$ sudo apt-get install usbmount

then just plug in your usb device and... it mounts ;-)

No reboot is necessary.

HTH !

Thank you! Solved this problem in Maverick Meerkat (Netbook) 10.10. Just couldn't get USB drives to automount -- tried disabling "floppy", blacklisting it.. But all it took was installing usbmount!

---

### Post by likes2skate on 2010-11-22
I recently upgraded from 8.04 to 10.04, and ever since, I have not been able to access my camera and cell phone with the USB cable.

None of the suggestions in this thread worked for me.

What did work for me was to boot 8.04.

When I installed 10.04, I kept my prior (8.04) hard drive in the box, but changed it to primary slave.  That way, when I needed to access files on my prior main hard drive, I could conveniently mount it in /mnt/temp and copy the files.

Grub2 found my prior (8.04) hard drive, and I can boot that by selecting it from the grub2 boot menu.

My USB devices auto mount no problem when I boot 8.04.  So I did that, and copied all the files I need from the USB device to the prior hard drive.  (In 8.04, I cannot mount my new main hard drive, because 8.04 does not know about ext4.)

After I copy all the files I need from the USB device, I reboot and go into 10.04 as usual.  From there, I can mount my old hard drive in /mnt/temp and copy all the files from the USB device on there.

It is a sorry state of affairs when one must backtrack to a 2 year old distribution to access a USB device.

---

### Post by surprisebloom on 2010-11-24
I have Lucid installed and I spent a lot of time trying to resolve this issue but I have never given a serious look to my fstab till today. This thread helped me out, exactly the same error:

[http://ubuntuforums.org/archive/index.php/t-1496914.html](http://ubuntuforums.org/archive/index.php/t-1496914.html)

And I thought this was a major bug.

---

### Post by likes2skate on 2010-11-28
The title of this thread suggests that the problem may have been fixed in 10.10.  Does anyone know, or should I try it?

---

### Post by likes2skate on 2010-11-29
> **likes2skate said:**
> The title of this thread suggests that the problem may have been fixed in 10.10.  Does anyone know, or should I try it?

I tried 10.10 (on the same laptop), and the situation is better, as the USB device is recognized, and I can open it with either Dolphin or Gwenview.  But I cannot actually access the camera using either application -- there is a message "The process for the camera protocol died unexpectedly."

I tried installing usbmount, and adding usb_storage & usbhid to /etc/modules, and I got the same result (cannot access camera).

---

### Post by likes2skate on 2010-11-30
To access the camera via USB, it is possible to install 8.04 on a small partition, boot to that, download the pictures there, boot to the main partition with 10.04, mount the 8.04 partition, and copy the pictures to the main partition.  

The only caveat is 8.04 uses grub version 1, so the newly installed grub 1 in an 8.04 install cannot recognize the grub 2 install in main installation.  So after installing 8.04, you need to boot from the 10.04 CD, and reinstall grub2.  Instructions are here:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

See item 13, about half way down, "Reinstalling GRUB 2 from LiveCD".

Works for me.

---

### Post by iiiears on 2012-03-02
@efflandt

blacklist floppy

Works. 

Adding your external drive to fstab works but not nearly as well.

Still no UUID /shrug

Thank you.

---

### Post by deisto on 2012-04-14
Hi, I see this wasn't yet mentioned, but it fixed my problem, where thunar crasher in xubuntu if usb is not mounted, but is clicked in thunar.
Also repaired automount problem.

[http://web.archiveorange.com/archive/v/LLXmLhyP1iKI3rMbd4qh#4MzoS48cyh2ayit](http://web.archiveorange.com/archive/v/LLXmLhyP1iKI3rMbd4qh#4MzoS48cyh2ayit)

---

### Post by kralex on 2012-09-20
profdreamer the one real solution, the  right way

---

### Post by Pogo1 on 2012-09-30
This thread seems to have two objects that are very different. USB drives and USB cameras (which was the original question). Many solutions to the mounting of drives have been posted. None to the mounting of cameras.

I have a camera that has an onboard micro-SD card. It mounts as a drive, no problem. Unmounting the drive leaves a device listed in dmesg, but no camera.

I have had this camera mount properly under 12.04 and it works as expected under Windows XP, so I know the device is ok and drivers exist for it, but  a fix under 10.04 does not exist.

Upgrading to 12.04 is not helpful. I'm on a netbook, and Unity fits in a netbook like a whale in a goldfish bowl.

Can someone guide me through what is supposed to happen when a camera is attached and help me get this to mount correctly?

Pogo.

---

