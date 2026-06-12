---
title: "Ubuntu CD will not boot on OS-less laptop"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by AlbertoFerrer on 2008-11-22
I have a laptop that's a few years old and I thought it would be a great way to get started with Linux. I was installing 8.11 from the Internet (this laptop doesn't have a floppy drive and didn't have a CD-ROM drive) and at some point after I chose my time zone, the installation crashed. I now have no operating system at all on the laptop, and it will only boot to BIOS.

I found a CD-ROM drive for the machine on eBay and tried installing from the Live CD and the Alternate versions but the machine, after spinning the CD (it's selected at the first boot device in BIOS), goes back to the same message "strike F1 to retry boot, F2 for setup" that it's been giving since this started.

Is there anything I can do to get Linux on this machine? Or am I just the proud owner of a brick formerly known as a laptop?

Thanks for your help.

---

### Post by want2bdifferent on 2008-11-22
maybe try putting windows on the laptop, to see if it is booting from CD?

when you say 8.11 do you mean 8.10?

what laptop do you have?

wat

---

### Post by AlbertoFerrer on 2008-11-23
Thank you for your reply. Unfortunately, I no longer have the Windows 2000 CDs that I would use to install it. In fact, I don't have any Windows CDs at all. 

The laptop is a Dell Latitude CSx circa 2000/2001. It used to have Windows 2000 on it (and the usual Microsoft Office, etc., software). All that went away when the previous install crashed.

Thanks again for your help.

---

### Post by AlbertoFerrer on 2008-11-23
And yes, I meant Ubuntu 8.10, sorry for the typo.

---

### Post by Bucky Ball on 2008-11-23
You do have it set to boot from CD in your BIOS, yea? Might be a silly question but no harm checking. :) Do other CDs work in this drive?

---

### Post by oilchangeguy on 2008-11-23
> **AlbertoFerrer said:**
> Thank you for your reply. Unfortunately, I no longer have the Windows 2000 CDs that I would use to install it. In fact, I don't have any Windows CDs at all. 

The laptop is a Dell Latitude CSx circa 2000/2001. It used to have Windows 2000 on it (and the usual Microsoft Office, etc., software). All that went away when the previous install crashed.

Thanks again for your help.

what are the specs of this computer? cpu speed, amount of ram, and hard drive size?

---

### Post by AlbertoFerrer on 2008-11-23
The laptop is a Pentium III 500MHz with 512MB of RAM and a 12GB HDD.

**Update:** I tried something different. I made burned another install CD, (another Alternate) but this one I made "bootable" using the sbm.bin that I found as part of the Alternate CD contents.

I can get it to "boot" to the boot manager where I can get it to ask if I want to use Ubuntu or Windows 2000. Windows doesn't actually boot up (it hands in the middle of the startup process) and Ubuntu shows the logo and progress bar, but then crashes with some sort of I/O error message. 

Then I tried all the other options on the boot screen (Install Ubuntu, Try Ubuntu without changing your computer, OEM install, etc. None actually work except that I was able to get to a grub prompt.

Now I really don't know what to do as I stare at grub> all day.

**Update II:** I tried again with the Install and I got a series of errors like *[COLOR=Blue][1200.844072] Buffer I/O error on device fd0, logical block 0[/COLOR]* (it was a long list of those, with the numbers within the brackets changing each line). I decided to leave it be for a while and when I checked back, it said: 

[I][COLOR=Blue]BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(iniramfs) _[/COLOR][/I]


Thanks again for the help.

---

### Post by Bucky Ball on 2008-11-23
Maybe ... when you get to the partition section of the install, make sure you have the 'bootable' flag on the Linux OS drive set to 'yes' ('on' actually, from memory). There shouldn't be a need to load any other software. That will make that partition bootable. Possibly you are just missing that step if you are manually partitioning.

---

