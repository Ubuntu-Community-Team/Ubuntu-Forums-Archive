---
title: "can't boot into ubuntu nor from windows installation cd"
date: 2014-12-10
forum: Installation &amp; Upgrades
---

### Post by aka.mdsg on 2014-12-10
Hello, I ran into a mountain of troubles after trying to install Ubuntu.

First, it didn't work and my computer just kept saying "reboot and select proper boot device" or something alike, I posted here on the forums but none of the solutions could solve my issue, one of them I didn't try because I didn't understand how to do it, the sudo efibootmgr -c -L "Windows Boot Manager" - L "/EFI/ubuntu/shimx64.efi", I tried it into the terminal of the Live CD and it didn't work because apparently it was not meant to use it there, but I have no other operating system on the computer to use it from so... I only have on my 1TB HDD a failed try for ubuntu..

Now I am completly screwed apparently, I cannot boot from the CD Windows installation, I gave up on ubuntu because it brang me so many problems...

I use an Aspire M3985, I can boot form the ubuntu disc to use the live version of ubuntu but I cannot boot from the windows cd, and I have no idea why, I tried two different discs of windows and none of them are detected when I go into the boot options.. it only appears my hdd and that is broken with this ubuntu istallation..

So, any idea of how I make my windows cd bootable so I can install windows?

For the ubuntu problem, I tried many different things, the boot-repair recommended tool on the live cd, turn secure boot off, put the HD in the first position on the BIOS, I inserted a password protection on the BIOS cuz a moderator told me that it would unlock some other options so I could boot ubuntu but none were sucessfull, and I couldn't do that one involving sudo efibootmgr  because I didn't understand how to do that command, the live cd terminal doesnt do anything with that code provided to me from a moderator..

If I could get help in booting the disk of windows or resolving this ubuntu issue, I would appreciate a lot, even tho I prefer the windows solution ...

Thanks :|

---

### Post by oldfred on 2014-12-10
Thread on booting Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2256100](http://ubuntuforums.org/showthread.php?t=2256100)

Do not know about Windows.
You may do better on a Windows forum.
 [http://www.eightforums.com/](http://www.eightforums.com/)
[http://www.sevenforums.com/](http://www.sevenforums.com/)

You do have an UEFI system, and most Windows 7 DVDs are BIOS boot, but can be copied to a flash drive and converted to UEFI boot.
If you really have CD, those are not full install and may not be bootable. Probably upgrade CDs.

---

### Post by aka.mdsg on 2014-12-10
I already converted it to uefi, its copying to the usb stick now, il give it a try, trough CD I have not been lucky...

Thanks a lot for the information you provided me, I couldn't find a solution trough google so if it wasn't you I would be confused, you are a good moderator bro, thanks :)

---

### Post by Mark Phelps on 2014-12-10
> So, any idea of how I make my windows cd bootable so I can install windows?

Any Windows disk that came with the PC is automatically bootable.  So, if it does not boot, there's something wrong with the CD or your  BIOS settings.

Also, since Vista, Windows does not come on a CD, it's too large; instead, it comes on a DVD.  

IF this is really a CD and it came with your PC, then it's more likely a  Recovery CD, in which case, all it will do is boot into a recovery environment from which you can do a Restore (to factory settings), using the Recovery partition on the PC -- presuming that is still intact and in good shape.

---

