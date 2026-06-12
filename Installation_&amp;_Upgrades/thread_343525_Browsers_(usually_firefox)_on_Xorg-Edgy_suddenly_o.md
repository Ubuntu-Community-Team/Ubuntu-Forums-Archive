---
title: "Browsers (usually firefox) on Xorg-Edgy suddenly overload the CPU"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by lanflett on 2007-01-21
Hi,

I use a NVIDIA FX 6200 using the NVIDIA's original drivers installed with the help of envy. Since 3 days ago, almost every time I visit some URL, my browser (especially when scrolling the page on firefox) seem to lock the entire system: no keyboad response, I cannot click anything.

Apparently xorg starts consuming all the system resources, since I can still use the mouse (but the without response to the clicks) but every 10 seconds it freezes for about 3 seconds (the mouse) and then I can move it again for more 10 seconds before it freezes again and so on.

I spent the last two days trying lots of configurations and tips from topics in forums with problems that seemed approximately the same as mine.

I recently upgraded from Dapper to Edgy using command-line upgrade instead of a brand new installation. No problem occurred and all I had to do was few reconfigurations and all gone fine. The only thing I remember doing before the problem began was installing the last updates from the gnome's update notifier.

Below is a list of things I tried and their results:

a. I tried using Firefox and IE with wine and the problem doens't occur with the emulator;

b. Since in the begining I thought it was a problem with Firefox, I tried with Opera, Mozilla and Konqueror. With the other browsers the problem occur less frequently than in Firefox, but still occurs;

c. Downgrading to Firefox 1.5 didn't solve also;

d. The same problem occurs using KDE;

e. Disabling all plugins from the browsers (flash, java etc) doesn't solve either;

f. I tried switching my nvidia to use all modes (Twinview, Twinview w/ Xinerama, Single view [monitor only] and clone view) and color depths and screen resolutions with no result in solving the problem too;

e. And the last solutions I tried and wich didn't solve were:
            - do a dpkg-reconfigure xserver-xorg;
            - reinstall xserver;
            - and to disable all video acceleration from nvidia

I can't seem to find where can I begin to find the real source of this problem since I can't even go to console using CTRL+ALT+F1 because of the keyboard locking and even trying to attach a dbg (debbuger) to firefox doesn't work to log errors, because the program doesn't really crash (apparently) and no log is produced then.
Hope someone can help, even if it's some tips to where can I begin to find the source of problem.

If I can find any other information about the problem I will post here to help people wich happen to have the same problem.

Sorry for my terrible knowledgment of the english language and thank you for helping.

---

