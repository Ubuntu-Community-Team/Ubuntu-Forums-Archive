---
title: "big bug - creation of ext3 filesystem on SATA crash the system"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by aledin on 2006-06-01
Dapper has a really big isse with SATA hard disk: creating an ext3 filesystem on a partition of it make crashing the system. The crash (keyboard not responding, mouse not responding, ecc...) happens with the graphical installation tool of Live CD and with mkfs.ext3 of the live cd.

The PC is a Toshiba Satellite Laptop M70

---

### Post by aledin on 2006-06-01
The quick fix was to format with another CD, then do the installation without making the partitions. Not a lucky move: the system continues to crash during the installation, when copying files to the hd.

I'll go definitely with the (old good) alternate installation cd... :)

---

### Post by theguyotc on 2006-06-01
Having similar/same problem. Hangs during install (desktop i386) right after setting up partitioning. Totally stops responding.

The system is: MSI K8T Neo-FISR2 motherboard with VIA VT8237 SATA controller, Samsung SP1614C SATA drive.

Any help would be appreciated. Been looking forward to this release for a while, and it's kind of disappointing.

---

### Post by theguyotc on 2006-06-01
Update: Tried deleting existing partitions in GParted, hung. Tried deleting partitions in PartitionMagic and ran the install again. Got farther this time before it froze, but it still froze. I'm out of ideas.

**Update 2**: Got it working. I don't know how much of this is necessary, but here's how:

1. Create partitions in Partition Magic (root and swap). Format root with ext3.
2. Boot install CD. Run GParted (Gnome Partition whatever in the System/Administration menu). Format root partition with ext3 again.
3. Run install wizard. Choose Manually Edit partitions. Don't actually need to make any changes.

Hope it helps.

---

### Post by asmath on 2006-06-03
Hello, 

I'm trying to install Dapper on a Toshiba M70 - 183 with ATI 600SE (128Mo) - SATA 80 Go, and I had have the same problem :( 

After first try, the partition has been formated in ext2 :confused: 

All attemps for formating partition with Dapper tools aren't succed, and crash system...

Wait and see.... ](*,) because Dapper upgrade fast succeed on my desktop computer....

Sorry for my frenchie english.

---

### Post by aledin on 2006-06-03
[QUOTE=asmath]Hello, 

I'm trying to install Dapper on a Toshiba M70 - 183 with ATI 600SE (128Mo) - SATA 80 Go, and I had have the same problem :( 
[/QUOTE]

Have you tried loading the kernel with the options "noapic nolapic acpi=off"? In this way the install process seems to go well.
The problem maybe is about acpi (cutting the acpi line in the kernel generate another crash for me): sadly, i have to say, because we have laptops...

This is a serious problem with Dapper, i have no one with Breezy...

---

### Post by Fr@nKy on 2006-06-03
Does this also happens with Alternate Install (the ext3partition don't work)?? (I'm having big troubles to get any of this two to work! On my case Desktop (LiveCD) does not even start and Alternate (Flight 6, Beta 2 and RC) displays an error while loading the CD components (haven't tried final yet cause I don't believe it will work)!)

---

### Post by aledin on 2006-06-03
[QUOTE=aledin]
This is a serious problem with Dapper, i have no one with Breezy...[/QUOTE]

I have opened a bug in launchpad about this: Bug #48258

Please, help to resolve this so I can use Dapper and not Fedora or Arch Linux... :)

---

### Post by Scunizi on 2006-06-08
Try using ReiserFS instead of ext3 or 2.  Also if you're running an IDE drive along side your SATA, disconnect it before installing.  I have 2 SATA's hooked up and had to follow the release notes for disabling RAID prior to the install even though I don't have RAID setup.  It just helps the system see things better without that service running.  With Flight 5 I had issues with ext3.  After 30 reboots or so the system wanted to automatically check the drives for errors.  I once let it run for 36 hours with no end in sight.  After a forced reboot it would automatically start again making the machine unusable.  ReiserFS fixed all that.

---

### Post by aledin on 2006-06-10
Thanks for the tips. I'll have more time next weeks, so i'll try installing Dapper with all the tricks I have found in the forums... I'll write here.

---

### Post by ciorba on 2006-06-10
seems to be a similar problem /same problem on toshiba satellite m70 for me.
i tried the graphical installer of beta2: crash
install with flight 5 worked, but the kernel updates always caused crashes with "kernel panic". i still have to use kernel 2.6.15-19-386. 
i made but a bug report but got no reaction at all...
see [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/45636]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/45636")

and 
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/42909]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/42909")
and also
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/47489]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/47489")

greetings

---

### Post by pete01 on 2006-06-10
Same problem here also with a Toshiba laptop.  The install hangs formatting the hard drive.

---

### Post by aledin on 2006-06-14
Two days of hacking and "breaking"... actual Dapper kernel has definitely problems with ACPI (686 and 386 kernel's version).
I'll stay with Breezy next weeks, then I'll look around for a new Dapper.1 release or I'll go with another distro (sad about it, Ubuntu is my favourite distro).

---

### Post by Scunizi on 2006-06-14
I'm having NO problems with ReiserFS.  I did have problems with ext3 on Breezy with SATA drives.  The only real issue that's really bugging me is the system won't boot with a thumb drive plugged in.  I have to remove it otherwise the system just hangs after uncompressing the kearnal.

---

### Post by armware on 2006-06-14
same issue here. i tried using reiserfs, still locks up at the same spot as with attempting the ext3 filesystem - 53%. i have an hp pavilion dv8230, with dual 80gb sata drives. any other ideas? i'm not really new to linux, but it couldn't hurt to talk to me like i'm two.

---

### Post by armware on 2006-06-15
i just tried burning the install disc again at a slower speed (4x), still locks up at 53%.
so far i feel pretty lucky as i can still boot into windows for research, but i fear that one of these times it'll remove the current bootloader then crash before it can install grub. that'll suck.
anyways, would it work the same if i tried installing an older version then did a dist-upgrade? i'm up for other ideas.

---

### Post by ciorba on 2006-06-15
you should try dapper flight 5, (no graphical installer) if it is still available some place. worked for me on my toshiba satellite m70. and then do all the updates. but you have to stick with the old kernel version (2.6.15-19-386) if it is the same problem that i have. (see above)
building a new kernel also seems to be a possible solution:
[http://www.ubuntuforums.org/showthread.php?t=196556&highlight=toshiba+m70](http://www.ubuntuforums.org/showthread.php?t=196556&highlight=toshiba+m70)

greetings

---

### Post by armware on 2006-06-15
good news, i'm writing this post in ubuntu. thanks to ciorba for the suggestion. however i couldn't find the torrent or even a direct link for the flight 5 iso, so i busted out the first ubuntu disc i burnt and still had - ubuntu 5.10.
here's what i did, i hope this helps someone.
installed ubuntu 5.10
copied the sources.list from ubuntu 6.06 (found online) and pasted into my sources.list
sudo apt-get dist-upgrade

i then rebooted and held my breath. a few errors hit the screen after the bootloader but before the ubuntu splash screen, but then moves on, no problems. needless to say i'm not worried about those errors.

since then i've even been able to get xgl/compiz going without a problem. for the record, here's my system:
nvidia go7400
dual 80gig sata hd's

i love that xgl is running at my widescreen monitors' native resolution. that was my biggest concern, but everything is going pretty smoothly.
i hope to give back help to this community as it has helped me tremendously.

---

### Post by aledin on 2006-06-16
[QUOTE=ciorba]you should try dapper flight 5, (no graphical installer) if it is still available some place. worked for me on my toshiba satellite m70. and then do all the updates. but you have to stick with the old kernel version (2.6.15-19-386) if it is the same problem that i have. (see above)
building a new kernel also seems to be a possible solution:
[http://www.ubuntuforums.org/showthread.php?t=196556&highlight=toshiba+m70](http://www.ubuntuforums.org/showthread.php?t=196556&highlight=toshiba+m70)

greetings[/QUOTE]

Thanks! I had a Flight 4 cd around and I began the installation with this. The kernel of Flight 4 works well, so now I'm in Dapper... I have tried the new kernel in security, same situation: the pc hangs.
I'll bug report that Flight 4 kernel works.

---

### Post by araz on 2006-06-16
Have anyone tried the 2.6.15-25 kernel? Does it solves toshiba satellite m70 acpi problem?

---

### Post by ciorba on 2006-06-16
i tried the new kernel - does not work for me, neither the -386 nor the -686 version

---

### Post by aledin on 2006-06-16
[QUOTE=araz]Have anyone tried the 2.6.15-25 kernel? Does it solves toshiba satellite m70 acpi problem?[/QUOTE]

It doesn't work for me. I filled a reply at bug #45636 (hope other people with the same problem write more infos about to the devs).

In the waits, I'm trying to build a custom 2.6.16ck kernel... :)

---

### Post by aledin on 2006-06-16
[QUOTE=aledin]It doesn't work for me. I filled a reply at bug #45636 (hope other people with the same problem write more infos about to the devs).

In the waits, I'm trying to build a custom 2.6.16ck kernel... :)[/QUOTE]

The kernel 2.6.16+ck works well with Toshiba Satellite M70.
I followed the instructions in this HOWTO: [http://ubuntuforums.org/showthread.php?t=157560&highlight=compile+2.6.16](http://ubuntuforums.org/showthread.php?t=157560&highlight=compile+2.6.16)

---

### Post by ciorba on 2006-06-16
any problems/difficulties building the kernel? is it worth to read through the 45 (!) pages of this thread?

---

### Post by aledin on 2006-06-16
[QUOTE=ciorba]any problems/difficulties building the kernel? is it worth to read through the 45 (!) pages of this thread?[/QUOTE]

No problem at all. All the important infos are in the first page...

If someone has free public space we can upload the .deb for the 2.6.16ck kernel, so all the people with this kernel's problem can have a rapid work-around.

---

### Post by ciorba on 2006-06-18
hi aledin,
i gave it a try, kernel worked... but it was until now not possibile for me to get wlan and fglrx working. do they work for you?
i am now compiling a second one with the new 2.6.17 kernel. let's see...

---

### Post by armware on 2006-06-18
i have a domain or two that can spare the bandwidth for the deb file. let me know, i'd love to help.

---

### Post by zasf on 2006-06-19
[QUOTE=ciorba]hi aledin,
i gave it a try, kernel worked... but it was until now not possibile for me to get wlan and fglrx working. do they work for you?[/QUOTE]

**ipw2200 (wlan)**

you need to copy the firmware from your previous kernel

sudo cp /lib/firmware/2.6.15-23-386/* /lib/firmware/2.6.16-custom -rv

reboot and wlan will be fine

**fglrx (ATI 3d driver)**

you have to compile the kernel module for your own kernel, this can be either done with module assistant or by hand, I go with the second way

```
# download the fglrx installer from ATI website
cd ~
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.25.18-x86.run
chown +x ati-driver-installer-8.25.18-x86.run
./ati-driver-installer-8.25.18-x86.run
sudo dpkg -i fglrx-kernel-source
cd /usr/src
sudo tar xvf fglrx.tar.gz
# make sure that /usr/src/linux exists and point to your own kernel source
cd linux
# let's say that your kernel is 2.6.16-custom
# the following will compile fglrx for your own kernel and make a .deb file
sudo make-kpkg --append-to-version=-custom modules_image
cd ..
# install your own fglrx module
sudo dpkg -i fglrx...blabla-custom.deb
```

I had problems with this, since the package got installed but not configured because of a missing dependancie. This is due, in my view, of a version misanderstanding.. since it looks for xorg wich is obiouvsly installed in your system

The dependancie can be manually removed as follows:

open with the help of nautilus GUI the fglrx...blabla-custom.deb that you freshly created, open control.tar.gz, edit control file and remove the dependacy line (drag out each file, it can't be modified while inside of the deb). Re-install your deb.

```
sudo dpkg -i fglrx...blabla-custom.deb
sudo depmod
```

just to be sure, try with ```
sudo modprobe fglrx
```, if it doesn't give any output you should be fine, reboot and that's it, it works!!

I'm at work right now, I'll polish this guide later this evening.

---

### Post by aledin on 2006-06-19
[QUOTE=ciorba]hi aledin,
i gave it a try, kernel worked... but it was until now not possibile for me to get wlan and fglrx working. do they work for you?
i am now compiling a second one with the new 2.6.17 kernel. let's see...[/QUOTE]

I haven't tried wlan and I have no fglrx, sorry.

---

### Post by aledin on 2006-06-19
[QUOTE=armware]i have a domain or two that can spare the bandwidth for the deb file. let me know, i'd love to help.[/QUOTE]

I can give you a kernel image to upload: it works for all the piece of my PC (and the initial splash at boot works too...) and it has the config of the default ubuntu kernel.
If you want, i can send it via email to you.

---

### Post by aledin on 2006-06-20
[QUOTE=aledin]I haven't tried wlan and I have no fglrx, sorry.[/QUOTE]

For ipw2200 I had to download the firmware package from [http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/), 'cause the ubuntu firmware for 2.6.15 has different file names.

---

### Post by ciorba on 2006-06-20
so much help from italy...thank you alessandro and matteo  :D 
and also thanks to armware. if we are in need for a place to upload something... ;) 
i am now building a new kernel, and i expected it to work completely: i had some problems with the xorg-driver-fglrx which are now solved...i hope
if that is done, i am going try matteo's suggestions.

---

### Post by jfilip on 2006-06-20
After compiling the 2.6.16-ck kernel sources I had a tough time getting my wireless to work using wpasupplicant.  Eventually I used -Dwext and it worked like a charm.  So if you've recompiled your kernel and are using the ieee80211 and ipw2200 source downloaded form Sourceforge to get the wireless working with wpasupplicant and can't seem to make it work using -Dwipw.  Try -Dwext.

My ACPI works fine, as does everything else, now.  The only issue I have is that if I leave my laptop sitting around for a while it will blank the screen and then I have to force it to shut off with the power button as I can't make it resume.  That may possibly be due to something I set incorrectly in /etc/default/acpi-support, though.

---

### Post by aledin on 2006-06-21
The deb package for kernel 2.6.16 (+ck patches), thanks to armware, is at:
[http://www.armware.net/linux](http://www.armware.net/linux)

The kernel is for 686 systems. Hope it'll helps.

---

### Post by LazyTux on 2006-10-04
I know this is an old thread, but has this issue gotten a known fix yet?  

I just got a new Sony VAIO with a SATA, and I'm running into the same problem.  I've tried ext3 and reiserfs, creating the partitions before hand using the gnome partition tool, and a tool from sysresccd.org, and have had no luck.  I've even tried Xubuntu just for kicks.  I can usually create the partitions, but ubuntu won't continue without formatting the partition, and it bombs on 15%, every single time.  

Has anybody found a good fix for ths problem?  I'm using Dapper, but I don't have access yet to the alternate install or a breezy install disc at the moment, but I will be trying those sometime over the next few days.

---

### Post by armware on 2006-10-04
what worked for me was installing ubuntu 5.10, replacing the entire apt-get sources list with the default list for dapper and running apt-get dist-upgrade.

---

### Post by LazyTux on 2006-10-04
Thanks, I will try and download Breezy tonight and do an upgrade to Dapper, will post the results tomorrow.

Also, I'm locking up repeatedly now just trying to create a Ext3 partition using the rescue cd from sysresccd.org using run_qtparted...is it possible this is a system problem and not a Dapper problem?

Another (probably dumb) question...how do I add the options for the kernel to turn the acpi off on the install?  I hit the "options" command on the bootup screen on the graphical installer, I tacked "noapic nolapic acpi=off" to the very end of the options...but still had the same problems, was this correct?

---

### Post by LazyTux on 2006-10-04
Update:  

After much dismay, I have downloaded:

1) Ubuntu Breezy (5.10)
2) Ubuntu Dapper (graphical)
3) Ubuntu Edgy Beta (graphical)
4) Ubuntu Edgy Beta (alternate)

Thus far, none of these have worked.  Breezy, however, did get the farthest, after it installed the boot loader and rebooted to finish configuration, it stops with the error "ata1: BUG timeout before command".  Apparently other people have had this issue with Breezy as well, and I haven't found a fix for it either.  

On another note, Edgy gets to the same 15% marker, but just stops, although it doesn't lock the whole system like Dapper, it just doesn't do anything anymore.  

I'm downloading Dapper Alternate...although I don't have my hopes up for it either.  

I have tried installing graphically and in text mode with noapic and nolapic and even nodma, but they made no difference.  Are there any other suggestions perhaps?

---

