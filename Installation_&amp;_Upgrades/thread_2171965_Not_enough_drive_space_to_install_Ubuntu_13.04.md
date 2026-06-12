---
title: "Not enough drive space to install Ubuntu 13.04"
date: 2013-09-02
forum: Installation &amp; Upgrades
---

### Post by Myles_Vance on 2013-09-02
Hello, I'm new to this forum. I'm trying to install Ubuntu 13.04 on a HP desktop computer (model p6230y). It is only a couple years old and it has Windows 7 on it now, which doesn't work right (a blue screen error after having the computer on for a few minutes, the blue screen errors only appear for a second so I don't have time to read it before the computer restarts). I am trying to install Ubuntu from a USB stick to completely replace Windows. I can try Ubuntu from the USB stick but I cannot install it because there is an X next to "Has at least 5.3 GB available drive space" which is strange because this computer should have plenty of space on the drive (it has a 750 GB hard drive, not sure exactly how much is available, though). Am I doing something wrong? Or is something wrong with the hard drive? Or is there something else that could cause this? I checked the computer files in safe mode yesterday and it has no pictures or documents. Thanks in advanced for any help anyone can provide!

---

### Post by mörgæs on 2013-09-02
Hi, welcome to the fora.

If you are new to Buntu I think the easiest approach is to run the drive over with Killdisk first. It will also clean the master boot record.

You just create a bootable Killdisk USB stick like the one you made with Buntu.

---

### Post by Myles_Vance on 2013-09-02
Okay, I have run Killdisk and I have read in the user guide that I will have to repartition and reformat the HDD. How exactly do I do this?

Edit: Actually... I think I am doing something wrong. I think that whatever I am doing wrong is also the reason I am unable to install Ubuntu on the computer. I think I just ran Killdisk on the USB drive that I set up as a bootable drive. And I think that I was trying to install Ubuntu on the USB drive. When I start the computer and press F12 it only shows Windows as the bootable operating system, as if it doesn't even notice the USB drive. Then when the computer boots in to Windows and then Windows runs into and error and says it has to restart it boots the USB drive. I am confused, I must be doing something wrong.

---

### Post by mörgæs on 2013-09-02
It's done automagically during the Buntu setup afterwards.

---

### Post by Myles_Vance on 2013-09-02
[COLOR=#000000]I edited my above post after you replied- [/COLOR][COLOR=#000000]Actually... I think I am doing something wrong. I think that whatever I am doing wrong is also the reason I am unable to install Ubuntu on the computer. I think I just ran Killdisk on the USB drive that I set up as a bootable drive. And I think that I was trying to install Ubuntu on the USB drive. When I start the computer and press F12 it only shows Windows as the bootable operating system, as if it doesn't even notice the USB drive. Then when the computer boots in to Windows and then Windows runs into and error and says it has to restart it boots the USB drive. I am confused, I must be doing something wrong.
[/COLOR]

---

### Post by Bucky Ball on 2013-09-02
Welcome to the forums. 

Make the USB again, change the boot device in the BIOS to boot from USB, choose 'Try Ubuntu' when you get to the options and that should get you to a desktop, launch Gparted (Partition Manager) and delete all partitions. Click the 'Install' icon on the desktop and proceed.

Good idea to make a plan of how you want the drive to eventually look *prior* to commencing the install. As you are starting with a blank disk, though, you do have some leeway for altering 'on the fly', but you can also back yourself into a corner which is difficult to get out of if you realise in a month you should have done things differently. A basic partition setup might be:

/ = your OS, 20Gb fine;
/home = your personal stuff, as large as you can/want/need;
/swap = 2Gb generally plenty unless you hibernate a lot.

A rough guide. All of this can live inside an extended partition, incidentally: you don't need to use primaries. You can partition manually when you get to that section of the install by choosing 'Something Else' or, as suggested by Morgaes, let Ubuntu partition 'automagically' (remembering that this might set the partitions up nowhere close to what you actually want).

Good luck. ;)

---

### Post by Myles_Vance on 2013-09-02
Yeah, I definitely ran Killdisk on the USB drive from the computer I meant to run Killdisk on... I think I am trying to install Ubuntu on the USB drive (a 4 GB drive, explains why there wasn't enough space on it) but I want to install it on the computer. How can I fix this?

---

### Post by Bashing-om on 2013-09-02
Myles_Vance; Hi !

+1 ^ ....
IF your bios (some Windows' 7 are) is not UEFI enabled nor raid employed at any past time, then we expect that all that is required is boot the installUSB and choose to install ubuntu "use the entire drive" option -> a few simple questions to respond to - IMPORTANT; remember your password - and done .. do not make it more complex that it is ..installing should be quick and easy. Else these is a problem .. and we will guide you through to resolution.

[INDENT][INDENT]love'n ubuntu
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2013-09-02
> **Myles_Vance said:**
>  ... I want to install it on the computer. How can I fix this?

Like bashing-om said or follow the (lengthy) explanation I posted directly above your last post. Or a pinch of both.

---

### Post by Myles_Vance on 2013-09-02
I don't see a "use the entire drive" option. It won't let me go past the page that tells me I am connected to the internet and that I need more space on my drive. But it isn't trying to install it on the computer, it is trying to install on the USB drive which is my real problem I guess. I am using [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) to make my USB drive a bootable drive.

---

### Post by Myles_Vance on 2013-09-02
[ATTACH=CONFIG]245931[/ATTACH]  Here's what appears when I hit F12 while the computer boots up. I do have the USB drive in it. Ubuntu only boots up after Windows boots then restarts, however instead of restarting it boots Ubuntu (or when I tried to run Killdisk it booted that).

---

### Post by Myles_Vance on 2013-09-02
I got the computer to boot into windows and not ru into a blue screen error. The computer's HDD has 646 GB free of 686 GB. The computer doesn't seem to recognize the USB drive as being bootable until Windows runs into an error. But then Ubuntu seems to think the USB drive is the HDD.

---

### Post by varunendra on 2013-09-03
Possibly, this is what is happening -

[LIST]
[*]The USB doesn't get enough time to get ready before the BIOS stops probing USB devices and proceeds to boot from HDD.
[*]By the time windows starts loading, the USB becomes ready. Some problem causes the system to reboot and it loses HDD (until next boot, not uncommon).
[*]Since the USB is ready now (because it's a 'Hot reboot'), it gets detected this time, while the HDD has disappeared.
[*]Since the HDD has been disappeared, Ubuntu installer sees the USB as the only option left for installation.
[/LIST]

A slightly different explanation would be that you are not hitting the right key (or at right time) to bring up the BIOS boot-device selection menu. Thus it defaults to boot from the HDD. This replaces the explanation above why it initially doesn't boot from USB.

[INDENT]* Are you sure F12 is the correct hotkey to show boot devices at startup?

* Do you start tapping it as soon as the computer powers up (and keep tapping until you get the boot prompt)?

* When you are able to boot from USB, don't begin the installation. Choose "Try..." option. Do you see the hard disk in the live session?[/INDENT]

The screenshot you posted is Windows's own boot menu, not the computer's boot-device selection menu, which means the USB was already skipped.

Either the BIOS is not giving enough time to the USB to get ready (skips to HDD before USB gets ready) or you are not doing it right. If you can go into computer's system setup (BIOS settings), see if the USB device appears in it somewhere in the Boot devices. Set it to first boot device > save settings > reboot.

The fact that you are getting a blue screen error on windows (possibly BSOD - Blue Screen Of Death) also indicates a possibility of a loose hard disk connection problem. Although a driver issue may also cause it to disappear until next boot, thus the Ubuntu installer seeing the USB as the only drive left when it boots.

---

