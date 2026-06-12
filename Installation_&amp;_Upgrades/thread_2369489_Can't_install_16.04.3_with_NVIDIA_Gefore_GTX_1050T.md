---
title: "Can't install 16.04.3 with NVIDIA Gefore GTX 1050Ti"
date: 2017-08-23
forum: Installation &amp; Upgrades
---

### Post by linuxthunder on 2017-08-23
Greetings,

I just built a new rig with a Ryzen 1700 processor, Gigabyte AB-350 Gaming 3 motherboard, and a Geforce GTX 1050Ti.  When I try to install or try 16.04.3 live from a USB, it just hangs on the purple screen with the ubuntu text and the 5 lights just sequentially run through but nothing ever happens.

Ryzen doesn't have graphics integrated so I have to boot through the video card which I think is the issue but I could be wrong.

I did install Manjaro successfully but I had to make a change on the boot screen to use "non-free" drivers and it worked.  I would like to switch back to Ubuntu however.

Does anyone know how to get this machine booted?  I'm guessing I have to do something regarding the graphics card when I boot from the USB or perhaps it is something else.

Thanks in advance

---

### Post by Bashing-om on 2017-08-23
linuxthunder; Hi !

A common kernel (boot)parameter is nomodeset, which is needed for some graphic cards that otherwise boot into a black screen or show corrupted splash screen. See : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) on how to use this parameter ,

I too have a later generation nvidia card, and I had to initially boot up with "nomodeset", then install the proprietary driver.

[INDENT][INDENT][INDENT]works for me
[/INDENT][/INDENT][/INDENT]

---

### Post by linuxthunder on 2017-08-23
You're the man!!!  That was really easy.  The only thing that link doesn't specify is where to type in nomodeset so I did a search and found an ask ubuntu thread that specified to delete "quiet splash" and replace that with "nomodeset."

Thanks for your help!  Appreciate it.

---

### Post by Bashing-om on 2017-08-23
linuxthunder; Great .

You have a proprietary driver now installed, and all is rosy ?
If so; Then
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

### Post by linuxthunder on 2017-08-24
Yes, proprietary driver installed and everything working great!  Thanks

---

