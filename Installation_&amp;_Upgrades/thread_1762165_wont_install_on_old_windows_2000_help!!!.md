---
title: "wont install on old windows 2000 help!!!"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by funbob10 on 2011-05-18
I have been trying for a week now to install ubuntu on my windows 2000. I have followed both the usb and cd install to the t with no prevail. it seams that it wont boot to disk or recognize and boot to usb. I have test this on both of my windows 2000 computers and i gotten the same problems. Any help would be really appreciated, Thanks.

---

### Post by BrandonC19 on 2011-05-18
Have you checked the BIOS to see if booting from CD is checked? Most computers from the early 2000's wont boot from USB, unfortunately. Check your BIOS by pressing either F1, F2, F10, F12, ESC, or DEL as soon as your pc comes on. Most comps will display the key for you to press. Even better is if you see something along the lines of "Press <key> to access Boot Menu" as from there you can just choose the device to boot from.

---

### Post by funbob10 on 2011-05-18
Yes, i have tried just about every boot possible, cdrom, ide-1, ide-2, ide3, A:/ zip drive, Z:/ zip Drivae, SISCI. I am out of options and it keeps launching to windows 2000 on IDE-0.

---

### Post by confused57 on 2011-05-18
Plop Boot Manager may be an option:
[http://www.plop.at/en/bootmanager.html#runwin](http://www.plop.at/en/bootmanager.html#runwin)

---

### Post by tommcd on 2011-05-19
> **funbob10 said:**
> I have been trying for a week now to install ubuntu on my windows 2000. I have followed both the usb and cd install to the t with no prevail.
How did you burn the iso to a CD? If you are burning the CD from Windows, use Iso Recorder or Infra Recorder: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
And be sure to burn the iso at the slowest possible speed.

---

### Post by funbob10 on 2011-05-19
> **confused57 said:**
> Plop Boot Manager may be an option:
[http://www.plop.at/en/bootmanager.html#runwin](http://www.plop.at/en/bootmanager.html#runwin)

I have attempted plop but the manual is very poorly worded and i have no clue how to run it let alone set it up.

Also I have burned there boot disks on different speeds with different os' but they don't work on the windows 2k's, they work on my current dual booted computer and other windows 7's but thats it.

any help, Thanks.

---

### Post by tommcd on 2011-05-19
> **funbob10 said:**
> 
Also I have burned there boot disks on different speeds with different os' but they don't work on the windows 2k's, they work on my current dual booted computer and other windows 7's but thats it.

What exactly happens when you try to boot from the CD on the Windows 2000 computer? Give details here.

If it just boots straight into Windows then the computer is likely not set to boot from the CDROM drive. Make sure the computer is set to boot from the CDROM drive as *the first boot device* in the computer's BIOS.

---

### Post by funbob10 on 2011-05-19
> **tommcd said:**
> 
If it just boots straight into Windows then the computer is likely not set to boot from the CDROM drive. Make sure the computer is set to boot from the CDROM drive as *the first boot device* in the computer's BIOS.

The exact order I've had it in is CDROM, IDE-1, and IDE-0. IDE-0 is the windows 2000. when its booting it shows the screen checking to see if it can boot to cd, then it checks if it can boot to IDE-1, then it boots successfully to windows 2000 on IDE-0.

---

### Post by tommcd on 2011-05-19
Boot from the CD on one of the other computers that it works on and run the option to check the CD for defects. You may have hit the space bar to see this option. 
(It used to on the main screen when the Ubuntu live CD booted up. Apparently, the Ubuntu devs decided that was too easy, so they chose to hide it).
If the CD passes the integrity check; and the Windows 2000 computers are indeed set to boot from the CDROM drive as the first boot device, then I am not sure what else you can do.
It seems that the Windows 2000 computers are not recognizing the CD for whatever reason.

---

### Post by wandalalakers on 2011-05-19
I've seen some CD rom / DVD rom drives go bad, meaning they can still read discs once you boot the operating system but won't boot from a CD or DVD.
Do you have another ide cd rom that you can install in this computer?
I always have a spare ide dvd rom laying around in case I have an old computer with a bad cd rom or dvd rom drive.  This way I can install ubuntu on an old pc that has a bad cd or dvd rom drive.  Also maybe the drive is too old to boot from a cd-r.  If you have a windows 2000 or windows xp original cd not a cd-r, see if you can boot from that.

---

### Post by funbob10 on 2011-05-19
> **pcdoctor said:**
> I've seen some CD rom / DVD rom drives go bad, meaning they can still read discs once you boot the operating system but won't boot from a CD or DVD.
Do you have another ide cd rom that you can install in this computer?
I always have a spare ide dvd rom laying around in case I have an old computer with a bad cd rom or dvd rom drive.  This way I can install ubuntu on an old pc that has a bad cd or dvd rom drive.  Also maybe the drive is too old to boot from a cd-r.  If you have a windows 2000 or windows xp original cd not a cd-r, see if you can boot from that.

Sadly I don't have the old windows 2000 boot disk cause these went originally my computers. My old friend built both of them so i cant really check if it will boot to a windows 2000 or xp disk.

The only thing i can think of doing is taking the disk tray out of one of them and putting it one of the computers and hope it works.

Also I think I installed plop but I have absolutely no clue on how to use it

---

### Post by funbob10 on 2011-05-20
Also I have followed about every tutorial on plop and i still cant get it to work. The only way i an think of install ubuntu is dual boot the computer which i don't want to do cause it will slow it down(right?).

---

### Post by tommcd on 2011-05-20
> **funbob10 said:**
> Also I have followed about every tutorial on plop and i still cant get it to work. The only way i an think of install ubuntu is dual boot the computer which i don't want to do cause it will slow it down(right?).
Dual booting with Windows will not slow down Ubuntu. You will still need some way to boot into the Ubuntu installer though, either from a CDROM drive or a usb flash drive. Since the computer is old it is likely that booting from a flash drive is not possible.

Have you tried any other linux live CDs just to see if they will boot from the CDROM drive?

---

### Post by funbob10 on 2011-05-20
I have only tried ubuntu but i don't see a reason why ubuntu wouldn't work and another one would.

---

### Post by linuxinstalledfromhdd on 2011-05-20
You should try a network installation.

[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

