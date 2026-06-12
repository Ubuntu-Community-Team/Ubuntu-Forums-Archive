---
title: "How to get rid of Windows 7 - doesn't allow to boot from cd or usb?"
date: 2012-12-14
forum: Installation &amp; Upgrades
---

### Post by whyregistrationrequired on 2012-12-14
Hi,
 
got my laptop back from warranty "service", and the hd is now equipped with Windows 7. I would like to get rid of it and install Xubuntu/Ubuntu.
 
For some reason the computer refuses to boot from any other device. Whatever I try, it boots to Windows 7. I have tried to put Xubuntu live-cd in the drive and put cd-rom as first boot option - no change whatsoever.
 
Next thing I tried was to make a DBAN-usb and set usb as first boot option, cd as second. Still not good. Windows 7 pops up.
 
What can I do?
 
Oh yeah, I have ASUS K52F

---

### Post by kuifje09 on 2012-12-14
Are you shure you tell the bios to boot from usb or cd/dvd?
Maybe you can try to disable boot from Harddisk? Or did you already these things?

---

### Post by whyregistrationrequired on 2012-12-14
Ok thanks for the tip i'll try that.

---

### Post by whyregistrationrequired on 2012-12-14
Disabled the hard disk, and the message was:
 
Insert proper boot device...
 
,or something like that. Maybe I have managed to screw both the disk and the usb?
 
dvd-rw a problem?
 
anyway, **** computers!

---

### Post by whyregistrationrequired on 2012-12-14
I know it's off topic but does anyone know how to delete a folder in Windows 7?
 
Right-clicking and choosing delete obviously doesn't work: pops up a window showing that it's deleting the files, closes, but the goddamn folder is still there. Windows... Oh how I try to get rid of you...

---

### Post by whyregistrationrequired on 2012-12-14
Why am I trying to delete? Because there seems to be a goddamn folder left in the usb even though it was supposedly formatted. Some kind of formatting! Perhaps that's why the DBAN-usb doesn't work, because there's an extra folder?
 
These frikkin computers are making me crazyyyy ):P

---

### Post by kuifje09 on 2012-12-19
Hm, Sound all rather silly. Never had such problem, maby because I never used windows 7.
Maby better of asking in a windows forum.

But if boot from harddisk is disabled, there must be an option to boot from something else. If you would try an ubuntu live cd, that should be possible then...
Only problem is you need a pc to burn an iso to a cd.

But I am glad to hear the disabling of the boot from harddisk worked[IMG]http://ubuntuforums.org/images/icons/icon12.gif[/IMG]

---

### Post by ezeze5000 on 2012-12-19
I found this on the wiki

The Unified Extensible Firmware Interface (UEFI) is a specification that defines a software interface between an operating system and platform firmware. UEFI is meant as a replacement for the Basic Input/Output System (BIOS) firmware interface, present in all IBM PC-compatible personal computers.[1][2] In practice, most UEFI images have legacy support for BIOS services. It can be used to allow remote diagnostics and repair of computers, even without another operating system.[3]

I went into my BIOS and had to disable the UEFI in the boot section .
I was able to boot after that,
I hope this helps.

---

### Post by offgridguy on 2012-12-19
> **ezeze5000 said:**
> I found this on the wiki

The Unified Extensible Firmware Interface (UEFI) is a specification that defines a software interface between an operating system and platform firmware. UEFI is meant as a replacement for the Basic Input/Output System (BIOS) firmware interface, present in all IBM PC-compatible personal computers.[1][2] In practice, most UEFI images have legacy support for BIOS services. It can be used to allow remote diagnostics and repair of computers, even without another operating system.[3]

I went into my BIOS and had to disable the UEFI in the boot section .
I was able to boot after that,
I hope this helps.
Thank you for this definition of UEFI.

---

### Post by whyregistrationrequired on 2012-12-22
Hi, thanks for the answers!

I finally managed to nuke the windows and install xubuntu. I think there were two simultaneous problems:

-cd/dvd drive is most probably broken: it refuses to boot anything, and doesn't recognise a disk even in xubuntu. it ejects the tray though when i type eject to terminal

-windows didn't manage to make a bootable usb (an extra folder was still there after "formatting"), but i managed to fix it with a mac computer, after which it was possible to nuke the hard disk and install xubuntu

I guess it's time for a new thread for the cd/dvd -drive issue, which is slightly frustrating. Or can someone point immediately a probable solution?

---

### Post by oldfred on 2012-12-22
Sometimes it just needs cleaning?

       How to clean CD lens:
[http://members.iinet.net.au/~herman546/p27.html](http://members.iinet.net.au/~herman546/p27.html)

---

### Post by whyregistrationrequired on 2012-12-22
Yeah, maybe, isn't it lame that it doesn't work when it came from warranty service it worked before sending it there...

---

