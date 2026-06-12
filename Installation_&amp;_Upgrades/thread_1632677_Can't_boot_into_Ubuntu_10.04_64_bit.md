---
title: "Can't boot into Ubuntu 10.04 64 bit"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by mj_mohsen on 2010-11-28
Hi

Last night I upgraded my ubuntu using the update manager thing, and now I can't boot into it. I'm using a dual boot Windows 7, Ubuntu 10.04 64 bit configuration. when I select Ubuntu from windows bootloader, it tries to load Grub, some NTFS message splashes and then restarts. I can boot to Windows though. searched the forums, couldn't find the solution. would appreciate a quick help. :)

---

### Post by dino99 on 2010-11-28
[https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu%20CD%20or%20ISO](https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu%20CD%20or%20ISO)

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by mj_mohsen on 2010-11-28
what should I do next? after I make the USB?

---

### Post by Rubi1200 on 2010-11-28
Hi and welcome to the forums :)

Use a LiveCD to boot the computer and choose to try not install Ubuntu.

Click on the boot info script link at the bottom of my post and follow the instructions there.

Post the results back here please.

Thanks.

It sounds as if you have a Wubi install which failed because of some recent updates to the GRUB bootloader.

However, we need to make sure that is the case, and that is why we need the results of the script.

---

### Post by mj_mohsen on 2010-12-09
I still haven't done what you proposed, but I have a question. If I  uninstall ubuntu from inside windows, and install side by side windows  not from inside of it; will I still experience these kind of errors and  GRUB problems? this is not the first time I've had problems with GRUB.  it once even stopped my access to windows, which is very important for  me because of my job. can you guide me with that?

---

### Post by Jay Car on 2010-12-09
If what you already have is a wubi installation of Ubuntu, try this link:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

I bet it can help you get the problem sorted out.

:)

---

### Post by mj_mohsen on 2010-12-09
Thank you very much Jay, I already found my problem in the list but haven't tried the solution. anyway, I'd like to know how different is the fresh install (alongside my existing windows of course) from the wubi install? I've heard the performance differs, and wubi is meant to be for trying ubuntu only, and it cause lots of problems, especially with GRUB and its updates. 

It's ok for me to uninstall my wubi installation, and install ubuntu freshly as my second OS, but as long as it doesn't harm my windows (I need to be 100% sure). could you help me with that?

---

