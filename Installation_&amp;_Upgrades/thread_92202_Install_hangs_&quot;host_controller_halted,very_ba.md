---
title: "Install hangs: &quot;host controller halted,very bad!&quot;"
date: 2005-11-19
forum: Installation &amp; Upgrades
---

### Post by Nolochemical on 2005-11-19
hey,

I am trying to install ubuntu and have had some success. The install seems to have stopped responding after it ejects the cd, reboots, and starts to install the packages. It halted when it was installing the packages at 44%.I then pressed CTRL+ALT+F4 to see the messages and the the final few messages are : 

Installing package states...Done
1) [2496.812507] uhci_hcd 0000:00:01.2: Host system error, PCI problem?
2) [2496.822454] uhci_hcd 0000:00:01.2: Host controller halted, very bad!

specs 
Motherboard :Asus TX97E 
pentium mmx 200Mhz
196 Mb Ram
creative 24x cdrom
40g hdd (generic)
Trident video card ( older,can't recall the model)

Notes: 
 A suggestions that I found very helpful within the forum was to make sure the cd or media you are using is not damaged!!

!! update the bios before installation!! (older machine)this helped me with the previous install problem.

I am wondering if anyone would have any advice or helpful hints that may help me here, I would really appreciate it. I am really hoping to cross over to unix to start some developement in c. Does anyone know if there is another GUI that might be "easier" to install than GNOME, I really like the pretty colous n all but its getting frustrating. :(

Unix - Live Free or Die!

---

### Post by yesplease on 2005-11-19
I found this by searching for light weight desktop :)

 if you're running older hardware you might want to try something slightly more light weight than gnome/kde such as xfce or enlightenment...

(there is also a desktop that is completely configurable, I think it is called blackbox)



" !! update the bios before installation!! (older machine)this helped me with the previous install problem. " This means youre install problem is solved?

---

### Post by Nolochemical on 2005-11-19
It was not totally solved, but it helped a bit with some of the install freezes and such..

I searched the forums again and found some more info about different Window managers..very helpful.

[http://www.ubuntuforums.org/showthread.php?t=87276&highlight=xfce+fluxbox+gnome](http://www.ubuntuforums.org/showthread.php?t=87276&highlight=xfce+fluxbox+gnome)

I finally got through a server install.I just have to choose a WindowManager  that supports my video card :???: 

vid card= 
Trident microsystems TGUI 9440 agi
1024kbytes (I think) 

but the previous link doesnt say much about min. requirements..time for some more reading

---

### Post by yesplease on 2005-11-19
I did not know that the windowsmanager should support the video card, isnt that arranged via the drivers?

Perhaps you can also write some words on the desktop you choose and why.

---

### Post by Nolochemical on 2006-03-06
Took me a bit of time to finish this thread been away.Thanks for the reply's. 

  I have not yet choosen a window manager yet. I think fluxbox is the way to go because it sounds like a lightweight option. Im not exactly sure if my video card is good enough to install anything else but the base system.:confused: 

Just a side question, how would I install gcc -c  compiler- from the base system or the console rather? I am preparing to not be able to use the gui version or buy a new vid card...:-k 

thank for any replies

~Nolochemical

---

### Post by Nolochemical on 2006-03-06
found my own answer about 

how to install gcc  C / C++ programming
question..[http://www.ubuntuforums.org/showthread.php?t=107569;](http://www.ubuntuforums.org/showthread.php?t=107569;))

---

