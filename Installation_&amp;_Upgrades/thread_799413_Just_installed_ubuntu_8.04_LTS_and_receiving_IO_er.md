---
title: "Just installed ubuntu 8.04 LTS and receiving I/O errors during startup"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by KB918 on 2008-05-19
Just as the title says, I installed Ubuntu under windows xp and restarted without the disk in the drive.  Once prompted to select an OS, I selected Ubuntu and the splash screen showed in a few seconds later with the progress bar.  After about a minute or two, the screen changed and showed command lines saying there are errors  in regards to I/O errors and would lists more and more for about 10 minutes then go to a black screen and sit until I hit restart.  I am new to Linux and this is my first try at this.  I got Ubuntu Live to work but a permanent install isn't not working at all and I am not sure how to fix this issue.

"KB"

---

### Post by iaculallad on 2008-05-19
What types of I/O errors was in your screen display? Post a more complete detail with regards to the I/O problem so we could trace what problems are occurring.

---

### Post by KB918 on 2008-05-19
I boot up my machine as normal and when it prompts me to choose an OS, I select Ubuntu and the splash screen comes up as normal with the progress bar.  After about a minute or two, that goes away and then shows a command screen that I myself cannot enter anything on but it shows

[     188.214662] Buffer I/O error on device fd0, logical block 0
[     200.351004] Buffer I/O error on device fd0, logical block 0
[     200.883308] Buffer I/O error on device sdb1, logical block 156284912


It continues on and on in the same fashion getting up in the 450.00000 or so for a few minutes then just goes to a black screen with a letter curser blinking as it does in command but I can not do anything but turn the power off.  I assume that this has something to do with my HDD..??

"KB"

---

### Post by VMC on 2008-05-19
You can try floppy=off for the kernel, but that's no cure. Is this Toshiba laptop, or IMP Thinkpad by chance?

Did the cd/dvd install go without a hitch? No errors.

---

### Post by KB918 on 2008-05-19
Yea, I ended up realizing that the floppy needed to be disabled.  No, haha.  Its a custom built computer.  I end up with this now that they floppy is disabled.  No more error messages though.  :)

BusyBox x1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

"KB"

---

### Post by epidemiks on 2008-05-20
I get "Buffer I/O on device sdb, logical block 0", & not getting any love in my thread :(

---

### Post by iaculallad on 2008-05-20
> **epidemiks said:**
> I get "Buffer I/O on device sdb, logical block 0", & not getting any love in my thread :(

Just hoping you could resolve your problem by relating with this [thread]("http://ubuntuforums.org/showthread.php?t=276930").

---

### Post by epidemiks on 2008-05-20
> **iaculallad said:**
> Just hoping you could resolve your problem by relating with this [thread]("http://ubuntuforums.org/showthread.php?t=276930").

there are some new things to try there [-o<, thanks!

---

