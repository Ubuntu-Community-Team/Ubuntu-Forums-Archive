---
title: "Aaaargh installation craps out"
date: 2006-03-07
forum: Installation &amp; Upgrades
---

### Post by Bubba Ho-Tep on 2006-03-07
Ok, so I've installed Ubuntu on 3 or 4 old computers now, I've played about, liked what I saw and I've decided to put Ubuntu on my "real" computer a P4 HP Pavilion t620a

...but the Ubuntu (Breezy) install always fails. 

I'm using shipped CDs (which I know work as I've installed Ubuntu to other 'puters) 

the BIOS is altered to boot off the CD 

I've tried the internal IDE CD-ROM and and an external USB CD-ROM - and each time it detects the Ubuntu Cd - starts installing vmlinuz and initrd.gz, says "Uncompressing... ok booting the kernel" and then reboots.

The Live CD does the same thing

I've booted Puppy Linux ok on this computer (from CD) and a FreeBSD install seemed to go ok (I didn't go thru with the install)

I have a 10Gb external USB hard drive which I can boot off  - is there some way I can take the stuff off the CD and stick it on the external HD?

Or is there something else I can try to boot from CD?

I hope someone can help cos I've spent a bit of time with Ubuntu and I don't want to change distribution just to get Linux onto my P4

TIA

BH-T

---

### Post by Bubba Ho-Tep on 2006-03-08
no-one? sigh........

---

### Post by zerocool1014a on 2006-03-08
not sure about your problem what exactly is happening i know im having a heck of a time getting it to install on my thinkpad laptop.  where is it stopping or freezing?

---

### Post by Bubba Ho-Tep on 2006-03-08
It reboots after the "Uncompressing... ok booting the kernel"  - dunno if this may help you but have you mucked about in yr BIOS - with IDE options? 

I'm at work at the mo and will have another crack at installing it tonight, if not I'm going to ditch Ubuntu and try Suse or Mandriva. Cos while I like Ubuntu and all, if I can't install it then its crap/useless.

BH-T

---

### Post by somerville32 on 2006-03-08
I had a similar problem once and I need to use special boot paramaters regarding the video - Try looking around there.

---

### Post by Bubba Ho-Tep on 2006-03-08
Not sure I understand - you mean video settings in the BIOS? Are there any?

Also I've had Puppy Linux successfully boot - it appears to be a Ubuntu thing rather than my 'puter

---

### Post by byen on 2006-03-08
Ok...just an off-hand suggestion.....try one of these and see if they work

1.try to boot using no-apci
2.try disabling the Legacy USB support option in the bios-options menu
3.try removing all the USB drives and doing an install

Can you provide us with your hardware specifications?

I would suggest you try the ones I have mentioned here.. I had a similar problem with Fedora and disabling legacy Usb support helped!See if this works...Goodluck!

---

### Post by Bubba Ho-Tep on 2006-03-08
Thanks for the info, unfortunately didn't help

1) couldn't see anything 'bout ACPI in my BIOS

2) disabled Legacy USB (the 'puter got one of those multi card readers connected to USB headers on the MB). no joy

3) physically disconnected all usb devices. again no joy 

All I can think of at the mo is to pull the HD out, stick it in another computer, install Ubuntu, reinstall to the HP and hope for the best.
 
Is this worth doing? or should I just save time and install another distro?

either way thanks for the suggestions

BH-T

---

### Post by Landser on 2006-03-08
I have the same problem as you.. With an HP Pavilion machine too.

> Ok...just an off-hand suggestion.....try one of these and see if they work

1.try to boot using no-apci

He means that you must type this at the command line:

live acpi=off

But this didn't help me either.. Can you try it and tell us what happens?

---

### Post by byen on 2006-03-08
> 1) couldn't see anything 'bout ACPI in my BIOS
I think I should have been more clear. Im sorry I wasnt specific. The acpi feature comes into play not at the bios but while booting the live cd. please try this and see of this works:
After inserting the livecd...type this to boot the cd:
```
live acpi=off noapic nolapic
```

let us know what happens.

EDIT: code corrected from livecd to live

---

### Post by Bubba Ho-Tep on 2006-03-09
Bingo!

(minor correction to the code - "live" rather than "livecd")

er ok the Live CD booted into Ubuntu - now what? (its late here and I'm tired so I'll experiment tomorrow) can I install Ubuntu from the Live CD?

Also what is the code doing exactly - turning off power management I got but noapic? nolapic?

BH-T

---

### Post by byen on 2006-03-09
I am not an expert in the terminology but let me try...
By disabling apic and lapic you are trying to prevent any power/inter processes interrupts that the processor might get during the boot process. Usually it is very common for this to happen and that is where the acpi and apic steps in! but since we are disabling acpi we are also disabling apic and lapic.
Im not sure how the system handles power management once this is disabled but this a very common way of dealing with computers with apic issues. (sorry i wasnt able to hit the target)

Coming back to your questions:
1.Though you have disabled acpi/apic etc once the OS has been booted, Power management is usually taken care of by the OS .
2.Now that you have the live cd up and running, see if Ubuntu supports all your hardware and you can use it as an OS on a disc
3.No you cannot install Ubuntu from the liveCD. I know some OS's like Mepis, PclinuxOS can but not here on Breezy (Ubuntu plans to have this feature in Dapper which is being released in a month!)

Hope that answers your questions. Enjoy Ubuntu and look around if you have any hardware issues. Goodluck!

EDIT: zerocool1014a.I was just going to ask you if it worked for you but I saw a post of yours which says that it did. Glad it worked out!

---

### Post by Bubba Ho-Tep on 2006-03-09
ok thanks for the info.

Ubuntu looks ok on the HP - how do I install it - is it just a matter of 

live acpi=off noapic nolapic

using the install CD?

BH-T

---

### Post by byen on 2006-03-10
If you are using the install CD there is already an option in the menu that gives you a choice between a normal install and a Install using acpi=off 
All you would have to do is select the later!

If for some reason it still fails...try to boot the install cd using

```
Linux acpi=off noapic nolapic
```

Good luck with the install. If you run into trouble...we are here!

---

### Post by Bubba Ho-Tep on 2006-03-11
Thanks for the help Byen! Everything installed easy once I disbled acpi. The info was actually in the F1 help menu (which I never noticed) but I wouldn't have known to switched off acpi.

Now I have a P4 Ubuntu system. Onwards and upwards! :-D \\:D/ 

BH-T

---

### Post by pearlson on 2006-07-08
when i tried installing from the liveCD my notebook was stalling at the line, "unpacking linux. ok, loading kernel". 


someone told me to enter "boot acpi=off" in the extra options. That worked and got me past the freeze and i was able to install ubuntu from the Ubuntu desktop. 

now when grub loads and i select ubuntu to run it freezes at the same point and i have to do a hard shutdown. i tried entering the acpi=off command by editing the command line and two things happen.

First; if i enter into the Ubuntu boot code it hangs up in the same place, "unpacking linux. okay, loading the kernel." 

Second; if i enter the code in the diagnostic mode it it makes a small difference but it just hangs up somewhere else after a lot of code flashes by the screen.

any ideas how to append the boot command from grub to make ubuntu load?

also, my sound card isn't picked up when i was running the liveCD.

 i have an ASUS S1300N machne.

thanks! MP

---

### Post by pearlson on 2006-07-09
so i fixed the problem, finally!

the acpi=off command needed to be added again to the boot command in grub. so for a while i would manually put the line in after each restart. then i found a website explaining how to edit the menu.lst -- here is the fix.

(i used Vim, but any text editor will work as long as you are su -)
FIRST: copy the menu.lst file incase you make a mistake.

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-original

SECOND: edit the menu.lst file. you'll need super user priv since its a read-only file by default.

sudo vim /boot/grub/menu.lst

the code is pretty simple for the file: # are comments and ignored by the booting shell, the rest is code that is either displayed or executed. scroll down to where there aren't any more commented sections and append the Ubuntu command as follows:

title Ubuntu, kernel 2.6.15-25-386
root (hd0,2)
kernel /boot/vmlinuz-2.6.15-25-386 root=/dev/hda3 ro quiet splash acpi=off
initrd /boot/initrd.img-2.6.15-25-386
savedefault
boot


you can add the acpi=off to the recoery mode also if you want.


cheers,
MP

---

### Post by 1an on 2006-08-13
Whe trying to boot from live cd (in order to install) I get: 

[4294667.296000]  SMP mptable: null local APIC address!
[4294667.296000]  BIOS bug, MP table errors detected...
[4294667.296000]  diasabling SMP support. (Tell your hw vendor)

Any thoughts?  I've tried "live acpi=off" and "noapic".  Neither worked.


I'm using a P4 1.4G processor with 384Mb of RIMM.  This is a Dell Dimension 8100.

---

### Post by MadKAT on 2006-08-28
Hi,

I am having the same problem on my HP pavillion notebook zx5000:

P4 3.2 GHz w/ smp
1G ram
wireless 
  
When I try "live acpi=off noapic nolapic", it returns "Loading /casper/vmlinuz......." and just hangs there.

This is the 6.06.1 CD by the way. and Mandriva 2006 is currently installed.  Ubuntu works well on my whitebox desktop.

Thanks.

---

### Post by DuncanG on 2008-01-24
Ubuntu 7.10 installed, wil not boot in normal mode, will boot in recovery mode.
I tried appending "acpi=off" after splash to the "kernel" command, but it didn't help.
Is someone able to help me get the system booted please. I don't know where to look to see the problem, I just get a blank screen. Is there a log file I can check when I reboot in recovery mode ? In recovery mode I don't have network access, so can't download latest patches, and USB doesn't work either.

Edit: Edited normal kernel line to remove "quiet splash" and also got rid of final quiet. Managed to get command line (CTRL-ALT-F1/2 ?) and startx. This wasn't recovery mode, so have net access. Dowloaded latest patches and ATI drivers. Altered /etc/usplash.conf to set resolution to 1024x768, and it starts. Woot !

---

