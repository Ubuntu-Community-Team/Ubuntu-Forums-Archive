---
title: "Mounting problem with Live CD"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by Ross92 on 2010-12-08
I had all kinds of trouble trying to install Ubuntu with the wubi installer last night and i gave up.  So, today i made a live disk.  When it starts, it asks what language, then if i want to install.  It then takes me to the screen that says ubuntu and has the little white and orange loading dot things.  At the bottom though it says 

"Error Mounting /Kernel/debug." 
and under that 
"Press s to skip mounting or press M for manual recovery"

So I've tried skipping but that didn't work. When I press M it brings up a maintenance cmd line.

Anyone else have this problem or know what i should do?

Thanks in advance!

---

### Post by ajgreeny on 2010-12-08
Check the live CD is good if it's one you burned yourself.  There is a menu that appears after the language selection, I think, which gives "Check install Media" or some such wording.  If any errors are found, burn again, but make sure your ISO file is good first by checking the md5sum.

---

### Post by Ross92 on 2010-12-09
What is the md5sum?...  I've tried having it check the disk for errors and it just locks up.  This is the third disk i've burned.

---

### Post by ajgreeny on 2010-12-10
The md5sum is an alphnumeric which will change if the downloaded ISO file (or any other file) is not as it should be and can therefore be compared with published lists of md5sums for the ubuntu isos available here:-
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
You can get info on how to do this in windows and other OSs here:-
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

The fact that your system locks up when you try to do anything with the CD suggests it is not a good burn.

---

