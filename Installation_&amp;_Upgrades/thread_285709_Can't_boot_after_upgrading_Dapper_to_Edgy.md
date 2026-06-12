---
title: "Can't boot after upgrading Dapper to Edgy"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by krsnendu on 2006-10-27
I had no problems upgrading from Breezy to Dapper but Dapper to Edgy has left me high and dry.
](*,) I did the commands given on the website to upgrade from Dapper to Edgy. Everything seemed to go fine until I tried rebooting. It shows the Ubuntu logo and the progress bar, but before the bar reaches the end of the screen it starts flashing all kinds of garbage.
I tried Alt-Ctrl-F2, Alt-Ctrl-Backspace and Alt-Ctrl-Del. Nothing does anything. The screen just keeps on flashing.

What should I try.
I tried SSH from another computer but I couldn't get in.
Is there any way to do an interactive boot?

---

### Post by frodon on 2006-10-27
What happen if you try the recovery mode and did you try to boot both generic and i386 kernels ? I may be able to help you but i need some error messages to see what the problem is.

---

### Post by krsnendu on 2006-10-27
How do I run recovery mode?

---

### Post by krsnendu on 2006-10-27
I figured out how to get into recovery mode. "Press esc at grub boot time" 
I got these messages when trying to "startx"
dlopen:/usr/lib/xorg/modules/extensions/libGLcore.so undefined symbol: __glXLastContext
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(EE) Failed to load module "GLcore" (loader failed, 7)

Fatal server error:
could not open default font 'fixed'
XIO: fatal IO error 104 (Connection reset by peer) on X server":0.0" after 0 requests (0 known processed) with 0 events remaining.

Does this help?

---

### Post by frodon on 2006-10-27
Ok try a :
```
sudo depmod -ae
```and a :
```
sudo aptitude reinstall linux-restricted-modules-2.6.17-10-generic
```Then reboot

---

