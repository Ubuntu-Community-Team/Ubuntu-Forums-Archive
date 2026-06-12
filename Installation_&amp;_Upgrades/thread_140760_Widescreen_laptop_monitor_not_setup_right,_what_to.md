---
title: "Widescreen laptop monitor not setup right, what to do?"
date: 2006-03-06
forum: Installation &amp; Upgrades
---

### Post by Arkolm on 2006-03-06
Hello again everyone! I have yet another problem that I can't seem to solve with the search function on google and the forums, though I am sure it's nothing new and I'm just slow. Anyway, I installed the newest version of ubuntu on my new laptop, dual boot with xp home. When ubuntu starts up after it loads everything I just get a grouping of lines, sort of light blue on a blue background, horizontally on the top of the monitor and vertically down the middle.

The laptop is a HP zv6200 widescreen. I had to use linux vga=771 to get to be able to see the install program, so I figure it's a similiar setting I have to set to get the installed version to be viewable. I tried a few things, but I found that after a normal boot up I couldn't get another console with ctrl + alt + f1, and I Was forced to ctrl alt del to reboot and go into recovery mode.

In recovery mode I tried using 

sudo dpkg -reconfigure xserver-xorg

I went through it and found nothing that I connected to widescreen monitor. It detected my monitor as generic, and I think that sounds wrong, but I don't know enough to know what to choose. It detected my video card fine. After it all went through I tried to use

sudo int 6

to reboot, as I was instructed, and was told no such command found, perhaps because of recovery mode? Anyway, that's about where I'm at, any suggestions?

Thanks!

---

### Post by Arkolm on 2006-03-07
No suggests eh? Is there some other setting I should have used for setup to prevent this?

---

