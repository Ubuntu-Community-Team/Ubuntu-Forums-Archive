---
title: "Cannot boot from USB pen drive"
date: 2017-01-28
forum: Installation &amp; Upgrades
---

### Post by yoramdavid on 2017-01-28
Hi,

I want to install a new operating system (Ubuntu Mate) on an old computer where I already successfully installed Linux Mint a few years ago.
I created a bootable USB pen drive with Ubuntu Mate, but I cannot boot from the pen drive.
I tried a few option on the BIOS, but none worked.

The boot options I have under Advanced are:
[HTML]Floppy
LS120
HDD-0
SCSI
CDROM
HDD-1
HDD-2
HDD-3
ZIP
USB-FDD
USB-ZIP
USB-CDROM
USB-HDD
LAN
Disabled[/HTML]

I tried all the options that have USB in the name. No luck.
It just ignores anything and boots directly on my HDD or gets stuck at a screen where it asks me to press Tab to see post screen.
There are many of threads for the same or similar problem, but none solved. Most are related to UEFI BIOS, this is not the case. It is an old BIOS.

Thanks.
David.

---

### Post by RobGoss on 2017-01-28
Did you try going in to your **BIOS** and rearrange the boot order? you should be able to move your **USB **device to boot first. 
What brand of computer do you have?

---

### Post by ian-weisser on 2017-01-28
You want USB-HDD. Make sure it is tried first. The hardware will boot the first bootable system it discovers.

It can't be the 'same or similar' problem if those are UEFI threads. Wildly different problems can present similar symptoms.
If you know how to fix their UEFI problems, please help them.

---

### Post by oldos2er on 2017-01-28
Threads merged.

---

### Post by yoramdavid on 2017-01-29
First of all, I apologize for the quadruplicate threat. 
I kept getting server busy error, cannot post threat, checked if threat had been posted anyway, it had not, tried again and now this.

---

### Post by yoramdavid on 2017-01-29
> **RobGoss said:**
> Did you try going in to your **BIOS** and rearrange the boot order? you should be able to move your **USB **device to boot first. 
What brand of computer do you have?

There is no rearranging option there, I have 4 entries, First boot option, second, third, fourth, and another one that says "enable boot from other devices".
What I do is select the option I want first and disable all the others. If "enable booting from other devices" is disabled, I get a disk error. If it is enabled, it just boots or gets stuck at this screen first for a long time:
[IMG]https://imagizer.imageshack.us/v2/1000x685q90/923/xx9mta.jpg[/IMG]

Then it gets stuck at this one until I press escape and it goes to the GRUB menu.
[IMG]http://imageshack.com/a/img924/8638/tUOGvT.jpg[/IMG]

Motherboard is ASUS, Graphic card is nvidia, AMD processor.

---

### Post by yoramdavid on 2017-01-29
> **ian-weisser said:**
> You want USB-HDD. Make sure it is tried first. The hardware will boot the first bootable system it discovers.

It can't be the 'same or similar' problem if those are UEFI threads. Wildly different problems can present similar symptoms.
If you know how to fix their UEFI problems, please help them.

I did try with USB-HDD, no luck. Is it possible that the USB pen is not recognized?

---

### Post by sudodus on 2017-01-30
Boot with your USB drive plugged in. Enter your BIOS menus - look at the boot order menu. Maybe your USB drive is recognized as a hard disk drive. If that is the case, please move it to the top of the boot order menu list. See this link for a longer explanation,

[Booting the Computer from USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

-o-

By the way, have you tried if your USB boot drive can boot another computer?

---

### Post by oldfred on 2017-01-30
> Maybe your USB drive is recognized as a hard disk drive. 

This worked for me on my old system. It had many USB boot options like you show. And at first I could not get it to boot. I tested flash drive in my laptop & it booted there, so I know I had it correctly configured. Left it plugged in on desktop and on a reboot found a new hard drive entry. So even if a USB flash drive, it still was seen from BIOS as another hard drive boot entry.

---

### Post by efflandt on 2017-01-31
For some computers, even if you set USB first in BIOS boot order, it will not "automatically" boot from USB (and possibly not from optical drives) unless that was the last thing you booted from. So you might need to press a hot key during boot (typically F12 or F10) to select boot device, but I do not see that mentioned on your BIOS splash screen and do not recognize your BIOS from the hot keys it does show.

I especially notice that with Dell computers. Maybe that is a safety "feature" so you do not accidentally boot a malicious USB or CD/DVD. The only virus I ever caught, which at that time infected Win95, but not Linux on the same drive, was spread by accidentally booting an infected floppy, and the infected Windows would infect any floppy inserted into it.

Of course all bets are off if the image was corrupt or the method it was written to USB does not quite work. For example if you use Startup Disk Creator in Ubuntu 14.04 to put Ubuntu 16.04 or 16.10 on USB, it will not BIOS boot without doing something special to it because syslinux in 14.04 is an older version than in the newer Ubuntu versions. Do you have access to another computer using BIOS that you could try booting the USB from?

---

### Post by yoramdavid on 2017-01-31
> **sudodus said:**
> Boot with your USB drive plugged in. Enter your BIOS menus - look at the boot order menu. Maybe your USB drive is recognized as a hard disk drive. If that is the case, please move it to the top of the boot order menu list. See this link for a longer explanation,

[Booting the Computer from USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

-o-

By the way, have you tried if your USB boot drive can boot another computer?

I just tried the 4 entries for HDD none worked, I get the disk failure error.
I was expecting that at least one of the HDD would boot into the system? Grub?
I had disabled "Boot from other devices", had to re-enable it to boot the system.

I have not tried to boot another computer, I can try on the laptop, but I think it is a UEFI BIOS, I have to look into that to see how to do it.

---

### Post by yoramdavid on 2017-02-01
Just tried to boot from teh USB pen with my laptop without success. I re-wrote the image to the pen using the laptop this time, same: no luck.
I flashed another pen drive and tried with this one, no luck either.

With the laptop, a recent one (less than a year old, I think), if I press escape key, I go to the boot menu, there is no entry there, just the hdd. If I go to the BIOS, there is no flash drive there either, just the hdd.
I do not know if I have uefi getting on the way.
I have Ubuntu only on the laptop, no windows. Fast boot is disable on the bios as well as secure boot.
The laptop is 64bit, the image of the pen drive is 32 bit, but it should still at least give me a warning and boot from it right?

---

### Post by oldfred on 2017-02-01
The 32 bit Ubuntu installer is not UEFI, only the 64 bit installer. (Same as Windows must be 64 bit).

       Ubuntu UEFI install ISO
Also links on how to create a bootable DVD or USB flash drive, from Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Easy way to create UEFI only bootable flash drive
[URL="http://ubuntuforums.org/showthread.php?t=2299040"]http://ubuntuforums.org/showthread.php?t=2299040
[/URL]
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html) 
      
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
    [URL="http://ubuntuforums.org/showthread.php?t=2299040"]
[/URL]

---

### Post by yoramdavid on 2017-02-01
The old computer where I want to install the new version of linux is 32bit.
And it is not UEFI.

---

### Post by sudodus on 2017-02-02
Let us start from the beginning and check what might cause your problems.

1. Did you check with md5sum, the the iso file was downloaded correctly? See this link, [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

2. Which tool did you use to install from the iso file to the USB pendrive? See this link, [Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by yoramdavid on 2017-02-03
> **sudodus said:**
> Let us start from the beginning and check what might cause your problems.

1. Did you check with md5sum, the the iso file was downloaded correctly? See this link, [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

2. Which tool did you use to install from the iso file to the USB pendrive? See this link, [Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Hi,

1. No I had not but did now and yes, it is ok.

2. I used usb-creator-gtk version 0.3.2

Thank you.

---

### Post by yoramdavid on 2017-02-03
I also compared the list of option on the BIOS without and with the pen and they are the same, none is added when the pen is plugged in.

---

### Post by sudodus on 2017-02-03
I saw the years 1997-2004 in your photo of the BIOS. Many computers made 2004 will boot from USB, but not all of them. Maybe you can use ***Plop*** to boot from the CD drive or floppy drive and chainload to the USB drive.

[Installation/FromUSBStick#PLoP_Boot_Manager](https://help.ubuntu.com/community/Installation/FromUSBStick#PLoP_Boot_Manager)

---

### Post by yoramdavid on 2017-02-03
I could burn a DVD and install it. I have still some at hand.

---

### Post by C.S.Cameron on 2017-02-03
It should be possible to add the USB drive to your computers grub menu, try sudo update-grub with the USB plugged in.

---

### Post by sudodus on 2017-02-04
If you have a DVD (read and write) drive, you can also create a DVD boot disk with Ubuntu MATE directly. (But the iso file is too big for the old CD disk format.)

-o-

Chainloading according to C.S.Cameron's advice is also a good alternative, if Linux Mint is still running it it.

---

### Post by yoramdavid on 2017-02-04
> **C.S.Cameron said:**
> It should be possible to add the USB drive to your computers grub menu, try sudo update-grub with the USB plugged in.

Thank you. It did nothing new.

---

### Post by kurt18947 on 2017-02-04
> **yoramdavid said:**
> I could burn a DVD and install it. I have still some at hand.

I don't recall a failure to boot from DVD on any machine I've tried. The boot process may take what seems like forever, but it has worked. Well, except for a pre-2000 system with Intel video. That required a non-Ubuntu system.

---

### Post by yoramdavid on 2017-02-04
> **sudodus said:**
> I saw the years 1997-2004 in your photo of the BIOS. Many computers made 2004 will boot from USB, but not all of them. Maybe you can use ***Plop*** to boot from the CD drive or floppy drive and chainload to the USB drive.

[Installation/FromUSBStick#PLoP_Boot_Manager](https://help.ubuntu.com/community/Installation/FromUSBStick#PLoP_Boot_Manager)

I tried to put in on a floppy disk, but it copies up to 1.37 MB and the file for floppy is 1.40MB.

---

### Post by sudodus on 2017-02-05
Did you try to boot from it? That could be the difference between MB (10-base) and MiB (2-base),

```
2^20*1.37/10^6=1.436
```

---

### Post by oldfred on 2017-02-05
This user just used CD to boot with plop.

[https://ubuntuforums.org/showthread.php?t=2351470&p=13603216#post13603216](https://ubuntuforums.org/showthread.php?t=2351470&p=13603216#post13603216)

---

### Post by yoramdavid on 2017-02-05
> **sudodus said:**
> Did you try to boot from it? That could be the difference between MB (10-base) and MiB (2-base),

```
2^20*1.37/10^6=1.436
```

Boot from the floppy? There is nothing in it, I could not copy the file as it is too big.

---

### Post by yoramdavid on 2017-02-05
> **sudodus said:**
> I saw the years 1997-2004 in your photo of the BIOS. Many computers made 2004 will boot from USB, but not all of them. Maybe you can use ***Plop*** to boot from the CD drive or floppy drive and chainload to the USB drive.

[Installation/FromUSBStick#PLoP_Boot_Manager](https://help.ubuntu.com/community/Installation/FromUSBStick#PLoP_Boot_Manager)

The year on this screen is different (1984-2002) and it states the BIOS model or make:

[IMG]http://imageshack.com/a/img923/9848/CUbQ4o.jpg[/IMG]

---

### Post by oldfred on 2017-02-05
Did you follow the procedure on the link with the use of a CD.
Plop is a small file, not the newer bootmanager.
> tiny file of only 544 KiB from February 2015

---

### Post by yoramdavid on 2017-02-05
> **oldfred said:**
> Did you follow the procedure on the link with the use of a CD.
Plop is a small file, not the newer bootmanager.

The one I found for floppy had 1,4 Mb.
OK, this one is ok now, I successfully installed the file in the floppy and booted to the usb pen!
I will now install linux and see how it goes. I am concerned about my old nvidia graphic card not being recognized.

---

### Post by yoramdavid on 2017-02-06
Solution:

The computer being too old to boot directly from a USB pen, the solution was using the plop boot manager from a floppy disk, from which I was then able to boot from the USB pen and install the system.

PS:

I had successfully installed Linux Mint Mate 18.
But did not get a desktop.
It is strange because from the USB, the screen was fine, resolution was fine. When the installation was finished it asked to reboot and so I did and all was fine again on this first reboot.
But when rebooted again, I got a screen that flickers a few times, then it was black and an error message appeared saying there was a problem. Same with subsequent reboots.
No proprietary drivers were in use.
Firefox and Thunderbird did not work.

So, I installed the recently released Ubuntu Mint Mate 18.1 and so far (after 3 reboots) it is fine regarding the screen.
Firefox and Thunderbird still do not want to lauch.

But I guess I should open a new threat about that problem now?

And perhaps I should mark this one as solved with a work around?

Thank you all for your help.

---

### Post by sudodus on 2017-02-06
Thanks for sharing your solution :-)

And yes, please mark this thread as solved and start a new thread about the current problems.

---

