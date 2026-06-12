---
title: "Editing NTLDR to recognize Ubuntu"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by komputerkurt on 2010-10-22
Hi guys, today I just installed Windows XP professional after removing my low-space C drive and thus making my E drive with ubuntu C and now running XP pro. The problem is that now it doesn't have a option to boot to ubuntu. Using msconfig ([http://vlaurie.com/computers2/Articles/bootini.htm](http://vlaurie.com/computers2/Articles/bootini.htm)) I am able to edit the boot.ini safely. So I'm wondering what I'd put in and edit... I don't know where the directory should lead to, theres one folder with a disk, one with mbrs, etc. Can you guys please help me?

---

### Post by Rubi1200 on 2010-10-22
Firstly, I wouldn't start messing around with Windows boot.ini files (or any other Windows file) because Ubuntu does not start; just asking for trouble in my opinion.

Second, please use a LiveCD and post the results of the boot-script linked at the bottom of my post.

That information will help us determine what is going on and make offering solutions a lot easier.

Please wrap the text with the # tag when posting back.

Thanks.

---

### Post by komputerkurt on 2010-10-22
XP removed Ubuntu from the boot.ini
I can use msconfig to fix the boot file, I just need to know what code to put in. Ubuntu would work if it could boot but I have no way of making it boot. Im not sure if I have a live disk but if I can find one (it'll be 10.04) then I'll do this I guess.

---

### Post by Rubi1200 on 2010-10-23
If this is a Wubi install (?), take a look here:
[https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu)

---

### Post by komputerkurt on 2010-10-23
So chkdsk /r will find ubuntu and automatically add it?

---

### Post by kansasnoob on 2010-10-23
We really need to see the output of the Boot Info Script as Rubi1200 requested:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

You can run it using any Ubuntu Live CD. 

Alternative instructions:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Otherwise we don't know if this is a true dual-boot or a Wubi install, if it's the prior it would be much simpler to use grub to boot both OS's.

If it's the latter that's a whole different story.

---

### Post by komputerkurt on 2010-10-23
I used wubi to install Linux. I'll see what I can do today.

---

