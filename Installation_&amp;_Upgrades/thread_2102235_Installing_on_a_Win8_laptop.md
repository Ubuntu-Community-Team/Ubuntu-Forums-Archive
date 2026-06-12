---
title: "Installing on a Win8 laptop"
date: 2013-01-06
forum: Installation &amp; Upgrades
---

### Post by CharlieFoxtrot on 2013-01-06
Note: Although I have been an Ubuntu user for over 5 years, I'm just that, a user, not a technical wiz (but can follow instructions well).

I purchased a new Toshiba L875 laptop to replace my older laptop that died. I have spent the last two days trying to install Ubuntu and learned that with Windows 8 pre-installed and new BIOS, it ain't as easy as it used to be.

First thing I learned is that SHUT DOWN isn't really SHUT DOWN any more.  Powering up after a SHUT DOWN will not allow access to the BIOS by pressing F12. The User's Guide states that to shut down the computer: 

"Highlight Shut down while holding the Shift key, and then click the Shut down option." without explaining when and why the +SHIFT is necessary. 

After a SHUT DOWN + SHIFT, powering-up and pressing F12 up brings up the Boot Menu. By booting from the CDDVD drive with an Ubuntu 12.10 (64-bit) DVD, I am able to load "Try Ubuntu" or "Install Ubuntu". However, when I try to install Ubuntu and get to the Installation type, I get the message "This computer currently has no detected operating systems. What would you like to do?" and there is no option for a side-by-side install.

By searching this forum and elsewhere on the web I read that it is related to a newer BIOS and UEFI. In the course of trying to find a solution I've gone into my BIOS and disabled Secure Boot. The only reference to EPI I see is in the Boot Menu as item 4: LAN EPI Network 0 for IPv4 . . .

Is there a simple way to install dual-boot Win8/Ubuntu on this laptop?

If not, is it safe to continue with the install with "Erase disk and install Ubuntu", wiping out Win8 or will that just create new problems?

---

### Post by CharlieFoxtrot on 2013-01-09
Marked as solved but resolved is probably the better word. No one had any advice for me, so I just went ahead and installed 12.10 wiping out Win8. The installation went well and 12.10 worked as advertised. Unfortunately, the default display driver didn't work so well. Tried installing other AMD drivers from the repositories and AMD's website. Everyone I tried either wouldn't load or caused a hang on reboot. From what I found searching the web, it appears that there are currently no linux drivers that work with my Toshiba 875.

Restored Win8 from recovery discs and after five years I'm back to being a "Windows wiennie" again (at least on the laptop). Next time I'll exercise more care in selecting a computer.

---

