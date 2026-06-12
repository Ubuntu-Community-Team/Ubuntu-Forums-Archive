---
title: "Upgrade to 10.04 freezes on the Ubuntu screen"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by pmulgaonkar on 2010-07-19
Yesterday I upgraded from 9.10 to 10.04 (32 bit). Everything seemed to go well with no errors until the point where the system needed to restart at the end. After it restarted (and every power cycle since), it gets to the "ubuntu" screen with the moving cycle of square dots underneath, and stays there for ever. The screen resolution is absolutely goofed up, the word Ubuntu cannot be clearly read (looks like it is way overdriving the monitor). All letters seem to have like vertical bars on either side.

Below the Ubuntu and the dots, there appears to be two lines of completely illegible text (they just look like multicolored boxes about the size of characters. 

I tried using the shift key to get to grub and try to boot into recovery mode--no luck. I tried using grub to boot to the previous kernel--no luck. It just sits there at the Ubuntu screen with this weird resolution/appearance.

I can boot from the Live CD and things work fine. I can see the file system, grub files etc. Any help debugging this would be most useful.

I have a related question in case I need to reinstall from scratch--but will ask that on a separate thread.

--prasanna

---

### Post by pmulgaonkar on 2010-07-21
No help?

It looks like the resolution is set weird relative to my monitors capability during the ubuntu splash screen. Is there a way to boot with the live CD and fix the resolution?

--p

---

### Post by euux on 2010-07-24
These symptoms seem familiar. 
I'm using xubuntu but the freeze timing is about the same.
Maybe we can gather some more info, check out **[Can't boot default kernel after upgrading from 9.xx to 10.04 lucid lynx]("http://ubuntuforums.org/showthread.php?t=1535859")**.

---

### Post by pmulgaonkar on 2010-07-26
I got tired of debugging it, and did a clean reinstall of 10.04. That worked out fine. Luckily I have my /home on a  different partition, but now I do have to go through the effort to reinstall all apps.

--prasanna

---

