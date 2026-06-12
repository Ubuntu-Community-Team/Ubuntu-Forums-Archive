---
title: "Please, Help Me Get Rid of Windows 8"
date: 2012-11-16
forum: Installation &amp; Upgrades
---

### Post by smiley07 on 2012-11-16
Recently, I bought a HP 2000 Notebook PC and it came with Windows 8 pre-installed on it. And I want to get rid of Windows, but for the life of me, I can't get this laptop to work with me. 
 
I downloaded Ubuntu 12.10 (64 bit) and burned it to a dvd. I changed the boot order, so that basically everything except for the OS is suppose to boot first, but this laptop still won't boot the dvd. The laptop sounds like it's running the dvd, but then goes to the Windows 8 screen. How do I get my laptop to boot the dvd, so I can install Ubuntu and more importantly get rid of Windows?

---

### Post by mörgæs on 2012-11-16
Does it boot from USB?

---

### Post by NikTh on 2012-11-16
Hi , 
yes Bootable USB are more accurate . You can create one with Ubuntu iso & [unetbootin](http://unetbootin.sourceforge.net/) 
OR
try [to md5sum the iso image](https://help.ubuntu.com/community/HowToMD5SUM) and re-create the CD , burn it to the lower speed. 
Thanks

---

### Post by smiley07 on 2012-11-16
Right, so, I downloaded Puppy Linux to my usb to try and see if that would work. I restarted my laptop and the usb flashed like it was running, but then once again the laptop went to Windows. 
 
I feel like I should be pushing a button to load the usb or disc, but the screen doesn't say anything like that. I remember on my old computer (how I miss you!) when you had a usb or cd you wanted to boot, it would say something like "Push enter to load disc." Is there some button I could push to "force" this laptop to boot the usb or dvd?
 
Oh, and I can't naturally get into BIOS because I don't know what fn button to push. I have to do a workaround, where I "crash" my laptop on purpose to get it to give me the option to open BIOS. Frustrated? Check!

---

### Post by darkod on 2012-11-16
Once you get into bios, look around for options like Show Logo or similar. If you disable that, it should show more background information instead of an image while it's booting.

So you can better see which Fn key is got what.

Also, try to find some option like Fast Boot if it exists, and disable it too while you are troubleshooting the cd boot. You don't need the express boot right now, you need it to show you more info on the screen.

If the board/bios is UEFI, you might need to boot from the UEFI dvd-rom, not the legacy device (they are shown as separate on UEFI bios).

Did you try if the ubuntu dvd boots on another machine?

---

### Post by ALinuxWindowsBalance on 2012-11-16
I know what this is. It's that stupid 'secure boot' thing that all new PCs have. Ubuntu needs a cert to boot, and I bet it doesn't have one yet.

I remember when all you needed was a MS-DOS startup file and a floppy.

---

### Post by kurt18947 on 2012-11-16
> **ALinuxWindowsBalance said:**
> I know what this is. It's that stupid 'secure boot' thing that all new PCs have. Ubuntu needs a cert to boot, and I bet it doesn't have one yet.

I remember when all you needed was a MS-DOS startup file and a floppy.

I agree with having to change the boot order in BIOS.  I recall reading somewhere - i don't remember where so don't know how credible - that Ubuntu 12.10 would work with secure boot.  Microsoft will 'permit' manufacturers to disable secure boot on X86 devices but not on ARM devices.  It'll be interesting to see which manufacturers include a disable option for secure boot.  Someone (EFF?) has a Linux workaround for secure boot as well.

---

### Post by whatthefunk on 2012-11-16
More than lekely F10 to get to BIOS.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

### Post by smiley07 on 2012-11-16
Alright, so, I disabled secure boot and enabled legacy boot, and finally got my dvd to boot. Unfortunately, as I was installing Ubuntu, an error occurred (I should've wrote it down, but it had something to do with the LVM/LMV??) destroying everything. And spent the rest of the day just reinstalling Windows. 
 
But on the plus side I did find out how to get to BIOS without intentionally crashing it thanks to whatthefunk. It's the esc key, which has to be pushed really quickly because if the HP logo shows up, you're already too late. I'll try again tomorrow.
 
Thanks everyone for the help so far.

---

### Post by kurt18947 on 2012-11-16
> **smiley07 said:**
> Alright, so, I disabled secure boot and enabled legacy boot, and finally got my dvd to boot. Unfortunately, as I was installing Ubuntu, an error occurred (I should've wrote it down, but it had something to do with the LVM/LMV??) destroying everything. And spent the rest of the day just reinstalling Windows. 
 
But on the plus side I did find out how to get to BIOS without intentionally crashing it thanks to whatthefunk. It's the esc key, which has to be pushed really quickly because if the HP logo shows up, you're already too late. I'll try again tomorrow.
 
Thanks everyone for the help so far.

HP gives you a way to disable secure boot.  Kudos to them!  With some new systems, there can be another 'gotacha'.  I'm not an expert and have no experience with newer partitioning schemes  so I hope I'm not giving you bad information.  If I am, I hope someone will jump in and correct me.  

'Traditional' disks can only have 4 primary partitions.  Oftentimes systems come from the manufacturer with 4 primary partitions.  It's necessary to do some changing/deleting in order to create a space to install another operating system.  Ubuntu can install in an extended partition (Windows can't) but you must first create an extended partition.  I use boot software that creates sorta pseudo partitions so I can have more than 4.  Downside is that I must use that software for disk management.

---

