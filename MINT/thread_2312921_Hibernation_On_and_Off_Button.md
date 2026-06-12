---
title: "Hibernation On and Off Button"
date: 2016-02-08
forum: MINT
---

### Post by misswham2 on 2016-02-08
I had to reinstall Mint 17.02 Mate on my pc and before I had the reinstall, I had a button in the panel that would allow me turn the hibernation/suspension ON & OFF at my will.  I had forgotten where I found it and no one on the Mint forum has answered and I thought that maybe someone here would know.  I saw it on a youtube video and I forgot which one.

---

### Post by howefield on 2016-02-08
Thread moved to the "*MINT*" sub forum.

---

### Post by maglin2 on 2016-02-08
Have a look here
[https://sites.google.com/site/easylinuxtipsproject/mint-mate-first#TOC-Disable-hibernation-suspend-to-disk-](https://sites.google.com/site/easylinuxtipsproject/mint-mate-first#TOC-Disable-hibernation-suspend-to-disk-)
Seems the command to put it back is
```
[COLOR=#0000FF][FONT=Arial]sudo mv -v /com.ubuntu.enable-hibernate.pkla /etc/polkit-1/localauthority/50-local.d[/FONT][/COLOR]
```

Doesn't seem that the Easy Linux Tips author recommends it though.

Edit:
On a re-read it appears that this is not to provide a hibernation enable/disable toggle button as OP wants, just to remove/replace the hibernation button itself in the shutdown menu. (It is also for mint 17.3, not 17.02).

---

### Post by misswham2 on 2016-02-08
It says no such file in directory in the terminal when I put that command in.  It was simple the first time.  I just activated something and the button popped up in the panel and I could just click on it when I didnt want my pc to go into sleep mode and I could UNclick it when I wanted it back to normal.  Thats strange that no one knows about this button.

---

### Post by maglin2 on 2016-02-08
No - I'd just realised that command would only make any sense if you'd first followed his original disable command and moved the file to the place he specified.

---

### Post by maglin2 on 2016-02-08
Do you mean hibernate (suspend to disk - takes quite a long time to reboot, just like normal shutdown but session is restored), or sleep (suspend to RAM - wakes up very quickly), or even possibly just lock screen (machine still running but screen locked till you unlock it)? If you want to stop your machine going to sleep after a period of inactivity that's probably a power manager thing in system settings. I think Mint also has a screen locker under system settings (I don't use Mint any more, so I can't check).

---

### Post by misswham2 on 2016-02-08
I found it.  In case anyone wants to know it's called the inhibit  Applet.  It's found in the Add to Panel section when you right click on  the panel in an empty space.  Once it's in the panel, you can click it  to override hibernation/sleep mode settings.

---

### Post by maglin2 on 2016-02-08
Glad you found it - is that Screensaver Inhibitor or some other applet?

---

