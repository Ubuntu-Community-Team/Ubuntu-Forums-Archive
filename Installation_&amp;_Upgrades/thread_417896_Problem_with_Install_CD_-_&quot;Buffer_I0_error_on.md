---
title: "Problem with Install CD - &quot;Buffer I/0 error on device fd0; logical block 0&quot;"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by sradhakrishna on 2007-04-22
Hi,

I've downloaded the CD image for Ubuntu 7.04 and verified that the MD5Sum was the same as that was mentioned in the [UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes") page.

Burnt the image into a CD, and followed the procedure mentioned in the "MD5SUM on CD" section of [this page]("https://help.ubuntu.com/community/HowToMD5SUM") to verify that the the MD5Sum was ok on the CD too.

However, when I boot from the CD and check for CD defects, the installer gets back with this error - "Buffer I/O error on device fd0; logical block 0". The installation doesn't work too. It throws up similar Buffer I/O errors.

I have tried downloading and burning twice with the same result.:( :confused: 

Any idea how do I go about resolving this issue?? It's become pretty painful downloading and burning this image...

Any help would be extremely appreciated.

Regards,
Radha.

---

### Post by Stelakis1 on 2007-04-22
I had the same problem with my HP nx5000 portable, but don't worry I think this message pops out because there is no floppy drive (at least my HP desn't have one). But the installation continues despite that message (it apears twice if I remember correctly) after a little while. So just go ahead.:)

---

### Post by halo6819 on 2007-04-23
i seem to be having the same problem, but it isnt "just going away" has anyone found out whats going on with this?

---

### Post by timcriger on 2007-04-24
same problem here.... and it just keeps repeating... doesn't move on
help please

---

### Post by AndrewNi on 2007-04-24
I get the message... it spends about 5 minutes going through those errors before continuing. I didn't see them on the final installation.

---

### Post by bdk9246 on 2007-04-25
yep same problem here. except mine was able to run after the error (in a very corrupted state)

---

### Post by ThisPlay on 2007-05-09
I had this problem.

What caused it was the fact that I burnt a CD-ROM ISO over a DVD media.
So... if that's the case, try re-burning it but on a CD-ROM media this time.

Have a great day!
TP!

---

### Post by bdk9246 on 2007-05-10
I've managed to fix this problem. 
Hope this helps!
Basically, I had recently removed my floppy drive (fd0) and had not turned it off in the BIOS, 
doing so fixed the problem.

---

### Post by helpdeskdan on 2007-08-18
Thanks for the tip - playing with BIOS helps.  I set the boot order, leaving out the floppy all together, but I think what really helped was the setting to disable hot swapping by setting "restart only" for the drive bay.  I still got some hdc errors, but they only mildly slowed it down. 

For the rest of you, if you get this error (you can only see it if you hit ctrl-alt-F1) and you are not comfortable with bios, go run some errands and come back.  By the time you come back, it should be booted up.  I don't think it persists after install.

---

### Post by ncsubowen on 2007-10-28
I'm getting a Buffer I/O error on device fd0, logical block 0, and it won't let me go anywhere. I leave it and that error pops up for a long time, then the screen goes blank and I don't get anything after leaving it for ~an hour. This is my first foray into Linux (as a fed up Windows user), so any possible assistance would be most appreciated.

I'm running 2 gigs of ram on a Core 2 Duo @ 2.13 GHz and an Asus Mobo, I've got an IDE DVD-RW drive and a SATA hard drive. I can post any additional information if needed. 

Note: This is a clean install on a brand new hard drive.

Also getting: ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen

---

### Post by chchandler on 2008-04-30
> **ncsubowen said:**
> I'm getting a Buffer I/O error on device fd0, logical block 0, and it won't let me go anywhere. I leave it and that error pops up for a long time, then the screen goes blank and I don't get anything after leaving it for ~an hour. 


Well, not that I know what I'm doing... but I had that happen to me.  Try Ctrl-Alt-f1, which will get you into a terminal screen.  Then try Ctrl-Atl-f7, which for me brought up the GUI.

---

