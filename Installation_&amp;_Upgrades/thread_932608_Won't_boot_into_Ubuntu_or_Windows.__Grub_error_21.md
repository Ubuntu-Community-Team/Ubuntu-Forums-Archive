---
title: "Won't boot into Ubuntu or Windows.  Grub error 21"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by timdownie on 2008-09-28
Apologies if this has been done to death repeatedly but I'm totally new to Linux.

I had Windows problems with my PC after a trial run of ubuntu without installation but that turned out to just be a creaking windows problem solved by a long overdue complete re-installation.

Having fixed the Windows XP problem, I had a go at installing Ubuntu to an external USB hd.  Everything seemed to be going well until the reboot when the system hangs with a "loading stage 1.5" and "Grub error 21" message.

Unfortunately, removing the external hd doesn't allow the PC to boot with Windows so the only way I can access the machine at the moment is with the live CD.

I've searched the forums a bit and it seems I'm not alone but I find most of the advice close to doubledutch so I'm hoping there's someone out there with a bit of patience.

FWIW, my PC has a 250gb sata HD and the BIOS does allow for booting from USB memory sticks and USB CD roms but there's no option for USB HDs.

I'm not desperate to have Linux on a USB external drive, I just wanted to try it out "safely" but it seems I've screwed that up. ;-).

In the short term, what's the easiest way of getting Windows back?  Should I just take the plunge and install Ubuntu to the main HD and forget faffing around with and external drive?

TIA

Tim

---

### Post by werries on 2008-09-28
you probably need to update grub.

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "find /boot/grub/stage1"
6. it should find where grub is, then do "root (hd0,0)", and put in the info for what it said before (hd0, 3) for example.
5. Type "setup (hd0)", to whatever your harddisk number is.
6. Quit grub by typing "quit".
7. Reboot.

---

### Post by caljohnsmith on 2008-09-28
Right now it sounds like you have Grub (Ubuntu's boot loader) installed to the MBR (master boot record) of your Windows drive. If you don't have the option to set your BIOS to boot your USB drive, then one option is to restore the Windows MBR and then add Grub as a boot option in the Windows boot loader. The advantage of this is you will be able to boot Windows regardless of whether your USB drive is connected or not, or whether something happens to your USB drive. This is what I would recommend, but does this sound like a good plan to you? 

If so, the first thing to do is restore your Windows MBR; do you have a Windows Install CD? If so, boot it up, press "r" at the first main menu to get the recovery console, and run:
```
fixmbr
```
If you don't have a Windows Install CD, you could download the [Super Grub Disk]("http://www.supergrubdisk.org/") and use that to restore your Windows MBR. Let me know how that goes or if you need more details/info, and we can work from this point.

---

### Post by timdownie on 2008-09-28
> **werries said:**
> you probably need to update grub.

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "find /boot/grub/stage1"
6. it should find where grub is, then do "root (hd0,0)", and put in the info for what it said before (hd0, 3) for example.
5. Type "setup (hd0)", to whatever your harddisk number is.
6. Quit grub by typing "quit".
7. Reboot.

Sorry, but you're still shooting over my head.  I've found Terminal, fired it up and tried "find /boot/grub/stage1" but it comes up with "No such file or directory".

I've had a look at partition manager but can't make much sense in terms of what my HD number is from it.  My boot partition is listed as /dev/sda1.

---

### Post by lavinog on 2008-09-28
> **timdownie said:**
> Sorry, but you're still shooting over my head.  I've found Terminal, fired it up and tried "find /boot/grub/stage1" but it comes up with "No such file or directory".


did you type grub first?
> 3. Type "grub"
4. Type "find /boot/grub/stage1"

---

### Post by timdownie on 2008-09-28
> **caljohnsmith said:**
> Right now it sounds like you have Grub (Ubuntu's boot loader) installed to the MBR (master boot record) of your Windows drive. If you don't have the option to set your BIOS to boot your USB drive, then one option is to restore the Windows MBR and then add Grub as a boot option in the Windows boot loader. The advantage of this is you will be able to boot Windows regardless of whether your USB drive is connected or not, or whether something happens to your USB drive. This is what I would recommend, but does this sound like a good plan to you? 

If so, the first thing to do is restore your Windows MBR; do you have a Windows Install CD? If so, boot it up, press "r" at the first main menu to get the recovery console, and run:
```
fixmbr
```
If you don't have a Windows Install CD, you could download the [Super Grub Disk]("http://www.supergrubdisk.org/") and use that to restore your Windows MBR. Let me know how that goes or if you need more details/info, and we can work from this point.

Cheers.  Fixmbr did the job and I have Windows back.  I would still like to have a go with Ubuntu though and preferably with an external bootable drive that I can use with other PCs.

I suspect this may be beyond my knowhow but if anyone can suggest where I went wrong first time I'd be grateful.

Cheers,
Tim

---

### Post by timdownie on 2008-09-28
> **lavinog said:**
> did you type grub first?

Yep.  No dice.

I suspect I screwed up the initial installation by ejecting the Live CD rom early as I was worried about the PC booting from the CD rather than the new drive and when it didn't work, I tried repeating the installation figuring that this would sort the problem but it didn't.

Something clearly got screwed in the MBR (which is fixed now, at least for Windows) but I would have thought a re-install would have cleared it.

If I try again, now having restored the MBR, is it likely I get a dual boot system?

Cheers,

Tim

---

### Post by caljohnsmith on 2008-09-28
> **timdownie said:**
> Yep.  No dice.

I suspect I screwed up the initial installation by ejecting the Live CD rom early as I was worried about the PC booting from the CD rather than the new drive and when it didn't work, I tried repeating the installation figuring that this would sort the problem but it didn't.

Something clearly got screwed in the MBR (which is fixed now, at least for Windows) but I would have thought a re-install would have cleared it.

If I try again, now having restored the MBR, is it likely I get a dual boot system?

Cheers,

Tim
Well, if you don't mind having your Windows drive dependent on your USB drive, you can install Grub to the MBR of your Windows drive. The problem you were running into before is that you have to run grub as root with "sudo grub", and also you mentioned a boot partition, so you have to use the find command a little differently:
```
sudo grub
grub> find /grub/stage1
grub> find /boot/grub/stage1
```
One of those find commands should return your Ubuntu partition in the form of (hdX,Y), for example (hd1,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hd0)
grub> quit
```
That will install Grub to the MBR of your Windows drive, but Grub's system files will be on your Ubuntu drive. Give that a try, and remember you can always run "fixmbr" again to go back to a Windows MBR, so you have nothing to lose by trying the above. On reboot you should get a Grub menu, but choosing the OSes may result in an error which we will need to correct; but see if you get the Grub menu first and we can go from there.

---

