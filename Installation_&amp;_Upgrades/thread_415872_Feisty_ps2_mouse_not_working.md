---
title: "Feisty ps/2 mouse not working"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Aero Leviathan on 2007-04-20
I've been happily using 6.10 for a while, and everything works great. Just to make sure everything still works great in 7.04, I burned and booted a 7.04 Desktop CD before going back and upgrading (I don't intend to use the CD for upgrading, it was just to test). Unfortunately, I found a problem right away: my mouse doesn't work!

This is just a plain, boring old Compaq with a plain, boring old PS/2 mouse. However, it works fine in 6.10! I even put the 6.10 Desktop CD back in to check if it was some configuration upon install time that was supposed to make it work, but no - the mouse works fine automatically from both the installed 6.10 and the 6.10 Desktop CD. No configuration has ever been necessary. It doesn't work at all from the 7.04 Desktop CD.

So you can see why I'm a little hesitant to upgrade to 7.04, lest I be left without a working mouse. Any ideas why this might be happening? Any suggestions?

Thanks :)

Aero


P.S. here is the applicable section of my /etc/X11/xorg.conf under 6.10. I didn't change any of this, it was set up by a clean install of 6.10.

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection
```

---

### Post by marksi on 2007-04-20
I have the same problem except I have upgraded already! I have checked xorg.conf and it seems fine. From other posts it seems this is a kernel problem.

Can anyone tell me what are the keyboard commands for the mouse pointer while I wait for a solution?

Thanks

ian

---

### Post by kerry_s on 2007-04-20
Same here i got some that work perfectly in edgy and debian sid, but don't work in feisty. i replaced them with others i had, but i have 1 that everything works but the middle click and i'm all out of mice. :(  I been using the left+right click for middle click. I looked into it briefly but did not find a fix and it was easier just to change to a working mouse. Sorry, i know it doesn't help.

---

### Post by Aero Leviathan on 2007-04-20
If this is a known kernel bug, could someone provide a LaunchPad link so we can track its progress? I searched but didn't find anything that was obviously applicable. Or should I file a new bug...?

Edit: filed a bug: [https://bugs.launchpad.net/ubuntu/+bug/108350](https://bugs.launchpad.net/ubuntu/+bug/108350)

Also references:
[http://ubuntuforums.org/showthread.php?t=415462](http://ubuntuforums.org/showthread.php?t=415462)
[http://ubuntuforums.org/showthread.php?t=415318](http://ubuntuforums.org/showthread.php?t=415318)

---

### Post by Simon G Best on 2007-04-21
I've had the same problem, [http://ubuntuforums.org/showthread.php?t=414123]("http://ubuntuforums.org/showthread.php?t=414123").

My mouse is a three-button, PS/2 mouse.  An old one.  A real IBM one from an old IBM RS/6000.  Just an ordinary, simple, nonexotic, three-button, PS/2 mouse.  I upgraded to Xubuntu 7.04 two days ago (on the very day it was released), and the mouse just wasn't working.

I ended up finding that selecting an older kernel from GRUB's boot menu resulted in the mouse working again.

---

### Post by marksi on 2007-04-21
I have tried booting with an older kernel but with no success. Which version of the kernel worked for you.

Thanks for your help

Ian

EDIT

I have jsut found that you can enable keyboard control of the mouse pointer by pressing shift+(left)alt+NumLock. You should hear a beep when you enable this.Not brilliant but better than nothing!

---

### Post by Big Ed on 2007-04-22
I had a similar problem.  My usb mouse worked but my ps2 keyboard didn't.  What worked for me was going into the bios screen and disabling the usb mouse.  That got the keyboard to work and didn't affect the mouse.  The only downside is that my arrow keys don't work correctly in vi, they fail only when in edit mode.  So now I'm using pico instead.  An odd failure, but not too serious.

There are a bunch of other solutions to this usb mouse/keyboard problem on these forums, but none of them worked for me.

HTH,
Ed

---

### Post by angeldariodelapuente on 2007-04-22
> **Aero Leviathan said:**
> I've been happily using 6.10 for a while, and everything works great. Just to make sure everything still works great in 7.04, I burned and booted a 7.04 Desktop CD before going back and upgrading (I don't intend to use the CD for upgrading, it was just to test). Unfortunately, I found a problem right away: my mouse doesn't work!

This is just a plain, boring old Compaq with a plain, boring old PS/2 mouse. However, it works fine in 6.10! I even put the 6.10 Desktop CD back in to check if it was some configuration upon install time that was supposed to make it work, but no - the mouse works fine automatically from both the installed 6.10 and the 6.10 Desktop CD. No configuration has ever been necessary. It doesn't work at all from the 7.04 Desktop CD.

So you can see why I'm a little hesitant to upgrade to 7.04, lest I be left without a working mouse. Any ideas why this might be happening? Any suggestions?

Thanks :)

Aero


P.S. here is the applicable section of my /etc/X11/xorg.conf under 6.10. I didn't change any of this, it was set up by a clean install of 6.10.

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection
```

Hello I have a that problem.

Solution????:( :( 

Ubuntu edgy rulz :lolflag:

---

### Post by angeldariodelapuente on 2007-04-22
Hello I find other but report:

> The point is, that Feisty has been launched (20th April) and these bug reports have apparently been ignored.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108382](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108382)

---

### Post by Miguellint on 2007-04-23
> **marksi said:**
> I have jsut found that you can enable keyboard control of the mouse pointer by pressing shift+(left)alt+NumLock. You should hear a beep when you enable this.Not brilliant but better than nothing!

Same problem (no PS2 mouse) using Xubuntu 7.04 but fine in Edgy

Tried the Numlock trick and got the beep but still nothing.

Plugged in an old USB mouse as a workaround. Problem solved for the time being.

Hope the powers that be fix the problem soon-ish.

Regards
Miguel

---

### Post by Big Ed on 2007-04-24
I posted a possible solution to this in another thread you could look at:  

[http://ubuntuforums.org/showthread.php?t=416356](http://ubuntuforums.org/showthread.php?t=416356)

HTH,
Ed

---

### Post by SlipstreamInsane on 2007-05-15
same problem

ps/2 not working

worked fine in 6.10

lots of people posting this bug...still havn't seen any solutions !! :(

---

### Post by poper on 2007-05-18
A similar problem here:

Linux 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux
ASUS A8N-E Motherboard
PS/2 mouse that works fine in Windows XP and work**ed** nice in Ubuntu till a week ago. Now I can use it but sometimes it goes crazy (changes its position, it moves itself...) and sometimes freezes. The keyboard and the system keep working but the mouse not :confused:

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```

I've tried this: [http://ubuntuforums.org/showpost.php?p=2534596&postcount=4](http://ubuntuforums.org/showpost.php?p=2534596&postcount=4) but it solves nothing (for me)
Thanks in advance.

---

### Post by CSMatt on 2007-05-18
I too have this problem.  It seems that the only feasible workaround is to buy USB mice (which are thankfully very cheap yet reliable, I got an optical wheel model for $10) or to buy a USB to PS/2 adapter (which is more expensive that it sounds I'm afraid).

I suppose one could also try compiling the newest kernel from kernel.org, but I probably wouldn't try that.

---

### Post by Gibo on 2007-05-19
> **CSMatt said:**
> I too have this problem.  It seems that the only feasible workaround is to buy USB mice (which are thankfully very cheap yet reliable, I got an optical wheel model for $10) or to buy a USB to PS/2 adapter (which is more expensive that it sounds I'm afraid).

I suppose one could also try compiling the newest kernel from kernel.org, but I probably wouldn't try that.

USB->PS/2 converters arn't expensive. I remember grabbed one for like £1.50 when I used my old modem (all USB slots were full). I'll have a look at my xorg.conf later also, I had issues getting my MX518 to work at first, but managed to resolve it.

---

### Post by CSMatt on 2007-05-19
Well they are here.  I bought mine at RadioShack for $15.

I also think we might be at a misunderstanding.  I'm talking about a device that accepts PS/2 plugs and allows them to be plugged into a USB port.

---

### Post by Simon G Best on 2007-05-21
My mouse problem is solved!  My PS/2 mouse is now working!  Hooray!

There's [a new kernel package that fixes it]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108221/comments/7").  It'll probably be in the updates, soon, but for those who want to see if it works and give feedback, you can try it now (following the easy instructions given in that linked comment).

:D

---

