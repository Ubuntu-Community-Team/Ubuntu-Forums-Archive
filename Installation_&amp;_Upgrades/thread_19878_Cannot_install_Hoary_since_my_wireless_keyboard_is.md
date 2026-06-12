---
title: "Cannot install Hoary since my wireless keyboard is not recognized"
date: 2005-03-14
forum: Installation &amp; Upgrades
---

### Post by BaffledMollusc on 2005-03-14
I've just tried to install the Hoary preview release and failed at the first hurdle. 

I have a Logitech wireless keyboard and mouse. When the initial Ubuntu splash screen appears you have to press enter to continue, but the installer doesn't register my keyboard. I find this quite odd, because even the BIOS recognizes the keyboard (i.e. I can get into it by pressing Delete and then make changes).

There seem to be a couple of other people with the same problem:

[www.ubuntuforums.org/showthread.php?t=19057&highlight=wireless+keyboard](www.ubuntuforums.org/showthread.php?t=19057&highlight=wireless+keyboard)
[www.ubuntuforums.org/showthread.php?t=276&highlight=wireless+keyboard](www.ubuntuforums.org/showthread.php?t=276&highlight=wireless+keyboard)

One of them solved the problem by enabling "USB keyboard" in the BIOS, but this option doesn't exist in my BIOS, and since the BIOS is happy with my keyboard anyway, I don't think this is the problem.

Anybody have any other suggestions (except getting a PS2 keyboard and mouse, installing Ubuntu, and then hoping the full installation will see my kb/mouse. I'll try this approach as soon as I can get hold of a PS2 keyboard).

Any advice happily accepted...

---

### Post by BaffledMollusc on 2005-03-14
Sigh. So I'm an idiot. There was indeed an obscure corner of the BIOS where you can specify that you want the BIOS to handle legacy USB keyboard and mouse input rather than letting the OS do it. I made this change, and now the installer recognizes the keyboard.

Problem solved. Now to tackle the wireless network...

---

