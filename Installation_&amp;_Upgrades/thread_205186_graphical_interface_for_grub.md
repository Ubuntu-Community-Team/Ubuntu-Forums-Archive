---
title: "graphical interface for grub"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by AltoMelto on 2006-06-28
Hello
i know it's a small problem, but if anybody has the solution...
Ince i own a ATI X850Pro the installation disk for ubuntu didn't recognize properly my card and so i had to boot in safe graphic mode. Since then I have installed the correct ATI drivers (but even without everything in 2D went perfectly). 

For that reason I think ubuntu installed the textual version of grub, so i'm left with a plain black/white bootloader, when I was hoping to get a multicolor madness one. How is it possibile to switch to grub graphical?

Thanks!

---

### Post by scxtt on 2006-06-28
if you just want color, make sure a line like
[indent]color red/black white/black[/indent]isn't commented out in /boot/grub/menu.lst

if you want something a little more fancy, well i'm not sure - i just use defaults cause i don't look @ grub often ... i have seen some fancy GRUBs w/ Mandriva and SuSE (image backgrounds, etc.) ...

---

### Post by AltoMelto on 2006-06-28
I was more thinking about the graphical interface....
anyway thanks

---

### Post by aysiu on 2006-06-28
Try [this](http://www.ubuntuforums.org/showthread.php?t=89916).

---

### Post by scxtt on 2006-06-28
there isn't a "graphical interface" (a la GDM, etc.) -- at best there's what you're calling a "graphical interface" which is just an image w/ the "textual interface" you reference ...

---

### Post by AltoMelto on 2006-06-28
You're right, i mean the slpash image, and I think I will solve with the help provided in the link

Thanks a lot
I'll let you know!

---

### Post by AltoMelto on 2006-06-28
Thanks a lot, working perfectly.

Since we're there and you're so helpful, i'll abuse your kindness with a couple more graphics boot issues....

1) now that i have the splash screen I can't see anymore the highligting for the selected booting OS, i guess it's a colour codes issue, can you tell me in the line 
color red/black white/black 
what means what?

2) the first part of the boot is in low resolution (i guess 640x480) and it's quite annoying, mostly beacuse my LCD doesn't like that resolution, any hint?

Thanks a lot again!

---

### Post by scxtt on 2006-06-28
congrats on getting it working :D

1) i'm not sure which is which - couldn't find much documentation on it (just examples) ... experimentation is probably in order ... i think the 1st set is the text (foreground and background) and the other set is for background color and the outline color ...

2) i think it's possible to get 1024x768 w/ a little finagling, but i'm not sure how it's done (and that might be for the splash/usplash) ... did you resize your image to 640x480?

---

### Post by AltoMelto on 2006-06-28
1) thanks, I will experiment

2) i have found eslewhere to add to the kernel line in grub a vge=1280x1024, but doesn't seem to work, and the image is actually 640x480 as i downloaded it from the internet....

---

### Post by hemes on 2006-06-28
try one of the following boot options in the kernal line to get 1024x768 resolution on startup  :) 

vga=792
or
resolution=1024x768

---

