---
title: "Unviewable splash screen, part Deux"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Serenitude on 2007-10-19
An update to the RC broke the splash screen on my 15 inch LCD. Bug report filed, other users had the same problem. Splash screen on LiveCD works fine. Installation goes great. Reboot. Grub boots, and works. Then I get "Unable to display this video mode". Letting it run for a bit eventually puts me at the (visible) log-in screen, where everything works OK afterwards.

Navigating to usplash.conf, I see it's set to 1280x1024, or something. I set it to my monitor's native 1024x768, save, and reboot. Still no splash screen or text, just the same "Unable to display this video mode" until I get to the X server.

This irritates me, as it was a known bug before Gutsy was released :-( I had a thread about it in the old Gutsy Beta forum. I wasn't the only one with this issue.

I can't believe it's not fixed for the gold master.

Anyone have any idea on how (if?) this can be fixed? It just inspires me with no confidence that if they can't even fix a known splashy error, what else may be lurking, borked, under the hood? :-(

---

### Post by divague on 2007-10-19
I had the same problem, i installed startupmanager and there i configured usplash. it worked for me

---

### Post by Serenitude on 2007-10-19
Worked here also. This solves the issue, for now

---

### Post by pacsum on 2007-10-20
Here's the easier fix:
> To fix the no boot splash I did the following

1) Change the resolution in /etc/usplash.conf to 1024x768
2) Add vga=791 to the kernel line in /boot/grub/menu.lst
3) sudo update-initramfs -u -k `uname -r`
Thanks to **fcumok**

---

