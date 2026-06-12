---
title: "Cannot log in after initial install of Ubuntu 6.06.1"
date: 2006-12-25
forum: Installation &amp; Upgrades
---

### Post by jerrynewt on 2006-12-25
Just finished installing Ubuntu 6.06.1 over my old Red Hat 2 OS and everything went just fine, until I removed the install CD as instructed and the system rebooted. During install I did the username and password deal just fine--only thing is I did not write them down and kept getting Christmas phone calls during installation. Well you know what's next--I forgot the username and password. Anyway, do I run the install CD to correct this problem or is there another way to get around this? As you can see I am a fresh faced genuine dyed in the wool noobie, but I am really excited about the new OS. Any help would be appreciated--Thanks and Merry Christmas to all.   Lost in Texas--still!!

---

### Post by thinklife on 2006-12-26
Q: I am a complete moron and forgot my password. How can I get back into my system?
(Hey, YOU forgot it, I think that gives me the right to do some degrading before letting you back in!)

A:
1. Turn off your computer.
2. Tap it 3 times
3. Say your favorite magic word.
---- If that doesn't fix your problem, do the steps below...
4. Turn your computer on.
5. Press ESC at the grub prompt.
6. Press e for edit.
7. Highlight the line that begins kernel ........., press e
8. Go to the very end of the line, add rw init=/bin/bash
9. press enter, then press b to boot your system.
10. Your system will boot up to a passwordless root shell.
CAUTION: This is a FULL ROOT SHELL! You can damage your system if not careful!
11. Type in passwd <username>. Set your password.
12. Type in reboot.
NOTE: steps 1-3 may help at this point.
13. Bow down to me....


PS: I used windows to type this though, so i wont remember this link cauz i boot into windows every 10 years 8)

---

