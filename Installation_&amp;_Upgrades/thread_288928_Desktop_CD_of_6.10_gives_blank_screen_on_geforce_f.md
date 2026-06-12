---
title: "Desktop CD of 6.10 gives blank screen on geforce fx5600"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by Cirrus on 2006-10-30
Hello.

I could use fast advice: I want to install ubuntu 6.10 to a athlon xp 2800+ machine with geforce fx5600. The desktop cd starts to boot fine, but after it tries to start the x-windows system the screen goes blank. This same problem I had also with 6.06. Then I resolved it by using instructions from here [http://www.penguintutor.com/blog/viewblog.php?blog=217](http://www.penguintutor.com/blog/viewblog.php?blog=217) Also the problem went away with 6.06 if I replaced the geforce card with radeon 9800pro.

What I am asking that if some one knows a way to get get the desktop cd running with fx5600 or do I just need to get the alternate-installation cd again?

This installation issue with old geforce cards have seemed to around atleast two releases now. Why can't it be fixed?

- 
Cirrus

---

### Post by Aikon- on 2006-10-30
> **Cirrus said:**
> Hello.

I could use fast advice: I want to install ubuntu 6.10 to a athlon xp 2800+ machine with geforce fx5600. The desktop cd starts to boot fine, but after it tries to start the x-windows system the screen goes blank. This same problem I had also with 6.06. Then I resolved it by using instructions from here [http://www.penguintutor.com/blog/viewblog.php?blog=217](http://www.penguintutor.com/blog/viewblog.php?blog=217) Also the problem went away with 6.06 if I replaced the geforce card with radeon 9800pro.

What I am asking that if some one knows a way to get get the desktop cd running with fx5600 or do I just need to get the alternate-installation cd again?

This installation issue with old geforce cards have seemed to around atleast two releases now. Why can't it be fixed?

- 
Cirrus

Hi Cirrus,

There are several of us that are having a similar issue, all with different hardware. I don't think you specified this in your post, but once we've reached this blank screen (what w[e've been calling Ubuntu's BSOD]("http://www.ubuntuforums.org/showthread.php?t=281111") (or Black Screen of Death) we can't get to a console using ctrl-alt-f1 through f6. As yet there is no resolution.

We've also [filed a bug report here]("https://launchpad.net/distros/ubuntu/+bug/67487"). Read through the comments in both threads and if the issue you're having is in fact the same, then please add your comments to the bug report.

Aikon-

---

### Post by Cirrus on 2006-10-30
Hi again.

I myself can get a console with ctrl-alt-f1-f6. So the whole system is not frozen. I also could get console with 6.06. So it seems that it not exactly the same problem. 

When I used the alternate-cd to install the 6.06 all went well until with the ready installation I tried to boot to GUI first time. Then the blank screen was there again. Then the solution was sudo apt-get install nvidia-glx nvidia-kernel-common and sudo nvidia-glx-config enable in console and then reboot. After that the GUI worked.

So it seems that this problem has to do something with nvidia drivers.

---

### Post by Cirrus on 2006-10-30
Hmm. Altough I know very little about Linux things I managed to fix this now it seems. I started console with ctrl-alt-f6 and edited file /etc/X11/xorg.conf and changed following part:
Section "Device"
         Identifier "Generic Video Card"
         Driver     "vesa"

to
Section "Device"
         Identifier "Generic Video Card"
         Driver     "nv"

then I switched back the x-windows console with ctrl-alt-f7
and restarted it with ctrl-alt-backspace and GUI started!

---

### Post by Aikon- on 2006-10-30
> **Cirrus said:**
> Hmm. Altough I know very little about Linux things I managed to fix this now it seems. I started console with ctrl-alt-f6 and edited file /etc/X11/xorg.conf and changed following part:
Section "Device"
         Identifier "Generic Video Card"
         Driver     "vesa"

to
Section "Device"
         Identifier "Generic Video Card"
         Driver     "nv"

then I switched back the x-windows console with ctrl-alt-f7
and restarted it with ctrl-alt-backspace and GUI started!

Nice work =)

I'm glad you got your system to work, and you're right, its not the same problem. Have fun!

-Aikon

---

