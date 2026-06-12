---
title: "[SOLVED] How do I change my grub with the Gutsy?"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by LitusMayol on 2007-10-21
Hi everyone!

I've changed my Feisty Fawn for the Gutsy Gibbon. (So easy installation process!)

First of all my Kopete doesn't works. But i've read that is a recognized bug, so no problem with it. 

Second: my bug. I've installed That-OS-that-musn't-be-named (Win... :S lol ), becaus i need it for AutoCAD and some of my family members use it aswell. But it hides the grub and i can't choose the Os. In the past i changed it by going to /boot/grub, and changin' the "menu.lst". But now the folder /boot doesn't contain the /grub :S . So, right now, i don't know how to change my grub! 

Can anyone help?

Thanks!

---

### Post by nosneros on 2007-10-21
Just to clarify, does your computer boot straight into windows? If so, I think that means you overwrote your master boot record (MBR) with the windows bootloader when you did the windows install. To fix it, if you have the Kubuntu CD (I think it's a liveCD), you can just boot from that and get into a command line terminal and use the grub utility to reinstall your grub. I don't remember the commands off the top of my head, but search around for "grub" and "install" and there should be something on the forums.

---

### Post by forestpixie on 2007-10-21
have a look [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

alternatively [supergrub]("http://supergrub.forjamari.linex.org/") seems to work fine at restoring grub, download and burn as an iso and boot with it

---

### Post by LitusMayol on 2007-10-21
Thanks both!

I'll try it, if it doesn't work i'll post it here.If it works i'll thanks you again, ok?

let's try!!

---

### Post by LitusMayol on 2007-10-22
Done it!

Great Forestpixie, the first web you gave me is so easy to understand.Newbies thanks it! :P lol I'm a REAL NEWBIE. So, thanks.

Also thanks to you nosneros. ;)

Thanks guys!

---

### Post by forestpixie on 2007-10-22
great glad it helped - it certainly has helped me , I'm new here too - the forums are basically what kept me here :D

---

