---
title: "Unable to Boot without Live CD"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by OriginalFlavor on 2010-04-05
I have installed Ubuntu 9.04 fom a Live CD.  My system is a Dell Optiplex 745 that originally had Windows XP installed.  Ubuntu is the only OS.  Windows XP was removed.
 
The sytem appears to be running normaly.
 
When I shutdown (not restart) and then power cycle the computer, 
I see the Dell splash screen
then I get the message:
"Errorauto-sensing secondary master hard disk drive.  Strike F! key to continue, F2 to run the setup."
F1 repeats the message.
F2 enters the BIOS setup but does not lead to a fix.
 
If I place the Live CD in the tray and boot from that, I get to the Ubunt install directory.
 
If I click "Check disc for defects", then run the check.  (I can even interupt the check without completing by hitting ESC), then the system reboots.
I see the Dell Splashscreen.
I see the Ubuntu Live CD menu
I choose "Boot from first hard disk"
Then Ubuntu loads perfectly.  I enter my username's passord.
  The system runs fine until the next time I shutdown.
 
How do I get the system to boot directly without needing the LiveCD?

---

### Post by tom4everitt on 2010-04-06
Sounds like you have to restore (reinstall) grub. Try this guide:

[http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11](http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11)

---

