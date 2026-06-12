---
title: "Fresh 9.10 Install - Freezes before login"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by dejay703 on 2009-12-05
I'm updating one of my computers to 9.10 (fresh install), and my when my computer boots up, it freezes before the login screen appears.  I see the screen that says ubuntu with the loading bar under it, but the loading bar freezes after about 1 second and just hangs there.  After a bit, the fans on my computer start spinning up faster but nothing happens.

I want to get into my GRUB menu so I can see what's freezing up the process, but I've never had to do that when I don't have a dual boot.  I read from the forums that I have to hit ESC right after GRUB boots to get into the menu, but that has not worked for me.  I have also tried continually hitting ESC right after the computer posts, but it still goes to the ubuntu screen and gets stuck.

Is there any other way around this to debug what is going wrong?  Thanks in advance!

---

### Post by darkod on 2009-12-05
Don't know much about the problem but ESC was for 9.04 and before I think. For 9.10 it's SHIFT. Give it a go.

---

### Post by dejay703 on 2009-12-05
Ok, I just tried continually hitting the ESC keep after I saw the GRUB loading, and this time it went directly to a terminal saying:

fsck from util-linus-ng 2.16
mountall: Cancelled
Warning... fsck.ext4 fore device /dev/sda1 exited with signal 15.
mountall:fsck/ [450] terminated with status 8
mountall: General fsck error
init: mountall main process (442) terminated with status 1
General error mounting filesystems.
A mintenance shell will not be started
CONTROL-D will terminate this shell and re-try.


I'm guessing all that output is because hitting ESC stopped some process.  Can anyone recommend how to go about debugging why the regular boot is not working from this terminal?  Thanks!

---

### Post by dejay703 on 2009-12-05
> **darkod said:**
> Don't know much about the problem but ESC was for 9.04 and before I think. For 9.10 it's SHIFT. Give it a go.

Ahh, thanks.  So I got rid of "quiet splash", to see where it was halting.  Surprisingly, it got through everything, and then showed that first Ubuntu screen with the loading bar again.  It then froze (as before) after a second.  Suggestions anyone?

---

### Post by darkod on 2009-12-05
It might be a dumb idea but are you sure you haven't got video driver problem? Did you use the Try Ubuntu option to check if it will run OK before installing?
On my PC the Try Ubuntu was restarting the PC just before it should show the desktop (or login screen). But the installer installed fine. Then on first boot it restarted the PC at the same place as Try Ubuntu option. :)
After wasting few days reading around it turned out video driver. I selected the recovery mode entry from grub menu, added video driver handling package and working perfectly since. Want the commands?

---

### Post by dejay703 on 2009-12-05
Hmmm sure, what package did you install?  It seems like it could be a video driver problem, but I just pulled the graphics card out of my ubuntu 9.04 PC (upgraded from 8.04).  And, if I remember correctly, I didn't have to do anything special on that installation when I installed 8.04.  Anyway, I'll try anything right now :)

---

### Post by dejay703 on 2009-12-05
Hmmm, so I just remembered that when I installed (after "trying ubuntu"), it did work, but I only had one monitor plugged in (DVI).  I was booting now with a DVI and VGA monitor.  Unplugged the VGA, and it boots just fine now.  I'm sure I can figure out how to fix it from here.  I probably just need Nvidia's proprietary drivers.  Thanks for the help!

---

### Post by darkod on 2009-12-05
EnvyNG.
Select the recovery mode, on the next menu when asked select something that sounded like "root with networking" to give you internet access. Then:
sudo apt-get install envyng-core envyng-qt

Running in text mode with:
envyng -t

You will figure out the rest. Forgot to mention, seems to cover only ATI and Nvidia drivers. You just select manufacturer, it downloads itself (have no clue how it knows from where and what). There is option in its menu to remove existing driver but I never did that, just downloaded the new one. After finishing the install it will ask to reboot and that was it.

PS. I just read you other post. The package also works as GUI if you have the desktop running. It's in Applications - Audio Video (I think)

---

