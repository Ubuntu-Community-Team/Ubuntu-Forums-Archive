---
title: "bad installation?"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by rdemel on 2008-11-01
Hi There,

I seem to be having trouble getting into ubuntu.
Here is how I tried to install it:
I have windows xp. 
I downloaded the ubuntu image (ubuntu-8.04.1-desktop-i386.iso)
I used daemon tools to mount the image on to a virtual drive. 
I installed ubuntu (i think i picked install inside windows)to a usb external hard drive (300GB)
I began the installation in the morning and left it.  At the time I left, the computer had restarted, the ubuntu splash screen had come and it was on a screen I believe with the ubuntu background with a widow showing some sort of progress.
When I returned in the afternoon, it was at the windows xp login screen.
At this time using windows was very slow.  I tried to reboot into ubuntu but all of the 3 ubuntu boot options in the menu, take me to a built in shell screen.

I tried using add/remove programs to try removing and reinstalling, but it wouldn't do anything.  I tried running the ubuntu image from my virtual drive again but it would only run if by usb hard drive in which I originally installed ubuntu is disconnected.
Now windows is running at normal speed, my usb hard drive has 14.6Gig used for ubuntu.

Can any one suggest how I should proceed?

Thanks a lot!
Ryan

---

### Post by zwygart on 2008-11-05
Probably your GRUB is setted wrong.
Where did you installed GRUB? It's not matter if you don't know.
The shell that you see is it the GRUB shell? They look all the same thing?
If yes try these things at the shell( you cannot lose a lot at this state)

root (hd0,0)                      Change the 0 by other values 0 to 4 for the first one and 0 to 8 or more for the second one.
If some of the number write ext or linux partition, then we are on a good track.
type the successful numbers then
load vmlinuz
initrd initrd           may be you have to add .gz
boot

What are the folders at the root of your ubuntu? Type these names instead of vmlinuz and initrd. 

On the ubuntu on your harddrive, what are the last lines of /boot/grub/menu.lst

---

