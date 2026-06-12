---
title: "Installing Ubuntu 9.10 on an External Hard drive"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by Bigbob22 on 2009-11-22
I'm going to be getting an external hard drive soon, and I was wondering if I could partition the hard drive and install Ubuntu 9.10 to one of the partitions on the hard drive. I am currently using Windows XP. If this is possible how would you do it? Would I be able to use the other partition to for other needs?

---

### Post by Claus7 on 2009-11-22
Hello,

it depends on what you want to do and what are your needs.

Now from what I get:
you have already a hdd (let's call it hda) and you will have an external one (let's call it hdb).

Now in hda you have windows xp. What you would like to do with hdb?

You could plug it and insert an ubuntu iso cd. Then you could select that drive and install ubuntu. Also there, you will be able to install grub and while booting to choose whether you will boot from hda and windows of hdb and ubuntu. 

How are you planning to plug this external hdd to your computer?

Regards!

---

### Post by Bigbob22 on 2009-11-22
I was going use the partition on the external hard drive without Ubuntu to back up and store data. I was going to use Ubuntu for just surfing the web, watching videos, making documents, and etc. I was just planning to plug in the external hard drive through the USB port. I might be getting a portable hard drive instead of an external hard drive.

---

### Post by Claus7 on 2009-11-23
Hello,

since you need an ntfs partition for back up purposes, I would advice you to make the whole usb external hdd an ubuntu one.

That is because now, it is possible to transfer data from windows to ubuntu via:
[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

In order to proceed with the installation I would advice you to check this link:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Regards!

---

### Post by Bartender on 2009-11-23
BigBob -
There's a big decision that you must make.

If you're going to run the PC with the external plugged in ALL THE TIME, you can just install Ubuntu and let GRUB install part of itself to the MBR of the Windows drive.

If you're NOT going to have the external hooked up all the time (I'm guessing not) then you must make sure to install all of Ubuntu's bootloader to that external drive.  

You would then boot from the external by choosing it when the computer is first starting up, or by changing BIOS settings so that if the PC sees a USB device plugged in it'll boot from that device first.

---

### Post by Bigbob22 on 2009-11-23
Could I use that option on the live cd to install it to a usb? I'm a linux noob so I'm still a little confused on how to install it. I wanted it to be so I could just plug in the external HDD when ever I wanted to (not always in). If I were to run the PC with the external plugged in ALL THE TIME what would happen if I unplugged it?

---

### Post by Bigbob22 on 2009-11-23
> **Claus7 said:**
> Hello,

since you need an ntfs partition for back up purposes, I would advice you to make the whole usb external hdd an ubuntu one.

That is because now, it is possible to transfer data from windows to ubuntu via:
[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

In order to proceed with the installation I would advice you to check this link:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Regards!


What is the fs-driver thing? How does it work?

---

### Post by Claus7 on 2009-11-24
Hello,

I do not know a way where you will plug a machine to your pc and it will boot automatically from that machine. 

I still advice you not to use such a machine (a usb external hdd) with ubuntu on, because these are not supposed to be plugged on a pc all the time. 

You can follow *Bartender*'s advice and install ubuntu in this drive. In the end of the installation process you will have an option, where you want to install grub. So you have to choose in which place you like it to be installed.

About the fs-driver thing you can check it out easily yourself. It is an exe file, which you execute on windows and it allows you to "see" disks based on the ext2, ext3 file system. I do not know what is going on with ext4 though...

Regards!

---

### Post by Bartender on 2009-11-24
Bob -
this all seems confusing but it's not.  
I have a pretty good general understanding of the "old" GRUB, but not the new GRUB2.  So I'm a little nervous about telling you something that is not true anymore.

Having said that, I believe that the basic principle is still the same.  I believe that during installation GRUB2 still looks for a Windows operating system on the "first" drive or first partition.  If it finds one, it will by default modify the Windows Master Boot Record (MBR) which is a tiny scrap of data installed to the leading edge of that HDD that tells the computer where to look on the hard drive to find an operating system.

Let me see if I can explain this differently.  When you first push the "on" button, it's important to understand that your PC is dumber than a bag of hammers.  

So your PC goes to the BIOS, which is stored on a motherboard chip.  BIOS gives it some basic information, such as how many drives are installed, etc. and **BIOS tells it which drive it should try to boot from first.**

That's an important statement.

So the PC goes wherever the BIOS sends it, and tries that first device.  If the PC does not find an operating system, it goes to the next bootable device listed in BIOS.  If it finds nothing there, it goes to the next one, until it gets to the end of the list.

If the PC finds a bootable device, such as a hard drive, CD, operating system on a USB drive, a network that feeds it everything it needs, etc. it will attempt to boot from that device.

For the typical Windows user, BIOS is usually set up to boot from the HDD first, or the optical drive then the HDD.  The first place it goes on the HDD is the MBR, which then tells the PC where to find Windows.

So it's Power On>BIOS>try the bootable devices>find Windows MBR>find Windows and start it up.

That may be overly simplified, or maybe even not technically accurate, but perhaps that puts a picture in your mind.

OK, back to GRUB - with a "typical" dual-boot installation, GRUB will find the Windows MBR and add a little bit of code.  This code is a detour sign.  It tells the PC to go to the second part of GRUB, **which is installed in the Linux partition**.  This second part of GRUB is what you see on the screen when it asks which OS you want to boot.

In your situation, let's say you install Ubuntu to the external hard drive.  You allow GRUB to install in the default method, where it places that scrap of code in the Windows MBR.  You're done, and you reboot.  The PC starts up, it gets to the Windows MBR, it sees the detour sign and goes to the second part of GRUB.  You choose your operating system (Windows or Linux, doesn't matter) and the PC goes either back to the Windows HDD or continues into the Linux installation on the external.

Now, what happens if next day you unplug the external and you start the computer.  It gets to the Windows MBR, where the first part of GRUB is waiting to direct the PC on to the second part of GRUB.  Where's the second part of GRUB?  IT'S ON THAT EXTERNAL HARD DRIVE THAT YOU UNPLUGGED.  The PC can't find the second part of GRUB, and you're done.

That's why you need to do something different.  I am not sure how many different options there are.  Maybe herman's website can help.  Does your PC have a "quick-boot" option in the BIOS where you can tap a key as the PC is starting up and choose which device to boot from?  Most PC's do.

I know the following works, but as I said there may be other options, such as some sort of smart bootloader program for Windows or etc.

Some PC's (mostly older ones) don't have a "boot to USB" option so you need to make sure you do.

In your case, if you're not sure on how to tell GRUB where to install, I'd unplug the internal HDD, plug in the external,  boot from the Ubuntu CD, make sure that the external was the only HDD that Ubuntu saw, and install the ENTIRE Ubuntu OS to the external HDD.  Then I'd restart the PC and make sure that it booted to Ubuntu.

Then I'd shut down, plug the internal back in, and restart.  Windows will start up if the internal is first in BIOS boot order.  Ubuntu will start up if you've reset the BIOS boot order to put USB before internal.  

There are two BIOS options that I know of.  
One, change BIOS boot device order so that USB is before the internal HDD.  That way the PC will boot to Ubuntu whenever the external is plugged in (and turned on!) If the USB external isn't there, the PC will continue on to the internal drive.
Two, leave BIOS boot order the way it is (in all likelihood the internal HDD is first or second) and be ready to hit the key that gives you the "quick-boot" menu where you pick which device to boot from.

---

### Post by Bigbob22 on 2009-11-25
Thanks for all the help!

---

### Post by CuriousSoul on 2009-12-10
Hi there folks,
I have a similar if not exact problem. I have 120 GB internal Hard disk, and another 500 GB external one.I have already XP installed on the internal one, i wanna know how should i install Ubuntu 9.10 on the external one? 

Till now i have proceeded this way:

**1**.changed the settings of BIOS to boot first from CD, then from USB HDD(so that if my USB HDD is plugged in it will automatically go to Ubuntu) and then from my internal HDD

**2**.restarted the computer, booted from Ubuntu 9.10 CD,but i dont know why after having selected my language and selected the install option it just goes to Ubuntu's wallpaper and stays that way.when i press ESC it gives me a list of errors!

Thanks everyone in advance for the help

---

### Post by darkod on 2009-12-10
> **CuriousSoul said:**
> Hi there folks,
I have a similar if not exact problem. I have 120 GB internal Hard disk, and another 500 GB external one.I have already XP installed on the internal one, i wanna know how should i install Ubuntu 9.10 on the external one? 

Till now i have proceeded this way:

**1**.changed the settings of BIOS to boot first from CD, then from USB HDD(so that if my USB HDD is plugged in it will automatically go to Ubuntu) and then from my internal HDD

**2**.restarted the computer, booted from Ubuntu 9.10 CD,but i dont know why after having selected my language and selected the install option it just goes to Ubuntu's wallpaper and stays that way.when i press ESC it gives me a list of errors!

Thanks everyone in advance for the help

Just to clarify, this is happening when you select Install Ubuntu in the cd menu, or you are loading ubuntu with Try Ubuntu and then clicking the install icon on desktop?
Try using the Install Ubuntu option from the cd menu if you haven't. No need to load ubuntu as live environment.

If the install process starts, in step 4 notice how is the ext hdd called (for example /dev/sdb) and in the last step 7, before clicking Install, click on Advanced and check if the bootloader (grub2) is going to be installed to the same /dev/sdb.

---

### Post by echotone on 2009-12-10
I also have a similar problem. I cannot run the live environment or choose the install option. i get a black screen. so I plug an internal drive into a usb adapter as a psudo-external drive. How can i just install ubuntu on it without having to go through the hassle of booting into the live cd --because i cant on that drive. I tried to plug it into my laptop and copy my home folder but i have no permission to do that. is there something similar i can do?

---

### Post by CuriousSoul on 2009-12-10
> **darkod said:**
> Just to clarify, this is happening when you select Install Ubuntu in the cd menu, or you are loading ubuntu with Try Ubuntu and then clicking the install icon on desktop?
Try using the Install Ubuntu option from the cd menu if you haven't. No need to load ubuntu as live environment.

If the install process starts, in step 4 notice how is the ext hdd called (for example /dev/sdb) and in the last step 7, before clicking Install, click on Advanced and check if the bootloader (grub2) is going to be installed to the same /dev/sdb.

Yes when i select "Install Ubuntu" not "Try Ubuntu".

I didnt get what step 4?

Thanks for the response

---

### Post by darkod on 2009-12-10
It might a bad cd. Maybe the ISO image got corrupted during download, or during burning. If the cd was burnt at high speed that's also an option. Remember that even with todays cds being burnt at 50+x, you should never burn installation cd at more than 8x. Sometimes using cd-rw makes it not working too.
It sounds like problem with the cd if even the install option doesn't wanna start.
Another option is to create bootable usb stick instead of cd and try with that. Most newer computers support boot from usb.

---

### Post by darkod on 2009-12-10
> **CuriousSoul said:**
> 
I didnt get what step 4?

Thanks for the response

Step 4 of the install process but since it doesn't even start, obviously you're not getting to step 4 at all.

---

### Post by echotone on 2009-12-10
My computer wont boot from a usb. but i made an alternate installer disk instead and it seems to be working.

---

### Post by darkod on 2009-12-10
> **echotone said:**
> My computer wont boot from a usb. but i made an alternate installer disk instead and it seems to be working.

The alternate install cd is one of the options if desktop cd doesn't work for any reason.

---

### Post by CuriousSoul on 2009-12-10
> **darkod said:**
> It might a bad cd. Maybe the ISO image got corrupted during download, or during burning. If the cd was burnt at high speed that's also an option. Remember that even with todays cds being burnt at 50+x, you should never burn installation cd at more than 8x. Sometimes using cd-rw makes it not working too.
It sounds like problem with the cd if even the install option doesn't wanna start.
Another option is to create bootable usb stick instead of cd and try with that. Most newer computers support boot from usb.


I  burnt the .iso image at 10X(the lowest possible on InfraRecorder), but the it would just hang after i select install or even try ubuntu in the installation menu.I used CD-R

using the other cd which gives me errors(both in install and try modes) it gave me these errors after i pressed ESC when the ubuntu wallpaper will emerge but not move ahead:

chroot: cannot execute debconfig-comunicate:Inupt/Output error
chroot: cannot execute /user/lib/user-setup/user-setup-apply:input/output error
grep:/root/user/share/i18n/SUPPORT: input/output error


To give you additional information, i had installed ubuntu and GRUB sometimes ago on my internal HDD, but then removed Ubuntu by removing its partition, and GRUB disapeared and i didnt get the chance to repair my MBR. do u think that problem might have come to haunt me now?

---

### Post by CuriousSoul on 2009-12-10
> **darkod said:**
> 
Another option is to create bootable usb stick instead of cd and try with that. Most newer computers support boot from usb.

I dont understand how its gonna work, i mean using the CD option i set BIOS into CD>USB HDD>Internal HDD

How should i set the options in BIOS to be able to boot from the stick? I have HP dv6137, with HP F.29 13/11/2007 BIOS

---

### Post by darkod on 2009-12-10
> **CuriousSoul said:**
> I  burnt the .iso image at 10X(the lowest possible on InfraRecorder), but the it would just hang after i select install or even try ubuntu in the installation menu.I used CD-R

using the other cd which gives me errors(both in install and try modes) it gave me these errors after i pressed ESC when the ubuntu wallpaper will emerge but not move ahead:

chroot: cannot execute debconfig-comunicate:Inupt/Output error
chroot: cannot execute /user/lib/user-setup/user-setup-apply:input/output error
grep:/root/user/share/i18n/SUPPORT: input/output error


To give you additional information, i had installed ubuntu and GRUB sometimes ago on my internal HDD, but then removed Ubuntu by removing its partition, and GRUB disapeared and i didnt get the chance to repair my MBR. do u think that problem might have come to haunt me now?

No, the cd not starting the install process has nothing to do with your hdd. You could even have blank hdd in a newly built computer, how would you install then?
But I have no clue what might be wrong if you're sure the cd and the cd drive are fine. If you have some usb stick around I would give it a shot.

---

### Post by ers11121 on 2009-12-11
Good Morning,
Let me see if I understand this because I am going to try this over the weekend. I have a 120gb external hdd, (2 60gb partitions). If I install Ubuntu 9.10 on one of those partitions, with the Grub installed on that same partition, set the bios to boot cd-dvd ./ external usb / internal hdd it should boot the Ubuntu install as long as the external drive is plugged in or straight to windows if it is unplugged, correct?
As an added question, (if I'm not pushing my luck) could I install a second distro (Ultimate Edition 2.5) on the other partition and dual boot them?
Ed

---

### Post by darkod on 2009-12-11
> **ers11121 said:**
> Good Morning,
Let me see if I understand this because I am going to try this over the weekend. I have a 120gb external hdd, (2 60gb partitions). If I install Ubuntu 9.10 on one of those partitions, with the Grub installed on that same partition, set the bios to boot cd-dvd ./ external usb / internal hdd it should boot the Ubuntu install as long as the external drive is plugged in or straight to windows if it is unplugged, correct?
As an added question, (if I'm not pushing my luck) could I install a second distro (Ultimate Edition 2.5) on the other partition and dual boot them?
Ed

Yes and Yes. Just small clarification, put grub2 on the MBR of the ext hdd, not the ubuntu partition itself. During the install process, in step 4 check the name of the ext hdd (for example if you have one internal it would probably be /dev/sda, the external /dev/sdb). Then in step 7, before you click Install button, click on Advanced and it will show you the advanced options. Make sure grub2 is installed to /dev/sdb (or what ever your ext disk will be called) to make sure it doesn't go to the internal drive.
And that should be it. When it's plugged it should find it, when unplugged your int hdd is next in line.

---

### Post by ers11121 on 2009-12-11
Darko, 
Thanks for the reply, I thought that it should work like that. I have seen too many threads stating that when you unplug the external drive nothing will boot, that didn't make sense to me. The computer should boot to whatever is first & available. I think to be on the safe side the internal hdd will be unplugged so no "accidents" happen.
Ed

---

