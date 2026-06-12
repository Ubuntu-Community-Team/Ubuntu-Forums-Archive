---
title: "Failed Installation, Black Screen."
date: 2012-08-15
forum: Installation &amp; Upgrades
---

### Post by HSovieticus on 2012-08-15
I tried installing ubuntu. It told me something about partitions and said that i had to restart before continueing, and so i did. Now i have a blank screen with a flashing underscore in the top left corner. What do i do?

---

### Post by HSovieticus on 2012-08-15
Ya. I'm really worried that my netbook is broken now.

I kindof needed it to continue working,
as i don't have money to replace it.

I had windows 7 professional, but i wanted to use linux instead.

So, if someone knows what is going on..

EDIT: i should mention that putting my windows 7 cd in does nothing either. same screen.
PLUS: the computer is an ASUS Eee PC, if that matters.

---

### Post by oldfred on 2012-08-15
Did you totally overwrite Windows or install side by side to dual boot?

If you hold shift key down from BIOS until menu appears, do you get the menu? Can you boot recovery (second line in menu)?

Often a video issue. I am not up to date on all the Eee issues, but have seen other posts with some model of Asus Eee.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by HSovieticus on 2012-08-15
I overwrote windows, i don't even think that ubuntu finished installing.

I've held down the shift key and TAB and f12,
nothing happens.

But i do get some very transient strings of numbers and a logo,
and then i get the black screen with the flickering underscore.

---

### Post by oldfred on 2012-08-15
It sounds like video, but if not fully installed reinstall is the best option.

This should show if the major parts are there or not and if grub is working or you can fix booting with this app. But it will not fix video issues.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by HSovieticus on 2012-08-16
I made myself a boot-repair cd,
put it in my external cd/dvd reader/writer,
but still nothing happens.

Like i said, a black screen with the flickering underscore,
so some kind of empty console which i can't even type in.

Maybe i should've just sold the netbook. I've got like 2 dollars to last me the next 15 days. not sure how much fun it'll be chain-smoking butts.

Uh, but that is tangential. It would just be cool to use Linux finally (and i'm thinking about giving Lubuntu a go after this one).

---

### Post by oldfred on 2012-08-16
If it is a video issue the CD may also need nomodeset or other boot parameter. Hit any key when the tiny accessibility icons (stick figure and keyboard) appear at bottom of screen. Then try f6 and nomodeset. See previous post for links to details and screenshots showing icons & menus.

---

### Post by HSovieticus on 2012-08-17
There is no stick figure or keyboard.
I start my computer. I get the asus screen which says i can press tab or else f12, but nothing happens. then i get the blank, nonfunctional console-like screen.

---

### Post by oldfred on 2012-08-17
Is this then after install and not liveCD? Then you do not get accessibility icons.

From BIOS hold shift key until grub menu appears. Then press e to get edit menu and on linux line change quiet splash to nomodeset.

Previous post on nomodeset links to screen shots of what you should see on reboot after install also. See this subtitle for screenshot example of grub screen with nomodeset typed in.

How to temporarily set kernel boot options on an installed OS (not wubi)

Also similar instructions:
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

