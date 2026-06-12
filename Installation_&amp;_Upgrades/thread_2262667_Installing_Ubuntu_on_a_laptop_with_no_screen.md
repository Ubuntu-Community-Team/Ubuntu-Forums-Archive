---
title: "Installing Ubuntu on a laptop with no screen"
date: 2015-01-26
forum: Installation &amp; Upgrades
---

### Post by Jedwinjim on 2015-01-26
Is it possible? I need to a do a clean install on my laptop (it's borked, ONLY thing I can do is bring up virtual terminal (ctrl+alt+F1-F6)). On top of this, the screen is smashed, leaving no idea whats happening. I can of course HDMI to my TV, & get myself to installation screen, only the TV is secondary display, so it's background wallpaper, while the installation guide is obviously sitting on my impossible to see laptop screen.

Any help on how to switch the screens over before I actually start the ubuntu installation progress?

Many thanks,

j.

---

### Post by MAFoElffen on 2015-01-26
While connected to an external monitor, use the laptop's hotkeys to switch to external, turning off the internal. Laptops have this hotkey defined in their keyboard BIOS. But what that key-combo is, varies by Vendor and model.

It's impossible for us to guess what tha key-combo might be without knowing the make and model of the laptop.

---

### Post by Jedwinjim on 2015-01-27
Hey  MAFoElffen, thanks for the response. Laptop is an unusual one, Novatech nFinity N1403 [http://www.novatech.co.uk/products/laptops/n1403.html](http://www.novatech.co.uk/products/laptops/n1403.html) is that any help?
 
Thanks.

---

### Post by westie457 on 2015-01-27
Hi Jedwinjim, a chat with the people at Novatech should be able to help with various hotkey combos. [http://www.novatech.co.uk/contact.html?d=t](http://www.novatech.co.uk/contact.html?d=t)

---

### Post by MAFoElffen on 2015-01-27
Taking a screen shot of the keyboard in that old add, it looks to be the same fn-key layout as my Acer. It's pretty grainy when blown-up, but (by my best guess) it looks like <fn><F5> is internal off, external on (Pressing it again would toggle it back);

That's my best guess on that. fn-keys were never a standardized kind of affair.

---

### Post by Jedwinjim on 2015-01-28
Ok thanks guys, I wasn't aware that was what that hot key represented.. because it's never worked! Just my luck huh? You think it might work on a VGA cable instead of HDMI? wishful thinking? I've experienced hotkeys not working with linux aplenty in the past, so I suppose this comes as no surprise.

---

### Post by MAFoElffen on 2015-01-28
if you can get a live image booted, then you could switch the output over querying via setting with xrandr. Installing from live image, then before reboot, you could edit a script using xrandr (in startup) to direct that output or an xorg.conf file configured to direct output ... to that specific port. What you would need to do is let the live image get far enough to use <cnrtl><alt><F2> to get to the CLI of a virt tty session. Not suggested for beginners or the faint of heart... But still possible.. 

Best guess- Wwhen the disk activity light ceases, wait a few, then press the enter key... repeat... until you get to a desktop. (would not get a menu or panels in in the external monitor) Then press <cntrl><alt><F2> wait a few. (No credentials in the Live Image.) Wait a few. xrandr command would be altered to the port type you are connected to and the video GPU in your laptop. (yours Intel)

```

xrandr --output LDVS1 --off --output DVI1 --auto

```
Which says to turn an Intel lcd display port off and turn dvi port 1 on...

OR
```

xrandr --output DVI1 --primary

```
would just set the DVI1 as the primary port, and you could get that display working to work out the rest...

If you can't get to virt tty session using an external display... then your chances are greatly diminished.

---

### Post by efflandt on 2015-01-28
What video chip does it have? In the past I seem to remember ATI or Intel defaulting to external display if one was connected and on during boot, but Nvidia would not. So when someone cracked a screen (diagonally half of it was gone) on an old laptop with Nvidia graphics, I could not see much of BIOS splash screen or grub menu, but managed to see enough of the screen in X to configure it to use external display as primary for X at least. Not sure if that is still the case with AMD video or what happens with hybrid Intel/Nvidia.

---

### Post by MAFoElffen on 2015-01-28
The specs on his laptop says Intel. The Op says it boots the live Image with external display... with the external as the right screen, which would mean that the laptop screen is still active enough to return a status to XServer, thus is the primary left X session. If the internal was completely dead, the external would auto config to being primary.

If he can get to prompt, even blindly, he can swap that and turn off the output to the LCD display... initially using xrandr, then with xorg to make that persistent.

---

### Post by Jedwinjim on 2015-01-29
that worked, thanks boys, now running my laptop via TV again :)

---

### Post by MAFoElffen on 2015-01-29
xrandr is only good until you reboot. Then it has amnesia about what was done previously. 

The easiest way to make that persistent is to copy one of the startup files and in properties, change the command line from starting whatever program it started-- to that xrandr command string. That way every time it starts X, it will switch that for you. The other way is to set the output to that monitor and port in xorg.conf.

---

