---
title: "Installing Ubuntu"
date: 2005-04-22
forum: Installation &amp; Upgrades
---

### Post by rlcoach on 2005-04-22
I had trouble installing ubuntu on a PC last night, didnt record all the error messages down as I was in a bit of a rush.  Anyway, tonight I am going to start over (with more patience and less wine). A couple of questions though before I start:-

My PC is an Athlon 3200 (ish) with 512mb RAM, connecting to a wireless mouse and usb keyboard via a belkin USB KVM. My monitor is a 19" tft.

Should I be making life easier for the installation by removing the KVM temporarly whilst I install ubuntu? Also will I get any resolution problems running with a 19" tft for the install (i.e. disapearing text). 

Thanks in advance for any help or advice.

Andrew :???:

---

### Post by heimo on 2005-04-22
If you had trouble with keyboard or mouse, bypass the KVM for now. For the monitor part of question, I can't give an answer. Maybe, maybe not. Did you have any trouble with your monitor, like ... for example, disappearing text? :-D
 
Just take it easy, step by step. If you select some options which are not default, make notes, so you don't have to try same settings again, if they fail (and it's easier to ask for help if you know what you did).
 
What should I say? Good luck. Hopefully you won't have problems this time. Helps to have your hardware specifications handy - information about graphics card, which X driver you should be using (if autodetection doesn't work), monitor manual can also come handy (not neccessarily, but may).
 
If you don't know what to answer in some question about configuration, go with the suggested values / defaults. Oh, and if possible, check that you're installation media (CD) is ok - run md5sum on it and compare with the value in the root directory where you downloaded it from (MD5SUMS)
 
Program for Windows here:
[http://www.linuxiso.org/viewdoc.php/verifyiso.html]("http://www.linuxiso.org/viewdoc.php/verifyiso.html")
 
And if possible, get the Live-CD too - so you can try it - and see if there is difference booting Live-CD and your actual installation.
 
Hmm.. :) There.

---

### Post by rlcoach on 2005-04-22
[QUOTE=heimo]If you had trouble with keyboard or mouse, bypass the KVM for now. For the monitor part of question, I can't give an answer. Maybe, maybe not. Did you have any trouble with your monitor, like ... for example, disappearing text? :-D
 
Just take it easy, step by step. If you select some options which are not default, make notes, so you don't have to try same settings again, if they fail (and it's easier to ask for help if you know what you did).
 
What should I say? Good luck. Hopefully you won't have problems this time. Helps to have your hardware specifications handy - information about graphics card, which X driver you should be using (if autodetection doesn't work), monitor manual can also come handy (not neccessarily, but may).
 
If you don't know what to answer in some question about configuration, go with the suggested values / defaults. Oh, and if possible, check that you're installation media (CD) is ok - run md5sum on it and compare with the value in the root directory where you downloaded it from (MD5SUMS)
 
Program for Windows here:
[http://www.linuxiso.org/viewdoc.php/verifyiso.html]("http://www.linuxiso.org/viewdoc.php/verifyiso.html")
 
And if possible, get the Live-CD too - so you can try it - and see if there is difference booting Live-CD and your actual installation.
 
Hmm.. :) There.[/QUOTE]


Thanks alot for the info. I did have trouble with my keyboard/mouse but I thought it may have been because I was working on my Mac (switched the KVM) so that maybe it didnt detect the mouse/keyboard properly.

I had a bit of missing text at one point but think the monitor maybe will be okay, but must admit had trouble finding how to change partition sizes, I suspected missing text (either that or the interface is retarded).

All through installation I was getting a weird usb device error, and then in the end   ubuntu was complaining some packages hadnt been installed correctly. Tonight I will be starting earlier and will be less intoxidated (although depending on installation success this may change).

---

### Post by heimo on 2005-04-22
Did you get to verify if your network connection was ok? Did it install packages from internet?
 
If after install all you get is a black screen, hit ctrl+alt+F1 to get into console (command prompt). Log in with your username and password, run ```
sudo su -
``` to become root (super user) and run:
```

dpkg-reconfigure -a
apt-get install -f
apt-get update
apt-get upgrade

``` 
 
If you can't get X working, reconfigure it:
```
 dpkg-reconfigure xserver-xorg
``` 
Try putting a little pessimistic resolution to get it working at all.
 
If you get warnings that you don't have permission to do something, put *sudo *in front of the command to run it with root permissions. The password is the one you set for your regular user account.
 
If you have computer with internet access while you're installing, keep this forum open, search and ask if needed.
 
Some of the command line commands are the same as in MS-DOS (if you're familiar). Sorry if this is too simple stuff for you (someone out there won't know this).
 
To change directory: cd [dirname]
To list directory contents: ls
To view text file: less [filename]
To edit file: nano [filename]
To rename or move file: mv [from] [to]
To remove file: rm [filename]
To get information on command: man [command]
To get list of parameters: [command] -h
 
There's command line history, you can use up arrow and down arrow to browse the commands you have entered. There's tab completion, you can enter for example *cd /et* and press tabulator key (->) and you'll get *cd /etc/* - it's very useful.
 
You can restart graphical userinterface like this:
```
 sudo /etc/init.d/gdm restart
``` 
which should give you a login window. Or you can just enter *startx *and you should end up straight on desktop (Gnome by default).
 
You didn't ask for all of this. But I suspect that if you run in trouble, some of this will be helpful.

---

### Post by rlcoach on 2005-04-22
Sadly it all went a bit pear shaped.

I created 2 partitions a 40gig root and 2 gig swap. I unplugged all my usb devices, leaving only my keyboard and mouse. I booted from ubuntu cd.

All seemed to be going well I picked the language, the keyboard layout put in a name for the computer and watched the progress bar slowly sweep along. The reboot came, then the scrolling mess of text saying things were unpacking and setting up etc. Eventually I get a blue screen saying not all packages had setup correctly you can either reinstall or go through package manager now and try to fix. Sadly though I could neither select yes or no or anything. My keyboard had ceased working. I have no idea whether its the keyboard that is the problem or something more serious. Like I said earlier, my keyboard was working fine earlier in the installation.

I have Windows XP and Mac OS X and had been persuaded to try ubuntu out as it was so easy to use but sadly it looks (at least at the moment) not to be.

 :-x  ](*,)

---

### Post by heimo on 2005-04-23
Sorry to hear that. You could try to check the installation media, that MD5 matches the one that's in MD5SUMS file in the directory you downloaded the file from. 
[http://www.linuxiso.org/viewdoc.php/verifyiso.html](http://www.linuxiso.org/viewdoc.php/verifyiso.html)
[http://se.releases.ubuntu.com/5.04/MD5SUMS](http://se.releases.ubuntu.com/5.04/MD5SUMS)

Another thing that may help to get around this problem is to first make much more limited install, selecting server installation in the very beginning of installation. That'll leave graphical user interface (Xorg/Gnome) out and minimize the possibility of broken packages. Then you can log in the console and install ubuntu-dekstop package with apt-get (sudo apt-get install ubuntu-desktop).

Be sure to edit /etc/apt/sources.list to comment out (prefix with #) lines which refer to your installation CD.

Also, order the installtion CDs from Ubuntu main site - it'll take some time, but you'll get nice CD's and you'll know that it's at least not about the installation media.

---

### Post by rlcoach on 2005-04-23
[QUOTE=heimo]Sorry to hear that. You could try to check the installation media, that MD5 matches the one that's in MD5SUMS file in the directory you downloaded the file from. 
[http://www.linuxiso.org/viewdoc.php/verifyiso.html](http://www.linuxiso.org/viewdoc.php/verifyiso.html)
[http://se.releases.ubuntu.com/5.04/MD5SUMS](http://se.releases.ubuntu.com/5.04/MD5SUMS)

Another thing that may help to get around this problem is to first make much more limited install, selecting server installation in the very beginning of installation. That'll leave graphical user interface (Xorg/Gnome) out and minimize the possibility of broken packages. Then you can log in the console and install ubuntu-dekstop package with apt-get (sudo apt-get install ubuntu-desktop).

Be sure to edit /etc/apt/sources.list to comment out (prefix with #) lines which refer to your installation CD.

Also, order the installtion CDs from Ubuntu main site - it'll take some time, but you'll get nice CD's and you'll know that it's at least not about the installation media.[/QUOTE]

Thanks for the help...

I just did a test on it with MD5sums for windows. I ran it against the CD and it came up with 6 errors, 4 files didnt match the checksums and 2 files didnt exist.

Is this an issue with the ISO or the cd writing process? Do I just need to burn again? and test before re-installing?

Here are the errors, dont know if it will make sense to anybody...

.\install\netboot\pxelinux.cfg\default ERROR: F:\.\install\netboot\pxelinux.cfg\default does not exists.
.\install\netboot\pxelinux.0 ERROR: Checksum did not match.
.\pool\main\l\linux-source-2.6.10\linux-headers-2.6.10-5_2.6.10-34_i386.deb ERROR: Checksum did not match.
.\pool\main\l\linux-kernel-headers\linux-kernel-headers_2.5.999-test7-bk-17_i386.deb ERROR: Checksum did not match.
.\pool\main\l\language-pack-yi\language-pack-yi_20050406_all.deb ERROR: Checksum did not match.
.\pool\main\m\mozilla-firefox-locale-all\mozilla-firefox-locale-en-gb_1.0.1lang20050309ubuntu1-0ubuntu3_all.deb ERROR: F:\.\pool\main\m\mozilla-firefox-locale-all\mozilla-firefox-locale-en-gb_1.0.1lang20050309ubuntu1-0ubuntu3_all.deb does not exists.

---

### Post by heimo on 2005-04-23
[QUOTE=rlcoach]
Is this an issue with the ISO or the cd writing process? Do I just need to burn again? and test before re-installing?
[/QUOTE]

Hopefully it's just the CD and not a hardware (burner) malfunction or hardware conflict in Ubuntu. Sure sounds like a bad CD, so what I'd do next is check the isofile (not the CD, but the file), and check if the checksum (MD5) matches the one in MD5SUMS file. If that's ok, you don't need to download it again.

Of course, if it's bad, you should download it again, before burning a new installation CD. If you can do it on different burned, that'd be good thing to do (but not a must), you could also select lower recording speed, for example x4 (sometimes helps to make better working CDs).

---

### Post by rlcoach on 2005-04-23
[QUOTE=heimo]Hopefully it's just the CD and not a hardware (burner) malfunction or hardware conflict in Ubuntu. Sure sounds like a bad CD, so what I'd do next is check the isofile (not the CD, but the file), and check if the checksum (MD5) matches the one in MD5SUMS file. If that's ok, you don't need to download it again.

Of course, if it's bad, you should download it again, before burning a new installation CD. If you can do it on different burned, that'd be good thing to do (but not a must), you could also select lower recording speed, for example x4 (sometimes helps to make better working CDs).[/QUOTE]

I downloaded and burned at work which is quite handy in a way. I am now downloading a fresh at home and will burn and try again (after checking MD5).

Fingers crossed, was close to giving up, will be made up if it now works.

---

### Post by fordfan753 on 2005-04-23
Can't you get a normal keyboard and mouse from somewhere? They'll work much better in the install...why have USB for peripherals anyway..I just find it unnecessary. I function fine on my PS/2 devices which my friends spend ages trying to get their USB stuff to work perfectly. I think you will have much more success in the installer with PS/2 devices.

---

### Post by rlcoach on 2005-04-23
[QUOTE=rlcoach]I downloaded and burned at work which is quite handy in a way. I am now downloading a fresh at home and will burn and try again (after checking MD5).

Fingers crossed, was close to giving up, will be made up if it now works.[/QUOTE]

Sadly, downloaded and burned and reran the m5 check and so far the same files are coming across as not matching. Looks like the CD was fine and the install failed for other reasons.

---

### Post by rlcoach on 2005-04-23
[QUOTE=fordfan753]Can't you get a normal keyboard and mouse from somewhere? They'll work much better in the install...why have USB for peripherals anyway..I just find it unnecessary. I function fine on my PS/2 devices which my friends spend ages trying to get their USB stuff to work perfectly. I think you will have much more success in the installer with PS/2 devices.[/QUOTE]

I use a USB keyboard and mouse because I share them between my PC and a PowerMac, the powermac only has usb ports. Also I run a logitech wireless mouse too.

I could find a a ps2 keyboard and mouse for install though.

---

### Post by heimo on 2005-04-23
Ok. Can you post the error messages you get? Which packages fail to install and what kind of errors you get about USB? Any other errors?

While installing, you can change between different consoles using ctrl+alt+F1,2,3,4 - There's more information on some of these. If you see any errors or warnings, make some notes and post them, if possible.

Also more details about your hardware could help. Is the hard disk SATA? I had some problems with my SATA disks at first. Can you try the 'server' install method?

To solve this problem (if you're still interested, I hope you're!) we need a better understanding of what exactly is causing this. What are the very first errors you get. There is most probably way to install Ubuntu on your computer, I'm quite sure of it.

Wireless keyboard and mouse are not probable reason. However KVM can cause problems, so keep the reveiver connected directly to the computer.

Also, consider trying the Ubuntu live-cd.


EDIT: 
I'm using - and used during install - this Logitech "cordless desktop":
[http://www.logitech.com/index.cfm/products/details/US/EN,CRID=2162,CONTENTID=8062](http://www.logitech.com/index.cfm/products/details/US/EN,CRID=2162,CONTENTID=8062)

---

### Post by rlcoach on 2005-04-23
[QUOTE=rlcoach]Sadly, downloaded and burned and reran the m5 check and so far the same files are coming across as not matching. Looks like the CD was fine and the install failed for other reasons.[/QUOTE]

My latest MD5 check produced following errors.

.\install\netboot\pxelinux.cfg\default ERROR: F:\.\install\netboot\pxelinux.cfg\default does not exists.
.\install\netboot\pxelinux.0 ERROR: Checksum did not match.
.\pool\main\m\mozilla-firefox-locale-all\mozilla-firefox-locale-en-gb_1.0.1lang20050309ubuntu1-0ubuntu3_all.deb ERROR: F:\.\pool\main\m\mozilla-firefox-locale-all\mozilla-firefox-locale-en-gb_1.0.1lang20050309ubuntu1-0ubuntu3_all.deb does not exists.

---

### Post by rlcoach on 2005-04-23
For my second install I took my KVM out the equation but it made no difference. I couldnt really see the errors as the scrolliing text went so past so quickly. I only really got a proper error when it ground to a halt. I will try one more install and record everything down.

My system specs are as follows:-

Medion Athlon XP 3200+ with 512mb RAM
nVidia GeForce FX5200
Pioneer DVD RW DVR-106D
Sony DVD Rom DDU1612
Seagate Barracuda ST3160021A (Ultra ATA/100)
Medion TV Tuner
Microsoft USB Digital Media Pro Keyboard
Logitech Wireless MX Laser mouse
Creatix Modem
Nevo F-419 19" TFT Monitor
Via Rhine II Fast Ethernet
4 card reader slot at front of PC.

USB Peripherals to plug in afterwards (not plugged in during install).

Logitech Webcam
USB Hub
USB HP IPAQ PDA Cradle
External soundcard (Creative Extigy)
USB KVM
Firewire Camera

---

### Post by heimo on 2005-04-23
Is it possible that the CD drive is not working correctly? I don't think this is a probable cause, but it's a possibility. Though it would be quite odd if you'd get so similar results from checksum tests.

Those packages didn't look like something that would prevent installation (I'm not 100% sure, but quite close). If I'd have same program to test same ISO, I'd do it - but I don't have CD drive on my only Windows machine.

You could try to do minimal install and check if you get any errors. It's important to know at which specific part of installation the problems start. Some failing driver / module or bad partition table or power management problems or undetected device can cause wide range of problems.

If you want to try, you could change the disk access mode in BIOS (only do this if you don't have anything to lose on the hard disk) - try different settings: normal, large, LBA.

EDIT: We posted quite much same time. Do you know the model of your motherboard? Or the chipset?

Do the problems start during the first part of insallation, or only after reboot? Does the second part of installation halt always at the same point?

---

### Post by rlcoach on 2005-04-23
[QUOTE=heimo]Is it possible that the CD drive is not working correctly? I don't think this is a probable cause, but it's a possibility. Though it would be quite odd if you'd get so similar results from checksum tests.

Those packages didn't look like something that would prevent installation (I'm not 100% sure, but quite close). If I'd have same program to test same ISO, I'd do it - but I don't have CD drive on my only Windows machine.

You could try to do minimal install and check if you get any errors. It's important to know at which specific part of installation the problems start. Some failing driver / module or bad partition table or power management problems or undetected device can cause wide range of problems.

If you want to try, you could change the disk access mode in BIOS (only do this if you don't have anything to lose on the hard disk) - try different settings: normal, large, LBA.

EDIT: We posted quite much same time. Do you know the model of your motherboard? Or the chipset?

Do the problems start during the first part of insallation, or only after reboot? Does the second part of installation halt always at the same point?[/QUOTE]


CD Drive has been fine upto now. I could try using my DVD drive instead on boot.

Not sure on Motherboard, will try find out.

I am downloading live CD too to see what happens with that.

---

### Post by rlcoach on 2005-04-23
NEWSFLASH

Made new CD.
Used ps/2 mouse and keyboard

I have now got the bad boy GUI brown screen up.

Just have to plug all my usb devices in..........

---

### Post by heimo on 2005-04-23
Great!

Hopefully you can get most of your USB stuff working easier than the base install was. Any ideas was the problem with CD or keyboard?

---

### Post by rlcoach on 2005-04-23
Forgive my stupid questions I will be more self sufficient in searching for solutions to things I dont know when I`m not typing at a weird angle and smashing my old broken mouse every 2 minutes (because my usb keyboard and mouse are not installed).

How do I install my usb keyboard and mouse? And for that matter any usb device?

I have tried plugging my usb mouse in whilst the pooter is on, and I get no response or feedback - it doesnt work. NOTE: this is whilst there is a ps/2 mouse still in.

I have also plugged usb mouse in and rebooted, this resulted in neither my ps/2 or usb mouse working, again no feedback.

Forgive my noob-ness.

---

### Post by rlcoach on 2005-04-23
[QUOTE=heimo]Great!

Hopefully you can get most of your USB stuff working easier than the base install was. Any ideas was the problem with CD or keyboard?[/QUOTE]

Am going to install mouse and keyboard one at a time making sure each survives reboots.

Then will plug in kvm and try install all my other stuff.

See my just posted previous reply re: not knowing how to install mouse

---

### Post by rlcoach on 2005-04-23
Anyway I can debug my USB ports. I have tried 2 usb mice and neither work. 

Also I dont know if they are related or if its an issue but on boot starting hotplug subsystem seems to take very long time on boot. 

Any ideas?

If there are problems on boot, is there some sort of log?

---

### Post by heimo on 2005-04-23
General log:
less /var/log/messages

Bootlog (watch this just after boot):
dmesg | less

To reconfigure Xorg (to change mouse/keyboard) use
 ```
dpkt-reconfigure xserver-xorg
``` 
(this will make new xorg.conf)

You could also check if modules for usb are loaded:

lsmod | grep hcd
 ```
ehci_hcd			   32708  0 
uhci_hcd			   32816  0 
usbcore			   119000  3 ehci_hcd,uhci_hcd

``` 

Also check what you can find in:
System->Administration->DeviceManager
can you see USB devices?

Try lsusb to list usb devices.

Run tail -f /var/log/messages in one terminal while plugging in USB devices and see if you get a notice of new device.

---

### Post by rlcoach on 2005-04-23
[QUOTE=heimo]General log:
less /var/log/messages

Bootlog (watch this just after boot):
dmesg | less

To reconfigure Xorg (to change mouse/keyboard) use
 ```
dpkt-reconfigure xserver-xorg
``` 
(this will make new xorg.conf)

You could also check if modules for usb are loaded:

lsmod | grep hcd
 ```
ehci_hcd			   32708  0 
uhci_hcd			   32816  0 
usbcore			   119000  3 ehci_hcd,uhci_hcd

``` 

Also check what you can find in:
System->Administration->DeviceManager
can you see USB devices?

Try lsusb to list usb devices.

Run tail -f /var/log/messages in one terminal while plugging in USB devices and see if you get a notice of new device.[/QUOTE]

Here are the messages I get when pluggin in basic standard usb mouse,

Apr 23 19:32:18 localhost kernel: usb 2-1: new low speed USB device using uhci_h cd and address 6
Apr 23 19:32:19 localhost kernel: usb 2-1: khubd timed out on ep0in
Apr 23 19:32:24 localhost kernel: usb 2-1: khubd timed out on ep0out
Apr 23 19:32:30 localhost kernel: usb 2-1: khubd timed out on ep0out
Apr 23 19:32:30 localhost kernel: usb 2-1: new low speed USB device using uhci_h cd and address 7
Apr 23 19:32:31 localhost kernel: usb 2-1: khubd timed out on ep0in
Apr 23 19:32:36 localhost kernel: usb 2-1: khubd timed out on ep0out

This is what I get when I plug in wireless usb mouse.

Apr 23 19:36:06 localhost kernel: usb 3-2: new low speed USB device using uhci_hcd and address 2
Apr 23 19:36:07 localhost kernel: uhci_hcd 0000:00:10.2: Unlink after no-IRQ?  Different ACPI or APIC settings may help.
Apr 23 19:36:08 localhost kernel: usb 3-2: khubd timed out on ep0in
Apr 23 19:36:13 localhost kernel: usb 3-2: khubd timed out on ep0out
Apr 23 19:36:18 localhost kernel: usb 3-2: khubd timed out on ep0out
Apr 23 19:36:18 localhost kernel: usb 3-2: new low speed USB device using uhci_hcd and address 3
Apr 23 19:36:19 localhost kernel: usb 3-2: khubd timed out on ep0in
Apr 23 19:36:25 localhost kernel: usb 3-2: khubd timed out on ep0out

When plugging ipod shuffle in (dont know what would happen usually, should map a drive?)

Apr 23 19:37:23 localhost kernel: usb 5-3: new high speed USB device using ehci_hcd and address 6
Apr 23 19:37:24 localhost kernel: ehci_hcd 0000:00:10.4: Unlink after no-IRQ?  Different ACPI or APIC settings may help.
Apr 23 19:37:24 localhost kernel: usb 5-3: khubd timed out on ep0in
Apr 23 19:37:29 localhost kernel: usb 5-3: khubd timed out on ep0out
Apr 23 19:37:34 localhost kernel: usb 5-3: khubd timed out on ep0out
Apr 23 19:37:35 localhost kernel: usb 5-3: new high speed USB device using ehci_hcd and address 7
Apr 23 19:37:36 localhost kernel: usb 5-3: khubd timed out on ep0in


Also usb modules loaded.

ehci_hcd               29444  0
uhci_hcd               30224  0
usbcore               107384  3 ehci_hcd,uhci_hcd

---

### Post by heimo on 2005-04-23
Sounds like you could use this solution:
[http://www.ubuntuforums.org/showpost.php?p=131614&postcount=10](http://www.ubuntuforums.org/showpost.php?p=131614&postcount=10)

---

### Post by rlcoach on 2005-04-23
[QUOTE=heimo]Sounds like you could use this solution:
[http://www.ubuntuforums.org/showpost.php?p=131614&postcount=10](http://www.ubuntuforums.org/showpost.php?p=131614&postcount=10)[/QUOTE]

Where abouts would I put NOAPIC and ACPI=OFF in the file? Do I word it just like that?

How can I change the read only file?

---

### Post by heimo on 2005-04-23
I don't use grub, so I don't even have that configfile in my system. But somewhere there is probably a place to put kernel parameters - it can be on it's own line or it can be on the same line with the kernel filename.

Oh, here's example and other things you may want to read before proceeding:
[http://www.ubuntuforums.org/showthread.php?t=2620&highlight=grub+noacpi]("http://www.ubuntuforums.org/showthread.php?t=2620&highlight=grub+noacpi")

That modules file edit applies to your scenario too. You want to try apm

---

### Post by rlcoach on 2005-04-23
[QUOTE=heimo]I don't use grub, so I don't even have that configfile in my system. But somewhere there is probably a place to put kernel parameters - it can be on it's own line or it can be on the same line with the kernel filename.

Oh, here's example and other things you may want to read before proceeding:
[http://www.ubuntuforums.org/showthread.php?t=2620&highlight=grub+noacpi]("http://www.ubuntuforums.org/showthread.php?t=2620&highlight=grub+noacpi")

That modules file edit applies to your scenario too. You want to try apm[/QUOTE]

Made the changes and rebooted, doesnt seem to have made any difference. I am fedup.

Is the boot part when it starts the hotplug sub system and takes a long time - is that the key to my problems? 

 ](*,)

---

### Post by heimo on 2005-04-23
Yeah, that's probably a very good clue.

Open two terminals. On one, run ```
tail -f /var/log/messages
```  and on the other run ```
sudo /etc/init.d/hotplug restart
```

Check what's going on. Somethings probably wrong. Is the apm now loaded? Run *lsmod | grep apm *and if you don't get a line with apm, try *modprobe apm *

If apm makes no difference, undo the changes to grub and /etc/modules and restart - and try the hotplug restart again.

That's what I'd do. :) But hey! Take breaks, don't get frustrated - it's a computer after all. :)

You've done great job solving the problems so far!

---

### Post by rlcoach on 2005-04-24
I have run the thing that you said and have included the results below. Also double checked and it says APM is running

Apr 24 08:12:52 localhost kernel: ehci_hcd 0000:00:10.4: remove, state 1
Apr 24 08:12:52 localhost kernel: usb usb5: USB disconnect, address 1
Apr 24 08:12:52 localhost kernel: ehci_hcd 0000:00:10.4: USB bus 5 deregistered
Apr 24 08:12:52 localhost kernel: uhci_hcd 0000:00:10.0: remove, state 1
Apr 24 08:12:52 localhost kernel: usb usb1: USB disconnect, address 1
Apr 24 08:12:52 localhost kernel: uhci_hcd 0000:00:10.0: USB bus 1 deregistered
Apr 24 08:12:52 localhost kernel: uhci_hcd 0000:00:10.1: remove, state 1
Apr 24 08:12:52 localhost kernel: usb usb2: USB disconnect, address 1
Apr 24 08:12:52 localhost kernel: uhci_hcd 0000:00:10.1: USB bus 2 deregistered
Apr 24 08:12:52 localhost kernel: uhci_hcd 0000:00:10.2: remove, state 1
Apr 24 08:12:52 localhost kernel: usb usb3: USB disconnect, address 1
Apr 24 08:12:53 localhost kernel: uhci_hcd 0000:00:10.2: USB bus 3 deregistered
Apr 24 08:12:53 localhost kernel: uhci_hcd 0000:00:10.3: remove, state 1
Apr 24 08:12:53 localhost kernel: usb usb4: USB disconnect, address 1
Apr 24 08:12:53 localhost kernel: uhci_hcd 0000:00:10.3: USB bus 4 deregistered
Apr 24 08:12:53 localhost kernel: usbcore: deregistering driver usbfs
Apr 24 08:12:53 localhost kernel: usbcore: deregistering driver hub
Apr 24 08:12:53 localhost input.agent[7803]:      evdev: already loaded
Apr 24 08:12:53 localhost input.agent[7803]:      evbug: blacklisted
Apr 24 08:12:53 localhost input.agent[7831]:      tsdev: already loaded
Apr 24 08:12:53 localhost input.agent[7831]:      mousedev: already loaded
Apr 24 08:12:53 localhost input.agent[7831]:      evdev: already loaded
Apr 24 08:12:53 localhost input.agent[7831]:      evbug: blacklisted
Apr 24 08:12:53 localhost input.agent[7883]:      evdev: already loaded
Apr 24 08:12:53 localhost input.agent[7883]:      evbug: blacklisted
Apr 24 08:12:53 localhost isapnp.rc[7912]:      rtc: loaded sucessfully
Apr 24 08:12:53 localhost isapnp.rc[7912]:      pcspkr: loaded sucessfully
Apr 24 08:12:54 localhost isapnp.rc[7912]:      psmouse: loaded sucessfully
Apr 24 08:12:54 localhost isapnp.rc[7912]:      floppy: loaded sucessfully
Apr 24 08:12:54 localhost isapnp.rc[7912]:      parport_pc: loaded sucessfully
Apr 24 08:12:54 localhost isapnp.rc[7912]:      analog: loaded sucessfully
Apr 24 08:12:54 localhost pci.agent[8026]:      via-agp: already loaded
Apr 24 08:12:54 localhost pci.agent[8055]:      shpchp: blacklisted
Apr 24 08:12:54 localhost pci.agent[8055]:      pciehp: blacklisted
Apr 24 08:12:54 localhost pci.agent[8099]:      saa7134: already loaded
Apr 24 08:12:54 localhost pci.agent[8148]:      ohci1394: already loaded
Apr 24 08:12:54 localhost pci.agent[8177]:      via82cxxx: already loaded
Apr 24 08:12:54 localhost kernel: usbcore: registered new driver usbfs
Apr 24 08:12:54 localhost kernel: usbcore: registered new driver hub
Apr 24 08:12:54 localhost kernel: USB Universal Host Controller Interface driver v2.2
Apr 24 08:12:55 localhost kernel: uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Apr 24 08:12:55 localhost kernel: uhci_hcd 0000:00:10.0: irq 21, io base 0xd800
Apr 24 08:12:55 localhost kernel: uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Apr 24 08:12:55 localhost kernel: hub 1-0:1.0: USB hub found
Apr 24 08:12:55 localhost kernel: hub 1-0:1.0: 2 ports detected
Apr 24 08:12:55 localhost kernel: uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
Apr 24 08:12:55 localhost usb.agent[8375]:      usbcore: already loaded
Apr 24 08:12:55 localhost kernel: uhci_hcd 0000:00:10.1: irq 21, io base 0xdc00
Apr 24 08:12:55 localhost kernel: uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Apr 24 08:12:55 localhost kernel: hub 2-0:1.0: USB hub found
Apr 24 08:12:55 localhost kernel: hub 2-0:1.0: 2 ports detected
Apr 24 08:12:55 localhost kernel: uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
Apr 24 08:12:55 localhost usb.agent[8435]:      usbcore: already loaded
Apr 24 08:12:55 localhost kernel: uhci_hcd 0000:00:10.2: irq 21, io base 0xe000
Apr 24 08:12:55 localhost kernel: uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Apr 24 08:12:55 localhost kernel: hub 3-0:1.0: USB hub found
Apr 24 08:12:55 localhost kernel: hub 3-0:1.0: 2 ports detected
Apr 24 08:12:55 localhost kernel: uhci_hcd 0000:00:10.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#4)
Apr 24 08:12:55 localhost usb.agent[8495]:      usbcore: already loaded
Apr 24 08:12:55 localhost kernel: uhci_hcd 0000:00:10.3: irq 21, io base 0xe400
Apr 24 08:12:55 localhost kernel: uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Apr 24 08:12:55 localhost kernel: hub 4-0:1.0: USB hub found
Apr 24 08:12:55 localhost kernel: hub 4-0:1.0: 2 ports detected
Apr 24 08:12:55 localhost pci.agent[8206]:      uhci-hcd: loaded successfully
Apr 24 08:12:55 localhost usb.agent[8577]:      usbcore: already loaded
Apr 24 08:12:55 localhost pci.agent[8555]:      uhci-hcd: already loaded
Apr 24 08:12:55 localhost pci.agent[8633]:      uhci-hcd: already loaded
Apr 24 08:12:55 localhost kernel: usb 2-2: new full speed USB device using uhci_hcd and address 2
Apr 24 08:12:56 localhost pci.agent[8662]:      uhci-hcd: already loaded
Apr 24 08:12:56 localhost kernel: Initializing USB Mass Storage driver...
Apr 24 08:12:56 localhost kernel: ehci_hcd 0000:00:10.4: VIA Technologies, Inc. USB 2.0
Apr 24 08:12:56 localhost kernel: ehci_hcd 0000:00:10.4: irq 21, pci mem 0xea402000
Apr 24 08:12:56 localhost kernel: ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
Apr 24 08:12:56 localhost kernel: ehci_hcd 0000:00:10.4: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
Apr 24 08:12:56 localhost usb.agent[8726]:      usb-storage: loaded successfullyApr 24 08:12:56 localhost kernel: scsi0 : SCSI emulation for USB Mass Storage devices
Apr 24 08:12:56 localhost kernel: usbcore: registered new driver usb-storage
Apr 24 08:12:56 localhost kernel: USB Mass Storage support registered.
Apr 24 08:12:56 localhost kernel: hub 5-0:1.0: USB hub found
Apr 24 08:12:56 localhost kernel: hub 5-0:1.0: 8 ports detected
Apr 24 08:12:56 localhost pci.agent[8691]:      ehci-hcd: loaded successfully
Apr 24 08:12:56 localhost pci.agent[8871]:      i2c-viapro: already loaded
Apr 24 08:12:56 localhost usb.agent[8886]:      usbcore: already loaded
Apr 24 08:12:56 localhost pci.agent[8949]:      snd-via82xx: already loaded
Apr 24 08:12:56 localhost pci.agent[8949]:      via82cxxx_audio: blacklisted
Apr 24 08:12:56 localhost pci.agent[8991]:      via-rhine: already loaded
Apr 24 08:12:56 localhost pci.rc[8015]:      ignoring pci display device on 01:00.0
Apr 24 08:12:56 localhost kernel: usb 2-2: USB disconnect, address 2
Apr 24 08:12:57 localhost kernel: usb 2-2: new full speed USB device using uhci_hcd and address 3
Apr 24 08:12:57 localhost kernel: scsi1 : SCSI emulation for USB Mass Storage devices
Apr 24 08:12:57 localhost usb.agent[9092]:      usb-storage: already loaded
Apr 24 08:13:02 localhost kernel:   Vendor: Medion    Model: Flash XL      CF  Rev: 3.0A
Apr 24 08:13:02 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
Apr 24 08:13:02 localhost kernel:   Vendor: Medion    Model: Flash XL      MS  Rev: 3.0A
Apr 24 08:13:02 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
Apr 24 08:13:02 localhost kernel:   Vendor: Medion    Model: Flash XL  MMC/SD  Rev: 3.0A
Apr 24 08:13:02 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
Apr 24 08:13:02 localhost kernel:   Vendor: Medion    Model: Flash XL      SM  Rev: 3.0A
Apr 24 08:13:02 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 00
Apr 24 08:13:02 localhost kernel: Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
Apr 24 08:13:02 localhost kernel: Attached scsi removable disk sdb at scsi1, channel 0, id 0, lun 1
Apr 24 08:13:02 localhost kernel: Attached scsi removable disk sdc at scsi1, channel 0, id 0, lun 2
Apr 24 08:13:02 localhost scsi.agent[9268]:      sd_mod: loaded sucessfully
Apr 24 08:13:02 localhost scsi.agent[9263]:      sd_mod: loaded sucessfully
Apr 24 08:13:02 localhost scsi.agent[9257]:      sd_mod: loaded sucessfully
Apr 24 08:13:02 localhost scsi.agent[9272]:      sd_mod: loaded sucessfully
Apr 24 08:13:02 localhost kernel: Attached scsi removable disk sdd at scsi1, channel 0, id 0, lun 3

---

### Post by rlcoach on 2005-04-24
Next clue.

I boot up and no usb devices work, regardless of whether they were plugged in before or after boot.

However, I did hotplug restart 

sudo /etc/init.d/hotplug restart

and after a short pause everything kicks into life. I guess this would have worked for ACPI so what is causing hotplug not to start properly on boot? Could it be a problem with the inbuilt card readers?

---

### Post by heimo on 2005-04-24
Well, it's hard to know what's causing this. Maybe the hotplug runs too early.

Check at which point it's run with:
ls -l /etc/rc2.d/*hotplug

/etc/rc2.d/S20hotplug -> ../init.d/hotplug
Write down ^^ this number 

Remove hotplug from services to be started.
sudo update-rc.d -f hotplug remove

And make it start at almost end of boot:
sudo update-rc.d hotplug defaults 98

I don't know if this is a good idea. You may have to try other values if some service depends on device that's found only after hotplug is run - but if the situation at the moment is that hotplug doesn't work at all, it could be better run at the end.

---

### Post by rlcoach on 2005-04-24
There is no hotplug stuff in rc2.d?

Thanks for all the help btw, I would have given up well before this if you hadnt have given me so many pointers.

---

### Post by rlcoach on 2005-04-24
Found it

/etc/rc6.d/K89hotplug -> ../init.d/hotplug

Will remove and re-add at end. Fingers crossed.

Here is what happened when I did it, now rebooting.

root@FreeGeoff:/home/andrew # sudo update-rc.d -f hotplug remove
update-rc.d: /etc/init.d/hotplug exists during rc.d purge (continuing)
 Removing any system startup links for /etc/init.d/hotplug ...
   /etc/rc0.d/K89hotplug
   /etc/rc6.d/K89hotplug
   /etc/rcS.d/S40hotplug
root@FreeGeoff:/home/andrew # sudo update-rc.d hotplug defaults 98
 Adding system startup for /etc/init.d/hotplug ...
   /etc/rc0.d/K98hotplug -> ../init.d/hotplug
   /etc/rc1.d/K98hotplug -> ../init.d/hotplug
   /etc/rc6.d/K98hotplug -> ../init.d/hotplug
   /etc/rc2.d/S98hotplug -> ../init.d/hotplug
   /etc/rc3.d/S98hotplug -> ../init.d/hotplug
   /etc/rc4.d/S98hotplug -> ../init.d/hotplug
   /etc/rc5.d/S98hotplug -> ../init.d/hotplug
root@FreeGeoff:/home/andrew #

Does this look okay.

---

### Post by heimo on 2005-04-24
[QUOTE=rlcoach]Found it

/etc/rc6.d/K89hotplug -> ../init.d/hotplug

Will remove and re-add at end. Fingers crossed.[/QUOTE]

Oh - I should have given more information on this. That one is ok - it should stay there. It's used to shutdown hotplug when rebooting. No effect on startup.

If there is no hotplug in rc2.d which is directory for default run level (there are several runlevels), you can just use these:

```

Remove hotplug from services to be started.
sudo update-rc.d -f hotplug remove

And make it start at almost end of boot:
sudo update-rc.d hotplug defaults 98
``` 

Links in rc?.d directories start with either K (=kill) or S (=start) and have number 00-99 which defines the order in which those scripts are run. By default in Ubuntu, during startup, scripts in rc2.d are run. Those starting with S will start services. Those with K are disabled and only used to stop services when switching runlevel.

When you reboot scripts (or actually symbolic links to scripts) in rc6.d will run. Actual scripts are in /etc/init.d/ directory and can be run also manually with /etc/init.d/scriptnamehere start
or *stop,* *restart,* [i]reload

[/i]I didn't have that hotplug in rc2.d either, but if it helps to add it, please let us know. :)

 >  Does this look okay. 
Yes, that looks ok.

---

### Post by rlcoach on 2005-04-24
[QUOTE=heimo]Oh - I should have given more information on this. That one is ok - it should stay there. It's used to shutdown hotplug when rebooting. No effect on startup.

If there is no hotplug in rc2.d which is directory for default run level (there are several runlevels), you can just use these:

```

Remove hotplug from services to be started.
sudo update-rc.d -f hotplug remove

And make it start at almost end of boot:
sudo update-rc.d hotplug defaults 98
``` 

Links in rc?.d directories start with either K (=kill) or S (=start) and have number 00-99 which defines the order in which those scripts are run. By default in Ubuntu, during startup, scripts in rc2.d are run. Those starting with S will start services. Those with K are disabled and only used to stop services when switching runlevel.

When you reboot scripts (or actually symbolic links to scripts) in rc6.d will run. Actual scripts are in /etc/init.d/ directory and can be run also manually with /etc/init.d/scriptnamehere start
or *stop,* *restart,* [i]reload

[/i]I didn't have that hotplug in rc2.d either, but if it helps to add it, please let us know. :)

  
Yes, that looks ok.[/QUOTE]

I am on my Mac, it has all gone a bit pear shaped. I removed and added but apart from not having to wait as long (or at all, didnt notice hotplug on reboot) nothing had changed. USB stuff still wasnt working.

So 

I removed hotplug again and readded, I put old number back in. i.e. 89 instead of 99. Presumed this would be putting it in original place.

Now I get a FAIL on boot up, I cant see what it is as it boots to quickly and I dont know where to go to get message once booted. I can no longer get on the internet with ubuntu, maybe it was the network card that failed.

:(

---

### Post by heimo on 2005-04-24
[QUOTE=rlcoach]
Now I get a FAIL on boot up, I cant see what it is as it boots to quickly and I dont know where to go to get message once booted. I can no longer get on the internet with ubuntu, maybe it was the network card that failed.

:([/QUOTE]

You can use dmesg to get boot messages.  ```
dmesg | less
``` 

Oh. Sorry to hear that broke your network connection. :( But removing those init scripts should make everyhing back to normal. There must be something I missed. 

You can always try to restart networrking: /etc/init.d/networking restart

Fine place to find error messages is /var/log/messages

Network card settings are in /etc/network/interfaces and you can check interface settings with ifconfig (lists all interfaces, including lo - you probably need to check eth0, the first ethernet card).

---

### Post by rlcoach on 2005-04-24
[QUOTE=heimo]You can use dmesg to get boot messages.  ```
dmesg | less
``` 

Oh. Sorry to hear that broke your network connection. :( But removing those init scripts should make everyhing back to normal. There must be something I missed. 

You can always try to restart networrking: /etc/init.d/networking restart

Fine place to find error messages is /var/log/messages

Network card settings are in /etc/network/interfaces and you can check interface settings with ifconfig (lists all interfaces, including lo - you probably need to check eth0, the first ethernet card).[/QUOTE]

Sorry still finding my feet with ubuntu, how do I remove the init scripts and get back to network working.

---

### Post by heimo on 2005-04-24
[QUOTE=rlcoach]Sorry still finding my feet with ubuntu, how do I remove the init scripts and get back to network working.[/QUOTE]

No problem!

This one removes hotplug start/kill scripts:
 ```
sudo update-rc.d -f hotplug remove
``` 

The K in runlevel 6 is useless when you don't have a single S to start the hotplug in first place. That should get you to same situation you were before these changes. If it doesn't those other trics in my post abowe can come useful.

---

### Post by rlcoach on 2005-04-24
I did the remove command again and rebooted. Still no network, I have also tried restarting after reboot and still no joy. Nothing jumped out at me in log/messages. Also dmesg | less didnt have the failure that came up at boot time?

I am now seeing if my window can squeeze open a little more so that I can squeeze my PC out and test it's gravity and impact resistance :(.

---

### Post by heimo on 2005-04-24
[QUOTE=rlcoach]I did the remove command again and rebooted. Still no network, I have also tried restarting after reboot and still no joy. Nothing jumped out at me in log/messages. Also dmesg | less didnt have the failure that came up at boot time?

I am now seeing if my window can squeeze open a little more so that I can squeeze my PC out and test it's gravity and impact resistance :(.[/QUOTE]

I pretty much understand what you're saying. You've had a very bad experience with Ubuntu. I'd like to help you out, if your PC will survive the flight. Output of lspci could help, and /etc/network/interfaces and output of ifconfig. Can you stop the startup messages with Pause|Break button and write down the error message?

Also... If you're still interested.. After all this.. Maybe after couple days on a relaxing OS X, you could try a fresh install. Or at least come back 10/2005 to check the next release (Breezy Badger). Or you could try the older Warty - and possibly upgrade later. Just thoughts.

Thanks!

---

### Post by rlcoach on 2005-04-24
As I have not actually got as far as using ubuntu, I thought it might be better to reinstall. So now I am back to square one (before switching off ACPI).

So I still have 2 problems to try fix.

USB doesnt work on boot - have to restart hotplug
No sound

---

### Post by heimo on 2005-04-24
[QUOTE=rlcoach]
USB doesnt work on boot - have to restart hotplug
[/QUOTE]

That should be easy to fix as you already know what to do. But maybe we won't try to do the update-rc.d stuff this time... I tried to search what makes the hotplug script run, because I think it is run during startup, but there's no link to it in rc2.d. What you may want to try is reconfiguring it using:
[i]sudo dpkg-reconfigure hotplug
[/i]
Output of *lspci *and some information of the motherboard you're using would be welcome. I hope other people reading this thread could also throw some ideas.

[QUOTE=rlcoach]
No sound
[/QUOTE]

Run *alsamixer *and check that no channel is muted (toggle with m) and that the levels are not at zero - specifically master and PCM.

Goto System->Preferences->Multimedia Systems Selector, try different selections for Default sink.

Go to System->Preferences->Sound, see if Enable Sound Server is enabled - it can sometimes help to switch this off and run *killall esd *and try alsa or oss.

Phiu... :) Hopefully this helps.

[http://www.ubuntuguide.org/#configuresoundproperly]("http://www.ubuntuguide.org/#configuresoundproperly")

Is it the Creative external soundcard we're trying to get working? Is it being detected? (/var/log/messages while plugging)

---

### Post by rlcoach on 2005-04-24
root@uGeoff:/home/andrew # lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:06.0 Multimedia controller: Philips Semiconductors SAA7134 (rev 01)
0000:00:09.0 Communication controller: Intel Corp. 536EP Data Fax Modem
0000:00:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [K8T800 South]0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

---

### Post by heimo on 2005-04-24
I have the same integrated audio (I think), and it's working.

My *lsmod | grep snd* lists:

```
snd_via82xx			27520  1 
snd_ac97_codec		 74144  1 snd_via82xx
snd_pcm_oss			52132  0 
snd_mixer_oss		  19680  2 snd_pcm_oss
snd_pcm			    94696  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer			  25060  1 snd_pcm
snd_page_alloc		  9732  2 snd_via82xx,snd_pcm
gameport			    4448  2 analog,snd_via82xx
snd_mpu401_uart		 7680  1 snd_via82xx
snd_rawmidi			24480  1 snd_mpu401_uart
snd_seq_device		  8460  1 snd_rawmidi
snd				    55012  9 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore			  10016  2 snd

``` 

If you're missing some of those - especially snd_via82xx, you could try to modprobe it in to kernel: [i]modprobe snd_via82xx

[/i]Also soundcore and snd are important. Most of should install automagicly via dependencies. Modules that need to be loaded during boot, can be put into /etc/modules file.

---

### Post by rlcoach on 2005-04-24
root@uGeoff:/home/andrew #  lsmod | grep snd
snd_usb_audio          60224  0
snd_usb_lib            11776  1 snd_usb_audio
usbcore               107384  7 usb_storage,ehci_hcd,uhci_hcd,snd_usb_audio,snd_usb_lib,usbhid
snd_via82xx            25248  2
snd_ac97_codec         64608  1 snd_via82xx
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  4 snd_usb_audio,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7168  1 snd_via82xx
snd_rawmidi            22944  2 snd_usb_lib,snd_mpu401_uart
snd_seq_device          8332  1 snd_rawmidi
snd                    50276  10 snd_usb_audio,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_devicesoundcore               9824  4 snd,saa7134
gameport                4608  2 snd_via82xx,analog

---

### Post by rlcoach on 2005-04-24
I have tried all the suggestions regarding fixing the sound and the usb problem to no avail.

I am running out of ideas now and looks like I may have to admit defeat, I have wasted my whole weekend trying to get it all working. It is incredibly frustrating.

Thanks for the help.

 ](*,) :cry:

---

### Post by rlcoach on 2005-04-24
If anybody has any more ideas or can point me to some resources that might help, I would be very gratefull.

---

### Post by rlcoach on 2005-04-25
Bump.

---

### Post by rlcoach on 2005-04-26
[QUOTE=rlcoach]Bump.[/QUOTE]

Persistence finally paid off. 

I flashed my bios and then all my usb devices kicked into life and now Ubuntu boots up fine with my usb keyboard/mouse attached  :) .

All I now need to do is fix the sound (at least that shouldnt be such a tall order with much documentation floating around).

Thanks for everbodies help, especially Heimo.

---

### Post by heimo on 2005-04-26
[QUOTE=rlcoach]Persistence finally paid off. 
I flashed my bios and then all my usb devices kicked into life and now Ubuntu boots up fine with my usb keyboard/mouse attached :) .
[/QUOTE] Great! I'm SO glad to hear this. This thing was a bit stressful, even to me. The feeling of relief, the feeling of getting it finaly sorted out... fixed, it's amazing, isn't it?
 
> Thanks for everbodies help, especially Heimo. 
Thank **you**. You made it. And I will never forget to suspect BIOS bug / incompatibility when something similar will happen.
 
See you around, rlcoach.

---

### Post by rlcoach on 2005-04-26
[QUOTE=heimo]Great! I'm SO glad to hear this. This thing was a bit stressful, even to me. The feeling of relief, the feeling of getting it finaly sorted out... fixed, it's amazing, isn't it?
[/QUOTE]

I was dancing around the house in the end, I had already given up and couldnt believe how frustrating it was. It was then I thought I will just at least rule out the bios so at least I could say Ive exhausted all solutions, it was completely unexpected when it started working.

---

