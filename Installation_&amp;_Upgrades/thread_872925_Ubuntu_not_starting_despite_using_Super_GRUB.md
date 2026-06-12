---
title: "Ubuntu not starting despite using Super GRUB"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by Dai84b on 2008-07-28
Hello
I have a dual boot PC with Windows XP and Ubuntu 7.10. I've used Super GRUB Disc to restore the master boot record a couple of times now. The last occasion wasn't wholly successful. The windows loader option works fine so my family are happy. The Ubuntu option gets under way and stops at the *Starting.....* message. 
Live CD and SuperGrub show that the file structure is in place. Do any of you know what to do to restore a full boot? Some fine commands in terminal window while using Live CD perhaps?

regards
David

---

### Post by Potatoj316 on 2008-07-28
have you tried installing grub from a live CD?  Its rather easy, I dont have any links or know how to off the top of my head but a quick search on google should result in what you need to know.

---

### Post by Elfy on 2008-07-28
This link for reinstall grub

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

but - have you by any chance got a kernel update to Ubuntu 8.04.1, kernel 2.6.24-20- - check your menu list - if you are tryingto boot that kernel try the previous one

Ubuntu 8.04.1, kernel 2.6.24-19- there is a bug with the new kernel apparently.

---

### Post by Dai84b on 2008-08-03
I've finally got round to attempting 'Recovering Ubuntu after installing Windows' per Forestpixie's lead. [My excuse for the delay is completing an installation of Xubuntu on a 1999 vintage PC]. I completed the quick start which installs grub in the MBR without any difficulty using terminal in LiveCD. The root device was on (hd0,7). On restarting there was no change. The Ubuntu selection led to the same stopping point as before [at the Starting UP message]. Windows booted up no problems. 

What is the next stage of the campaign to get Gutsy Gibbon working please? I will upgrade to Hardy Heron if this works satisfactorily.
Cheers
David

---

### Post by Elfy on 2008-08-03
We can try and see what is halting the boot by editing the menu.lst entry - you can edit it from the menu before it boots.

Reboot and then when the menu appears press esc to stop the count. Highlight the top entry which you are trying to boot and press 'e'

Use arrow key to move to kernel line and press 'e'

It should go to the end of the line - use the arrow keys to get to wher it says quiet, use backspace or delete to remove _only_ quiet - enter

You should be back at the kernle line - press 'b' to boot

It will probabl hang on one thing make a note of what it's hanging on and post it here, if there are any other errors - note them too.

Not sure if it will work with a usb keyboard so use a ps2 if you have one.

---

