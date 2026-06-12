---
title: "no dual boot option"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by corcorcor on 2010-01-14
Hello there.

I'm trying to install Ubuntu as a dualboot, i also have Windows XP. But during the installation, when this screen should appear

[IMG]http://i37.photobucket.com/albums/e99/dikkecor/ubuntu.jpg[/IMG]

(Translation)
(*) Dualboot, choose at startup
( ) Empty and use complete harddisk
( ) Use biggest connected space
( ) Manually adjust partitions.

I get a screen with only 2 options, the second and forth. How do I get the Dualboot option?

---

### Post by darkod on 2010-01-14
Boot with the cd, Try Ubuntu option, and when the live desktop loads open terminal and execute:
sudo apt-get remove dmraid

Either click the Install icon on the desktop or reboot and select the Install Ubuntu option, and see if you get the options you expect.

Just a word of advice, with XP it's better to shrink XP first, reboot to make sure XP is happy with the shrink and to do its disk checks, and only then install ubuntu into the free space created by the shrink.

Doing the process in the same step can possibly corrupt XP system files. XP is very stubborn about this and sensitive.

Because XP doesn't have a shrink tool like vista and 7, you could use the ubuntu cd with the live desktop loaded, open Gparted (System-Administration) and shrink XP partition as much as you want. Then reboot few times and let XP do its disk checks. After it's working fine after the shrink, proceed with ubuntu install.

---

### Post by corcorcor on 2010-01-14
> **darkod said:**
> Boot with the cd, Try Ubuntu option, and when the live desktop loads open terminal and execute:
sudo apt-get remove dmraid

Either click the Install icon on the desktop or reboot and select the Install Ubuntu option, and see if you get the options you expect..

Nope, still the same.

> **darkod said:**
> Because XP doesn't have a shrink tool like vista and 7, you could use the ubuntu cd with the live desktop loaded, open Gparted (System-Administration) and shrink XP partition as much as you want. Then reboot few times and let XP do its disk checks. After it's working fine after the shrink, proceed with ubuntu install.

I'm not sure how Gparted works, when i clicked resize C it said the minimum and maximum sizes are the same. I couldn change anything.

---

### Post by darkod on 2010-01-14
Can you post the Gparted screenshot here? You can take screenshots while in live desktop, it was in Applications-Accessories. Just set the timeout at 3sec for example, so the Take Screenshot window gets closed before taking the shot. :) And the live desktop should allow you internet access and you can post it here right away.

---

### Post by corcorcor on 2010-01-14
Here you go :)

First screenshot is when I open Gparted, second is where I can't resize XP.

---

### Post by darkod on 2010-01-14
In the second picture, if you click on the right end/border of the bar and start dragging it to the left, the numbers will start to change.

This is the start situation, the current one. The middle number is giving you the current partition size, the top number how much space you have preceding it (which is 0 at the moment), and the bottom number how much space after the partition (again, it's 0 at the moment, the other partition is starting right away).

If you start dragging the end to the left, the middle number should start decreasing, and the bottom one increasing.

---

### Post by corcorcor on 2010-01-14
Well, I can't drag it to the left. And when i change the middle number, it changes immediately back to what it was :(

---

### Post by darkod on 2010-01-14
OK, then it's complaining about something, but I don't know what. :( Sorry.
Maybe that's why there is the triangle exclamation mark next to /dev/sda1 in Gparted.

---

