---
title: "Wubi Installation with 10.04 fails"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by matmuc on 2010-05-10
I am trying to install 10.04 with wubi and I encounter a strange error:

At first, everything runs normally.
Then I am asked to reboot the system.
After rebooting, Ubuntu starts with a GUI (desktop background, my USB-Mouse is working) and a Window appears ("completing installation" and some advertisement).
A dialog tells me, that the systems tries to set the time (probably from an NTP-Server). This is shown with a completion bar, starting at 571% and going up to 800% in several steps.
Then it says: "Installation des Grundsystems".
Next steps: creating ext4 file system, copying files ...
Again, a progression bar appears, going up to 28%.
Then, an error message appears: "Datei entspricht nicht ihrer Quelle auf der CD/DVD" (file does not match the source on CD/DVD). It gives me a filename (e.g. /target/usr/lib/smbcquotas) and the choice to Abort/Retry/Skip.
I click on "Retry" ("Skip" has exactly the same effekt). The progress bar goes up to 38%, and I can hear that files are copied.
Then the system hangs, showing the desktop wallpaper, mouse functioning.
I can only turn it off.

I can try this procedure several times. I even used different disks (one brand new). It always comes to the same end. 
The only thing that changes are the file names ut gives me.

I think that the error message is misleading. Probably there is another error behind the scenes. Can anybody help me and give me another hint than buying new hardware?

Thanks a lot!

---

### Post by Mark Phelps on 2010-05-10
At the beginning of this forum, youn will find a pinned post dealing with Testing Wubi 10.04.  If you read through that, you may find the answer to your problem.

---

### Post by matmuc on 2010-05-10
Thank you for the message, I did not find anything there, that is why I ask for help. If anybody has a hint, please tell me. Please dont give me any tips like changing hardware components, weather conditions, astrology and the like. If it does not work and nobody knows why, I can live with that. I am working with computers for 25 years now.
Thanks a lot.

---

