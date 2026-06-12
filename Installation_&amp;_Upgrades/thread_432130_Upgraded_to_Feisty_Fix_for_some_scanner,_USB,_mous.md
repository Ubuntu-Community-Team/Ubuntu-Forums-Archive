---
title: "Upgraded to Feisty: Fix for some scanner, USB, mouse problem with new kernel"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by imon9 on 2007-05-03
Recently, when i upgraded to feisty from edgy, quite a few things broke:
(1) my Canon LIDE20 stop working (more specifically, the frontend of xsane stop working)
(2) my laptop touchpad left click stop working (for a moment, i really thought i was a hardware problem!! it even stop working in my dualboot windows XP. Many told me it is simply impposible that a kernel problem from linux will affect the dual-boot XP. Apaarently, THAT is NOT TRUE.)
(3) having random freezes and mouse-click stop reponding

A fix came in when i browse through a bug-report thread at [https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488) 

Apparently, fishor at the tread recompile the kernel without USB_suspend & after installing it, eveyrthing (i mean EVERYTHING) that breaks start WORKING AGAIN!!!

 
SO, if you have above mention problem OR any problem after upgrading to feisty, i recommend to install the recompiled kernel (provided .deb file link)

NOTE: disclaimer, I do not gurantee 100% fix for your problem, so does fishor! i'm just suggesting for the sake of helping, and i hope it helps!

here is the link to the kernel:
[http://rapidshare.com/files/28940816/linux-image-2.6.20-15-124-386_2.6.20-15.27ubuntu1.1_i386.deb.html](http://rapidshare.com/files/28940816/linux-image-2.6.20-15-124-386_2.6.20-15.27ubuntu1.1_i386.deb.html)

additionally, i've uploaded it to divshare (which i believe is a simpler and faster download) and here is the link to download the kernel:
[http://www.divshare.com/download/559577-a44](http://www.divshare.com/download/559577-a44)

drop in a thanks to fishor if it works!

---

### Post by NeoTaoistTechnoPagan on 2007-05-03
Isn't there a possible security issue when using an unknown/untrusted kernel? I'm not saying that it is definitely tampered with - Not at all. From a security standpoint, wouldn't it be better to show how to compile your own kernel without that option?

My $0.03

---

### Post by imon9 on 2007-05-04
actually, i am kindda newbies to linux...erm about 2 month now.... 

i tried to read up on doing the kernel compilation myself, but the documentation is unclear... so i assume if i really go ahead and compile it myself, it would do more damage than it already is as the pre-existing broken ones.

Anyway, i can give my personal word on this that the kernel is not tempered with (at least it doesn't seems like being tempered with so far... everything works on my machine and nothing funny happening)

Just offering the piece of info about the availability of the compiled kernel here so that those who needs it and trust the good-o-community here. then go ahead and give it a try. It fixed the problem for me and apparently the few others who had also comfirmed it in the bug thread.

anyway, i guess i made my point clear. hope everyones happy now.. that's our open-source spirit!!

---

### Post by jeanjean84 on 2007-05-04
Hi,

after upgrading to Feisty, my scanner Epson Perfection 660 (using snapscan) stopped working :( 

I searched around and found the Bug #85488 in linux-source-2.6.20 (Ubuntu)

fishor's fix (i.e. recompiled kernel) is working perfectly for me ! 

I have a desktop and no proprietary drivers, ... so no problem !!! :-)

Xsane works ! gscan2pdf works ! xscanimage works ! scanimage works !

Everything works (so far) !  :lolflag: 

Thanks, fishor !   :)

---

### Post by skyhopper88 on 2007-05-13
I tried using this kernal because my usb devices quit randomly. When I loaded it X failed to start so I attempted to uninstall then reinstall my nvidia drivers through the envy script and redo my xorg config. It complained about needing linux-headers-2.6.20-15-124-386, which I was unable to locate and install for some reason.

---

### Post by imon9 on 2007-05-14
erm...you will need to reinstall the kernel 2.6.20-15-generic (linux-2.6.20-15-generic) and it will overwrite the kernel 2.6.20-15-124-386 (which u just removed)

hope this helps you...
reason your x failed to start is most probably that you use restricted driver....

---

### Post by skyhopper88 on 2007-05-14
Is there a way to use the restricted driver with this kernal? I'm fond of beryl, and it doesn't seem to work with plain old nvidia-glx.

---

### Post by imon9 on 2007-05-14
well, gutsy repositories has new kernel 2.6.22-1 but it doesnt fix the USB bug yet :(

i guess there is a way to get thing work = recompilte the kernel yourself.... which might be a bigger challange.... 

(i'm no linux master, but i am pretty good with computer...still i find compiling kernel a tad distasteful for me :/ )

---

### Post by Ebuntor on 2007-05-18
There's a great fix for the problem on Launchpad by **Fraz**. It only works for XSane

[https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488](https://launchpad.net/ubuntu/+source/sane-backends/+bug/85488)

Here's a very simple explanation:[LIST]
[*]Open the terminal and type
[*]```
 sudo aptitude install scanbuttond
```
[*]After the installation simply type ```
scanbuttond
``` to run the program.[/LIST]What this program does is explained on Launchpad
>  the daemon allways watches for the scanner and the usb did not suspend. the real function of this software is to look for the buttons on the scanner and do something usefull lke
scanning -> printing - scanning -> email
To make this program run at startup so you don't have to think about it every time:[LIST]
[*]Go to **System** => **Preferences** => **Sessions**
[*]Under the **Startup Programs **click the **New** button
[*]A new windows will appear. Fill in any name you'd like in the name box, "Scanbutton" for example. In the command box enter **scanbuttond **(with a "d" at the end)[/LIST]I tried it with my scanner and it works great. :) And the buttons on my scanner now work too!
I know it isn't a real fix but at least your scanner works.

---

### Post by crjackson on 2007-09-26
Is there a 64-bit version of this fix?

---

### Post by Ebuntor on 2007-09-26
> **crjackson said:**
> Is there a 64-bit version of this fix?

The workaround I posted should also work on 64-bit systems. :)

---

### Post by crjackson on 2007-10-24
> **Ebuntor said:**
> The workaround I posted should also work on 64-bit systems. :)

Thanks, I got it working somewhat under Feisty, but in the end the perfect fix came from installing Gutsy.

---

### Post by venik212 on 2007-10-25
One might hope that the fishor fix has migrated into 7.10.  Is that true? If not, perhaps that is why myCanoscan N650U scanner does not work...

---

