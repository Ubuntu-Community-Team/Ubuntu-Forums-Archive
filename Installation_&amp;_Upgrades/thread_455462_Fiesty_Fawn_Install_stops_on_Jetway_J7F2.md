---
title: "Fiesty Fawn Install stops on Jetway J7F2"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by sparkfel on 2007-05-26
I recently tried to install Ubuntu 7.04 on a Jetway J7F2 1.2 GHz Fanless Mini-ITX mobo with 1GB of RAM. The system boots to the CD and brings me to a desktop. When I go to install Feisty Fawn on the system it gets to 79% and it says "creating user" - then the install box goes away, and the install never completes. It just dumps back to the desktop

On reboot, the system just hangs after POST. I have tried different hard drives and CD/DVD ROM Drives (IDE and USB) and the result is the same every time. Windows XP loads and runs just fine on the same system. I have successfully installed Ubuntu 7.04 on a Via Epia MII 12000 Mini-ITX, so I know what it should do.

I've gone in and changed a few BIOS settings. I made sure the 1st boot device is the IDE hard drive, turned off the SATA controller, but no change. I re-downloaded the ISO and burned a new CD and get the same issue. It gets to 79% - creating user - then quits. It appears the hard drive isn't being partitioned and formatted. I've even zero'ed out the hard drive and tried again. Like I said, I even tried a different hard drive.

Any suggestions?
Reply With Quote

---

### Post by sparkfel on 2007-05-29
OK,  I got a little further.  After some reading I re-burned the Feisty Fawn ISO onto a DVD instead of a CD.  This got me further in the install.   Now I get to 94% and get the error:

Executing 'grub-install (hd0) failed.
This is a fatal error

And then the install quits when I click OK.



The alternate install ISO fails either as a CD or a DVD.  Even though the disc tests OK, I get read errors on install.   The memory tests OK.  And the IDE controller works in Windows...

---

### Post by Vially on 2007-08-17
Don't waste your time with this piece of @*#$^%  c**p. Even if you would manage to install it, like I do for example, then it would still lock up when it wants to have fun. Read more here :
[http://forums.viaarena.com/messageview.aspx?catid=28&threadid=78573](http://forums.viaarena.com/messageview.aspx?catid=28&threadid=78573)

I have been trying to make this board reliable for 2 months now, and to no avail, even after trying 2 beta bioses from jetway and trying ten distributions. All I want now is to find a smart way of breaking it to pieces, as I cannot return it. Any ideas ?

---

