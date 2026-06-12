---
title: "Ubuntu install hangs at black screen"
date: 2012-01-11
forum: Installation &amp; Upgrades
---

### Post by Moldy11 on 2012-01-11
Hello,
Im sorry if this is an over-asked or stupid question, but iv been at this all day and have ran out of ideas.

Im trying to install ubuntu on my laptop. It has an amd quad core 64bit processor, and amd radeon graphics, but whenever i try to boot from unetbootin or the livecd, it will load for a minute then just go to a black screen, like its getting no power. It also does this with a secondary monitor. iv tried multiple installs from usb and cd, and still no luck. its probably some simple fix im not noticing, but any help would be greatly appreciated. i just wanna get this installed lol.

thanks. and again, sorry if this is a stupid question.

---

### Post by MAFoElffen on 2012-01-11
> **Moldy11 said:**
> Hello,
Im sorry if this is an over-asked or stupid question, but iv been at this all day and have ran out of ideas.

Im trying to install ubuntu on my laptop. It has an amd quad core 64bit processor, and amd radeon graphics, but whenever i try to boot from unetbootin or the livecd, it will load for a minute then just go to a black screen, like its getting no power. It also does this with a secondary monitor. iv tried multiple installs from usb and cd, and still no luck. its probably some simple fix im not noticing, but any help would be greatly appreciated. i just wanna get this installed lol.

thanks. and again, sorry if this is a stupid question.
Please refer to the instructions in my Sticky:
**[B]Sticky:**[/B] 			                         [COLOR=#008C00]**[all variants]**[/COLOR] 			 			[Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

Goto the first-half of Post #3...

That should get you into an install with graphics.  (If not tell me.)

After the install-
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Temporarily Editing Grub Menu for Boot Options]("http://ubuntuforums.org/showpost.php?p=11491229&postcount=812")**[/SIZE][/COLOR][/SIZE][/COLOR]
Then, after booting to the desktop, go to Additional Drivers to install your driver. If you don't see your driver, open a terminal session and 
```

gksudo gedit /etc/apt/sources.list

```
And uncomment the two "Conical Partner" lines, save and exit.

---

### Post by Moldy11 on 2012-01-12
Awesome. Thanks alot. I'm gonna give that a shot soon and ill post how it goes.

---

### Post by Moldy11 on 2012-01-12
Well I tried that, and it got it installed and everything. But when I try editing the grub menu to nomodeset it just hangs at a black screen. IV tried to figure it out on my own all day, but haven't had luck. Sorry to ask for help again lol.

---

### Post by kevdog on 2012-01-12
How are you trying to edit the grub menu?  In a pinch, if you know vi, you can edit /boot/grub/grub.cfg within the terminal.  Go down to the kernel line that you want to insert nomodeset on,  use the arow keys to go where you want this command, push the "i" key (for insert), type nomodeset, push the "esc" key to exit editing mode, and then push Cntl-ZZ (Z twice) to exit and save the file.  Thats it!

---

