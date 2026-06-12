---
title: "console"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by hirohitosan on 2008-03-07
Hello guys. Maybe this thread was discussed before but I can't find it. My console in text mode looks odd. Very big fonts. I tried to modify /boot/grub/menu.lst and I add vga=791 or 790, 788 but no results. 
First: where in the config file to add vga mode?
All that I want is a decent old fashion console in text mode. In LILO is noframe buffer or something like this
Also during booting my screen is complete blank

And how can I reduce the booting time. It takes a lot of time and I don't know what's happening since my monitor is blank.

Thanks a lot
have a nice evening:popcorn:

---

### Post by jahvascriptmaniac on 2008-03-08
Wow, you have a lot of questions :-p

If I'm not mistake, the vga option should be added at the end of the "kernel=" line in grub's menu.lst, if it doesn't work, google is your firend. And also, advice : copy the menu entry you're modifying below it and change the names, so you'll have two entries : [your entry]_modified and [your entry]_original, this way you'll still be able to boot even if you mess things up...

to have everything printed during boot, delete the "quiet" and "splash" options from the "kernel=" line in your menu.lst

to reduce your booting time, search for a tool that allows you to change the services that are loaded at startup. I'd go straight to the ubuntu docs if I were you...

---

