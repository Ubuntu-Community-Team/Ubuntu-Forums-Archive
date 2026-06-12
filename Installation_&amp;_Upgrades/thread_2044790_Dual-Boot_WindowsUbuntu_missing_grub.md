---
title: "Dual-Boot Windows/Ubuntu missing grub"
date: 2012-08-20
forum: Installation &amp; Upgrades
---

### Post by MrDongji on 2012-08-20
Hi there,

Complete beginner with Linux here who recently dual-booted Windows 7 with Ubuntu on two hard drives (one solely for windows, one for Ubuntu).

My boot priority is set to 
(1) HDD with windows 
(2) HDD with Ubuntu & partitions. 
(3) CD-ROM

Now, I have never even booted/used Ubuntu yet (with the exception of the installation process).

From what I can understand from googling, this grub menu can be missing for a variety of reasons. 

-Can try booting from 2nd HDD
-Could try ```
sudo update-grub
``` 
-Somehow get grub to be in sda

[S]I haven't touched Ubuntu since the installation[/S] 

Oops, I realized I had to enable kernel options through F6 nomodeset when I first installed Ubuntu. I have a Nvidia graphics card with the latest R300 drivers if that matters.

Windows is my OS every time I restart. I've tried pressing F8 or holding the shift key as well.

Thanks for the support guys, looking forward to getting this thing up and running.

**Update:** Successfully loaded Grub 1.99 after switching boot priorities; however, I'm unable to boot Ubuntu from grub. I am left with an empty pink screen.

---

### Post by darkod on 2012-08-20
If you needed nomodeset during install you will need it again on first boot. When the grub boot menu shows highlight the ubuntu entry and press 'e' for edit. That will display the boot lines.

Using the arrows keys move the cursor towards the end of the line starting with linux. Add nomodeset after the 'quiet splash'. Press Ctrl + X or F10 to boot.

Once it boots successfully, open Additional Drivers and activate the video driver suggested. Usually that should sort out the problem permanently.

If it doesn't, there is a procedure to make the nomodeset permanent. The above procedure with editing the boot lines in the grub menu is temporary for that boot only.

---

### Post by MrDongji on 2012-08-20
> **darkod said:**
> If you needed nomodeset during install you will need it again on first boot. When the grub boot menu shows highlight the ubuntu entry and press 'e' for edit. That will display the boot lines.

Using the arrows keys move the cursor towards the end of the line starting with linux. Add nomodeset after the 'quiet splash'. Press Ctrl + X or F10 to boot.

Once it boots successfully, open Additional Drivers and activate the video driver suggested. Usually that should sort out the problem permanently.

If it doesn't, there is a procedure to make the nomodeset permanent. The above procedure with editing the boot lines in the grub menu is temporary for that boot only.

Worked like a charm.

So far so good, drivers are loading and booting should be good now.

Appreciate your help, thanks for the lesson.

---

