---
title: "New to this, but can&quot;'t run ubuntu"
date: 2007-10-09
forum: Installation &amp; Upgrades
---

### Post by Devoske on 2007-10-09
Hi, i just installed ubuntu on a hp pavillion 9000 series laptop, and choose the default configuration everywhere. I can see the Ubuntu screen loading, but then it gets stuck. When i ran it in alternate mode, so i could see the steps ubuntu took, the the only thing I could see was wrong was " lp : driver loaded but no devices found " . He stopped loading at " setting up console font and keymap.... " and now I see " root@pcdimitri "

Could anyone help me? Thank you very much !

P.S. : I have Ubuntu 7.04

---

### Post by Pumalite on 2007-10-09
[http://ubuntuforums.org/showthread.php?t=431815](http://ubuntuforums.org/showthread.php?t=431815)

---

### Post by Devoske on 2007-10-09
that thread is closed... the only other open thread is about how to install it.. but I already installed it. The problem is I can't open it :s

Devos

---

### Post by Devoske on 2007-10-09
When I try to run it from the alternate cd, I can see Ubuntu loading screen fully, but then my screen turns black... Anyone that can help me?

---

### Post by Pumalite on 2007-10-09
Have you read this thread?:

[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

---

### Post by Devoske on 2007-10-09
yes, now i'm trying to add a line to the boot menu , saying noapic. But once I added it, i press escape. When i go back to the boot lines then, i can't see that line anymore. Is there a way that i can edit my boot menu and save that new boot menu ? 

Thanks.

---

### Post by Pumalite on 2007-10-09
You can add the boot parameters that work to your /boot/grub/menu.lst in the appropriate line (kernel)

---

### Post by Devoske on 2007-10-09
How do I that ? Sorry but this is really the first time that I work with this and I still have to learn everything

---

### Post by Pumalite on 2007-10-09
Post:

cat /boot/grub/menu.lst

---

### Post by Devoske on 2007-10-09
when i opened it with cat, it just showed the menu, but I couldn't edit it. So I went searching for a working editor and I tried " vi " ... I edited the text and overwrote it, and when I rebooted I had the same problems... When I looked into the menu I saw that the line wasn't added to the list at all, although I had saved it correctly with " vi " . Can anyone help me ?

Thanks

---

### Post by Pumalite on 2007-10-09
'cat' was to post it. If you want to edit it:

gksudo gedit /boot/grub/menu.lst

Make sure you backup first:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back

---

### Post by Devoske on 2007-10-10
Ok, I'm back awake :p

I made the backup first, no problem, but when I try to open gedit, it says " Gtk-WARNING **: cannot open display: "

---

### Post by nawitus on 2007-10-10
man update-grub
sudo nano /boot/grub/menu.lst

Edit the default options commented line, do not edit the list of kernels directly. Then type sudo update-grub and open the menu.lst again to see if the changes are updated. That's the proper way to edit menu.lst.

---

### Post by Devoske on 2007-10-10
I edited the menu properly now, I added the lines " noapic irqpoll noirqdebug " behind defoptions, but still with the same results. When I start in normal mode, I can see the screen loading, but then it turns black and the laptop just stops.

---

