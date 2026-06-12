---
title: "installation on toshiba satellite leads to black screen"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by lachlanl on 2008-07-15
New to Ubuntu - novice with unix

Thought I'd try and get a web server and have a play around with Ubuntu.

Downloaded the latest 8.04 desktop ubuntu cd, and tried to install on an old Toshiba Satellite 1800-181A that was lying around.

It goes through the splash screen motions, then when it gets to the end, black screen.

I've tried plugging in an external monitor, same result.

I removed the quiet splash -- from the commands and showed it going through the motions. The last thing I saw was "Starting Ubiquity"

When i press the power button it comes up with a screen saying to remove the cd and press enter, at which time it shuts down. 

Any advice would be appreciated
Thanks
Lachlan

---

### Post by Pumalite on 2008-07-15
Did you try the Alternate CD?

---

### Post by lachlanl on 2008-07-15
I'll give that a shot when i get home tonight, thanks

---

### Post by lachlanl on 2008-07-16
No luck. After the install it acts just as it did with the Live Cd. It shows splash screen on booting, then a black screen...

... so I'm assuming there's something wrong with the default video settings that both a) my laptop b) my external 1280x1024 lcd screen don't like?

---

### Post by Pumalite on 2008-07-16
Time to try some boot parameters:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
First try:
noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off vga=0x317 vga=788 vga=789 vga=791
One by one. Later in different combinations.

---

### Post by lachlanl on 2008-07-16
still no luck. it appears something to do with the xwindows though from what i can tell, as it still responds to the power button being pressed when in blank screen mode (except for when i turned acpi off and then it just turned off the laptop)

I tried coming in in command line recovery mode. Running startx got me to the same blank screen

.. and the different vga modes just changed how the text came up (when splash/quiet was removed) ... the 0x317 and 791 parameters made it use my entire screen.

---

### Post by Pumalite on 2008-07-16
Maybe taking a look at this might help:
[http://www.google.com/search?hl=en&q=installing+ubuntu+on+a+toshiba+satellite&btnG=Google+Search](http://www.google.com/search?hl=en&q=installing+ubuntu+on+a+toshiba+satellite&btnG=Google+Search)

---

### Post by lachlanl on 2008-07-16
It appears that my laptop is using a Trident CyberBlade graphics card. I saw a note somewhere, and gave it a shot, and it worked!

Basically, I booted into recovery mode, root prompt
Made a backup copy of /etc/X11/xorg.conf
Edited /etc/X11/xorg.conf and added to the "device" section

Option "NoDDC"

I'll also probably add some alternate resolutions in the Screens section

Thanks!

---

### Post by Pumalite on 2008-07-16
You are welcome. Congrats!

---

### Post by diamondfist on 2008-11-10
> **lachlanl said:**
> It appears that my laptop is using a Trident CyberBlade graphics card. I saw a note somewhere, and gave it a shot, and it worked!

Basically, I booted into recovery mode, root prompt
Made a backup copy of /etc/X11/xorg.conf
Edited /etc/X11/xorg.conf and added to the "device" section

Option "NoDDC"

I'll also probably add some alternate resolutions in the Screens section

Thanks!

hi, i am trying to do the exact same thing that you did (toshiba laptop w same video chip) and i am running into the same problem. i understand your method but i have no idea how to execute them. could you provide more details? this is the first time i am installing linux. thanks.

---

