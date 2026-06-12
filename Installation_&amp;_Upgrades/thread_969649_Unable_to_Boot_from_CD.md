---
title: "Unable to Boot from CD"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by MTGap on 2008-11-03
I recently downloaded the .iso from Michigan Tech and burned it onto a disc with Nero, the disc was only 700mb and the file was 699mb this may have been a problem.

My computer sees the disc and I see the menu screen with the Demo and full installation, install inside windows, and learn more. So I think the disc burned succesfully...

I have tried booting my computer with the cd, it is a dell dimension 3000. At the boot screen there is F2 for the bios and F12 for boot options. So far I've tried both, first time with the bios I set boot from CD. It went to XP... Another time I hit F12, selected boot from cd drive from the many options and it booted XP again. What exactly is going on?

All I want to really do is install all the files of Ubuntu on an 80 gb external hard drive so I can plug it in and boot my computer from the USB. So far I can't even boot the CD though...

I once selected the demo and installation and selected 'help me to boot from CD' it added files to my internal hard drive, which I didn't want. Then at the boot screen it did what it was supposed to and gave the options of OS, Ubuntu or XP. I selected Ubuntu and there was a command line thing with <grub> and if I hit the tab button all the options I could do were there. 

What is this? Shouldn't it have just started up Ubuntu? 


I'd appreciate anyones help, this is the first time I'm trying out Ubuntu. So far I'm rather unsatisfied...

---

### Post by taurus on 2008-11-03
How exactly did you burn it to a CD with Nero in windows?  Did you extract it first and burn?  Remember, when you download it, you should leave it as an ISO image file, with .iso extension, and instruct Nero to burn that large file as an image file, not a data file.

---

### Post by MTGap on 2008-11-03
Well I attached a screen shot at the bottom, I use Safari and so when I downloaded it I just went to the folder it was in opened it and it opened with Nero, then I hit burn....

---

### Post by taurus on 2008-11-03
Can you just tell it to save it to your harddrive without unpacking or opening with any program?  Then, make sure you have a one large ISO file before you burn it.  Also, try lowering the write speed from the burning app since you have it at 48X.  Try 4X or 8X if it allows you to.

---

### Post by MTGap on 2008-11-03
The only option is 48x, is there some way I can tell from the original burned disc if it is right? 

Or should I try changing the write method: Track-at-once, disc-at-once, and disc-at-once/96


Here are some more screenshots, one shows the .iso in another spot other than Safari Temporary files, with its properties and it says that it is 698mb.

Then when I looked at the properties of the actual cd-rom it says 698mb... so where is the problem? My computer?

---

### Post by inportb on 2008-11-03
I've always used isorecorder for burning images on Windows. Google it up if you're interested in trying.

---

### Post by MTGap on 2008-11-03
Well based on the fact that in one screenshot it shows in the properties of the disc that there is 698mb on it did it burn right or can I not be sure based on that? I don't want to have to burn it again when it will give me the same thing.

It did work at one time when I asked for the help with rebooting and it gave the option for Ubuntu and XP on the boot screen. It just showed up with a thing called grub. I thought it was supposed to go directly to the OS? I searched for grub here and all it showed was grub errors, mine wasn't an error it was just all commandline stuff...

---

### Post by crapple on 2008-11-03
Try burning another disk at a slow speed.  If your computer has multiple disk drives make sure you are booting from the right one.

Also if you are trying to dual boot xp and ubuntu use [wubi]("http://wubi-installer.org/")
It will let you install ubuntu as a windows application and then let you boot it from a boot menu on startup.

---

### Post by MTGap on 2008-11-03
Well I guess since I can't burn at a lower speed I'll try iso recorder, the fact that I saw Grub command line thing when I booted isn't right then?


I only want it on an external hard drive, with it never touching the internal hard drive, so I don't want to use Wubi.


Well just downloaded Iso Recorder and I'm burning it now at 4x speed...

---

### Post by inportb on 2008-11-03
If your bootup sequence completely skips the disc, you might want to have a look at the BIOS settings for boot order. CD-ROM should have higher priority than harddrive.

---

### Post by MTGap on 2008-11-03
Ok well at the support on dell.com for my computer it says this: 

> 
Changing Boot Sequence for the Current Boot

You can use this feature, for example, to restart your computer to a USB device such as a floppy drive, memory key, or CD-RW drive.

 	NOTE: If you are booting to a USB floppy drive, you must first set the floppy drive to OFF in system setup.
If you are booting to a USB device, connect the USB device to a USB connector. 

Turn on (or restart) your computer. 

When F2 = Setup, F12 = Boot Menu appears in the upper-right corner of the screen, press <F12>. 

If you wait too long and the operating system logo appears, continue to wait until you see the Microsoft Windows desktop. Then shut down your computer and try again.

The Boot Device Menu appears, listing all available boot devices. Each device has a number next to it.

At the bottom of the menu, enter the number of the device that is to be used for the current boot only. 

For example, if you are booting to a USB memory key, highlight USB Flash Device and press <Enter>.

 	NOTE: To boot to a USB device, the device must be bootable. To make sure that your device is bootable, check the device documentation.


I do that and always select IDE CD ROM Device, but it just goes to Windows XP....

I just did the ISO Recorder with the ubuntu 8.10 iso and burned it at 4x and tried that and it went to XP.

---

### Post by taurus on 2008-11-03
Do you have access to another computer that you can test the new CD that you just burnt to see if that machine would boot from the CD?

---

### Post by MTGap on 2008-11-03
Well I'm happy to say I was able to get it to work, I had to put it in the dvd rom tray instead of the cd rom tray. Even though there is no boot option for the dvd drive only cd drive.... 

Is this like it for all computers? Or am I confused that it was a CD? 

Well now I would like to put it on the external hard drive, I was going to do this: [URL="http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/"[/URL]

But my dad is saying no you can unplug it, even though I've done multiple upgrades to the computer with ram and switched hard drives with many computers.... :mad:

Is there any other way I can get it on there, with it being just like any other installation where files are saved as well as changes... 

It seems I can do anything, besides unplugging the internal hard drive and installing ubuntu on the internal hard drive....

My dad keeps making this more difficult for me...

---

