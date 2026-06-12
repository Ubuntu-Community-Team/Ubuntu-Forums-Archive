---
title: "cannot boot to Ubuntu after installing it using wubi"
date: 2012-12-01
forum: Installation &amp; Upgrades
---

### Post by imke on 2012-12-01
Hi all,
I'm a total newbie in such stuff, but recently I got a Samsung 100NZC with win7 starter on board and trying to install Ubuntu on it. I used Wubi, because my netbook cannot be booted from USB, and Wubi said after all the win part: lets reboot... and after that I cannot boot Ubuntu: it just stops booting on random places like "saving log messages" or "saned disabled" or somewhere else - once I even saw an Ubuntu logotype on purple screen, and more white-on-black stuff after that - and that's all. It's not freezing I believe - it reacts nice to power button, immediately starts to write about "stopping" this and that.
Googled, found recommendation to boot back in windows and check root.disk file - checked, I have one and have no idea what to do now - please help :(

---

### Post by Resistent on 2012-12-01
Hi !

I am not sure, maybe you have also the problem of compression of the wubi folder..
Once I wrote this post:

> I tried to install Ubuntu with the Wubi Installer. 

Rebooting, I got the "Uncompression Error...System Halted" message.
The problem was: The harddisk was adjusted to "compress to save space"  as I could see in Windows Explorer. (properties of harddisk). This  affected also the Ubuntu folder on the harddisk. After I unchecked  "compression" for the Ubuntu folder in Windows Explorer, I could restart  and landed at the "Bash promt". Then I installed Ubuntu with Wubi  installer again, and it worked (because Windows did not compressed the  Ubuntu folder on the harddisk).

---

### Post by imke on 2012-12-01
> **Resistent said:**
> I am not sure, maybe you have also the problem of compression of the wubi folder..
I see no errors actually at any stage - it just stops booting, and that's all. But thank you :)

---

### Post by oldfred on 2012-12-02
Are you sure you cannot boot from a USB flash drive? Or do you have a CD? Almost all systems in the last 6 years have a way to boot as that is the only way to fix them, if more than minor issues.

Even if just booting Windows you have to have a USB bootable repair  flash drive. And if attempting multiple systems you will eventually need  to boot a repair flash drive for either Windows or Ubuntu.

If not I would not plan on doing much and learn how to remove hard drive so you can fix from another Windows/Linux system.

---

### Post by imke on 2012-12-03
I'm sure, trust me - and even Samsung guarantee service is pretty sure it doesn't work.
Anyway I'm not sure I understand why I cannot count on the tool designed exactly for my situation - to install Ubuntu from Windows. That's what it supposed to do, right? And that's what I'm trying - I see no excusable reason for its fail.

---

### Post by oldfred on 2012-12-03
Your model does not exist on USA Samsung site so I cannot see details of system.

May be video or other boot parameter.

       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by imke on 2012-12-06
Here are all the details: [http://notebook.tech-details.com/Samsung_100NZC/#spec](http://notebook.tech-details.com/Samsung_100NZC/#spec)
I'll try to look in threads, thank you!

---

### Post by oldfred on 2012-12-06
Most Intel Video, just works, but some need extra parameters to get going. Or it just can be other boot parameters.

Hard to check what errors without a liveCD/Flash drive way to check system.

---

### Post by Tumshukuru H. Mhalila on 2012-12-06
You just use an external DVD ROM to repair your Windows with
```
bootrec/fixmbr
bootrec/fixbooter
```

then look for Ubuntu CD and enjoy the installation through your External DVD ROM enjoy!:)

---

### Post by imke on 2012-12-09
> You just use an external DVD ROM to repair your Windows
Ok, my letters just weren't big enough: I CANNOT BOOT FROM ANY USB DEVICE - and my Windows is ok, thank you.

---

### Post by imke on 2012-12-09
> **oldfred said:**
> Most Intel Video, just works, but some need extra parameters to get going. Or it just can be other boot parameters.
Hard to check what errors without a liveCD/Flash drive way to check system.

I know, I know :(
But that's what I have. I'll try to play with boot parameters now, maybe it will help :(

---

### Post by imke on 2012-12-09
All the same with nomodeset added to wubildr-disk.cfg: the last string I saw was "saned disabled: edit /etc/default/saned", and nothing after that - just cursor blinking :(

---

