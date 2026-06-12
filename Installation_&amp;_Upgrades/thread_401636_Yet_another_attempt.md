---
title: "Yet another attempt"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by utnubon on 2007-04-04
I've tried to install Ubuntu several times and on the release of FF I deciced to have another go. Several hours later and I'm about to give up again.

I've downloaded the Live CD. When I boot from it I need to press F4 at the opening screen to select a widescreen VGA (1400x 1080 from memory) otherwise booting gives me a blank screen. 
After doing this however the desktop comes up OK. Then I install on a blank HDD.

When I try to boot from this I always end up with a blank screen and no further progress. I have an Nvidia graphics card and from what I've read this could the problem. Nothing I have tried from hours of searching here and constantly re-booting gets any further though. 

Even if I try pressing ctrl-alt-F1 I get a screen full of garbled lines. 

Any ideas anyone?<br /><br />
----------------------------------------<br />

----------------------------------------<br /><br /><br />
----------------------------------------<br />

----------------------------------------<br />

---

### Post by mssever on 2007-04-04
> **utnubon said:**
> I've tried to install Ubuntu several times and on the release of FF I deciced to have another go. Several hours later and I'm about to give up again.

I've downloaded the Live CD. When I boot from it I need to press F4 at the opening screen to select a widescreen VGA (1400x 1080 from memory) otherwise booting gives me a blank screen. 
After doing this however the desktop comes up OK. Then I install on a blank HDD.

When I try to boot from this I always end up with a blank screen and no further progress. I have an Nvidia graphics card and from what I've read this could the problem. Nothing I have tried from hours of searching here and constantly re-booting gets any further though. 

Even if I try pressing ctrl-alt-F1 I get a screen full of garbled lines. 

Any ideas anyone?<br /><br />
----------------------------------------<br />

----------------------------------------<br /><br /><br />
----------------------------------------<br />

----------------------------------------<br />
Can you boot into recovery mode? (choose recovery mode from the GRUB screen that shows up when you first boot) If so, that narrows down the problem a bit.

Once you're in recovery mode, type ```
su - youusername
cd
less .xsession-errors
``` and post the relevant parts of the file (or the whole thing if you're not sure what's relevant). If you surround the contents with CODE tags, it will be much easier to read.

Next, try typing ```
startx
``` and see what happens. If it doesn't work, hit <Ctrl><Alt><Backspace> to kill X. Look for and post any error messages you see. Also, check .xsession-errors for anything different/new.

To reboot from recovery mode, type ```
reboot
``` or ```
sudo reboot
``` if you're operationg as your regular user. (Type ```
whoami
``` to find out which user you're running as.

---

### Post by genecaldwell on 2007-04-06
so, in short, you cannot install because of a lack of display output that you can see or read, is that right ? Then I suggest that this be reported as a bug. I believe that you are being bit by a refresh rate bug that is commanding your 60hz LCD display to operate at something else that it cannot support. I found similar links to this issue:

[http://ubuntuforums.org/showthread.php?t=378556](http://ubuntuforums.org/showthread.php?t=378556)
[http://ubuntuforums.org/showthread.php?t=402118](http://ubuntuforums.org/showthread.php?t=402118)

---

