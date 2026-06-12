---
title: "Crash after &quot;install in text mode&quot;"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by LieToPurify3 on 2007-07-04
I had Ubuntu installed on an old Sony Vaio, and wanted to reinstall it because I suspected it was a bad install, and now whenever I try to install any version of Ubuntu or Xubuntu, after I hit "install in text mode", I get this black screen with code all over it and at the bottom it says "run_program: '/sbin/modprobe' abnormal exit".   I'm not sure if this means anything to anyone, but can someone help me!?  Thanks!

---

### Post by Pumalite on 2007-07-04
If this is a clean install of Ubuntu only, the, prepare the drive first with Gparted:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

Make one large partition formatted ext3. Then install.

---

### Post by family on 2007-07-04
My PCs got nothing to do with Vaio, it's a Pavillion. But the text mode worked great for me! I'm a total nube, so don't take me too seriously! --- All I'm saying is that when I put in the 6.06 CD Canonical sent me, all my PC would do is restart. Regardless of pressing "Start or Install", or going down to "Boot from 1st Hard disk" and entering live acpi=off. So, after trying for a month:(, I accidently pressed Esc instead of F1 (for help, again). So it took me to the text mode. From there, I entered live acpi=off command, and boom. No seriously, it totally took off!!! I've been a blind (not in the literal sense) XP user forever, but wow, Ubuntu schools XP's posterior into the ground. :o
From there, I shut down, burnt myself a copy of 7.04, rebooted, and popped it in. Then I went to the text mode, entered the famous command, and I was back at the new live mode. I chose Install, and let it take the largest continual free space, so 50 Gigs. And I'm writing this from Ubuntu now!!:p

---

### Post by az on 2007-07-04
> **LieToPurify3 said:**
> I had Ubuntu installed on an old Sony Vaio, and wanted to reinstall it because I suspected it was a bad install, and now whenever I try to install any version of Ubuntu or Xubuntu, after I hit "install in text mode", I get this black screen with code all over it and at the bottom it says "run_program: '/sbin/modprobe' abnormal exit".   I'm not sure if this means anything to anyone, but can someone help me!?  Thanks!

Can you run the memtest option?  This sounds like a hardware issue.

---

### Post by LieToPurify3 on 2007-07-04
I really can't imagine what is wrong.   I think i cleaned out the system with Gparted, and I still either get that error, or something ending with "imPS/2 Generic Wheel Mouse as /class/input/input2".  The system used to work.  The machine used to run winxp, but the HD was corrupted and the computer didn't work, so i bought a brand new 80 gb hd and installed ubuntu perfectly.  But now when i'm installing it again, i get these errors.  I ran memory test, but what should i tell you about it?  I'm not sure how to read it.

---

### Post by az on 2007-07-04
> **LieToPurify3 said:**
> I ran memory test, but what should i tell you about it?  I'm not sure how to read it.

On the top-right, you see the progress of each scan.  You should leave it as it goes through many passes (hours).  About mid-screen downwards are where the errors are shown, when detected.  Any errors?

---

### Post by LieToPurify3 on 2007-07-05
I left my house right after I started running the scan on wed.  It is now thursday at 3:40 and sinc e it is sitll going and says pass - 91, i'm guessing it ran the test that many times.  It came up with no errors.  Any other ideas?  Once in a while, it wont give me that page with teh code on it, but when i get to installing the actual system it gives me errors, making it seem like the cd is defective, but i know it isn't. ive burned quite a few, used ones that have worked before, and even downloaded a new iso and burned several cds from that.

---

### Post by LieToPurify3 on 2007-07-06
now when i tried my edgy alt cd, it gets to the "select and install software" part, but gets stuck at 6%, and then tells me there was an error during the process and that i can go back to the list and choose where i want to restart hte install.  So i keep going back to the "select and install software" part, but nothing changes.  I keep getting this error.

---

### Post by Pumalite on 2007-07-06
Have you done ckecksums on your isos (Md5)? Have you burned at 1x? Have you checked the CD for corruption before install? If the answer is 'yes' to all those, then you should consider hardware: a bad burner? difficult graphics card?Motherboard? Connections ( after all is an old comp).

---

