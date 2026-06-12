---
title: "Win 7 Dual Boot"
date: 2012-07-31
forum: Installation &amp; Upgrades
---

### Post by capemayal on 2012-07-31
My System:
Win 7 64-bit
Ubuntu 12.04 LTS
 
Installed using WUBI.
 
When starting computer, the screen to choose OS flashes on screen and goes away. Computer loads Ubuntu.
 
I need to get into Windows to do some maintenance.
 
I am unable to start Windows - Can't get to safe mode - as the screen to choose OS stays on for, at best, a second.
 
I've tried using F8 during the booting process, but that doesn't work because I haven't started loading Windows.
 
I have wine installed. I can read the window's directories, etc.
 
Any help would be appreciated.
 
Al

---

### Post by levlaz on 2012-07-31
This sounds like a grub issue - been having a lot of posts about this today. 

oldfred pointed out there is a boot utility. Give it a try it may be just what you need. 

[https://help.ubuntu.com/community/Boot-Repair ]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by QIII on 2012-07-31
Not sure if bootrepair works with a WUBI install, so read carefully.

You could simply change the GRUB timeout.

In the Tutorials & Tips forum, there is a "GRUB 2 Basics" how-to on about page 6.  There are instructions there for extending the GRUB timeout.

---

### Post by bcbc on 2012-07-31
Yeah grub won't help. It's the windows boot manager that you need. 

Did you modify the timeout to make it shorter and set Ubuntu as the default? This can cause the problem.

I believe the only way to fix it is to boot from a Windows 7 repair CD and change the timeout:
```
bcdedit /timeout 10
```

---

### Post by QIII on 2012-07-31
Well, bcbc, it is clear that the few times I tried WUBI a long time ago did not leave any useful memories stuck in my brain.  I had forgotten that it changes the Windows boot screen.

Ignore an old man.  Carry on!

---

### Post by bcbc on 2012-07-31
> **QIII said:**
> Well, bcbc, it is clear that the few times I tried WUBI a long time ago did not leave any useful memories stuck in my brain.  I had forgotten that it changes the Windows boot screen.

Ignore an old man.  Carry on!

haha, no that would be rude.

Wubi has its oddities...

---

### Post by capemayal on 2012-08-01
Thank you all.
 
bcbc your solution worked.
 
Apparently, the boot order and timeout had changed.  Why, I don't know.  But, the solution did work.
 
Thanks,
Al

---

