---
title: "Saitek X52"
date: 2009-09-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Capt. Blackwood on 2009-09-12
Does anybody who has the Saitek X52 Flight Controler know if it works in the new Ubuntu?

---

### Post by luctor on 2009-09-12
I'm interested too, cause I have an X52 too, although it's a bit broken (need to replace the plug that connects the throttle to the stick :( )

---

### Post by Capt. Blackwood on 2009-09-19
Nobody?

---

### Post by rbmorse on 2009-09-19
Heck, the new Ubuntu doesn't even work in the new Ubuntu, yet. 

As soon as I can get Karmic to install I'll try my X52 (today's failure: gets stuck on the log-in screen and locks up).

---

### Post by Capt. Blackwood on 2009-09-19
> **rbmorse said:**
> Heck, the new Ubuntu doesn't even work in the new Ubuntu, yet. 

As soon as I can get Karmic to install I'll try my X52 (today's failure: gets stuck on the log-in screen and locks up).

I'm runnin 9.10 and am TRYING to get it to work.

---

### Post by Chris on 2009-10-03
See this older thread:
[http://ubuntuforums.org/showthread.php?t=1255083](http://ubuntuforums.org/showthread.php?t=1255083)


It is still broken in the latest 9.10 Karmic.  :confused:

---

### Post by Capt. Blackwood on 2009-10-14
crap...

really i want to completely drop my windows...and this is one of two things keeping me from doing so.

---

### Post by Zularan on 2009-10-19
Any news on this issue? Can't find any bugs posted on launchpad and was going to hold out till when the RC is released this week.

Failing that I'm compiling a 2.6.28.14 kernel which is the last one the X52 works on supposedly but I imagine there would be many issues using an older kernel on 9.10. I mainly use it for Xplane and am hoping someone or the dev get around to fixing this.

After reading around the kernels 'blacklisted' this particular joystick.

The system knows the joystick is there. 
```
ls /dev/input/by-id/
usb-045e_Microsoft_LifeChat_LX-3000-event-if03
usb-046d_G15_Gaming_Keyboard-event-if01
usb-046d_G15_Gaming_Keyboard-event-kbd
usb-Logitech_Logitech_Number_Pad-event-if00
usb-Logitech_Logitech_Number_Pad-event-if01
usb-Logitech_USB_Gaming_Mouse-event-mouse
usb-Logitech_USB_Gaming_Mouse-mouse
usb-Logitech_USB_Receiver-event-if01
usb-Logitech_USB_Receiver-event-mouse
usb-Logitech_USB_Receiver-mouse
usb-Saitek_Saitek_X52_Flight_Control_System-event-if00

```

usb-Saitek_Saitek_X52_Flight_Control_System-joystick is missing however

Looking forward to any progress here.

---

### Post by Capt. Blackwood on 2009-10-19
So we've gathered that Ubuntu "Sees" the stick, but will not "Use" it.


I'm gonna use Virtual Box to use the stick for the time being, i've texted under VBox with windows XP on it...and it sees it, and uses it.

---

### Post by Capt. Blackwood on 2009-10-23
[CENTER][SIZE=6][COLOR=Red]NEWS FLASH[/COLOR][/SIZE]

[LEFT][COLOR=Black]Kernel[/COLOR] Linux 2.6.28-16-generic now recognizes Saitek X52 Flight Controler
[/LEFT]
[/CENTER]

---

### Post by aamukahvi on 2009-10-23
> **Capt. Blackwood said:**
> [CENTER][SIZE=6][COLOR=Red]NEWS FLASH[/COLOR][/SIZE]

[LEFT][COLOR=Black]Kernel[/COLOR] Linux 2.6.28-16-generic now recognizes Saitek X52 Flight Controler
[/LEFT]
[/CENTER]

But 2.6.31 doesn't?

---

### Post by Capt. Blackwood on 2009-10-23
> **aamukahvi said:**
> But 2.6.31 doesn't?


haven't played with that kernel...i'm waiting for 9.10 release.

---

### Post by aamukahvi on 2009-10-23
> **Capt. Blackwood said:**
> haven't played with that kernel...i'm waiting for 9.10 release.
Ah. Was just wondering since this is the Karmic Discussion :)

---

### Post by Korenwolf on 2009-10-27
> **aamukahvi said:**
> But 2.6.31 doesn't?

Sadly it doesn't work with 2.6.31.
Been trying to find a solution for days.
I used to have the latest kernel version with wich the X52 worked, but since updating to Karmic I'm unable to fix it.

(I Only use the throttle section)

---

### Post by Zularan on 2009-10-27
Would recompiling the kernel be an option? Is there a switch in the config there that is no longer default for ubuntu I wonder.
 
This would be a pain however as it's still early and newer kernels are often included with updates.  Just a thought as this is the only limitation stopping me upgrading from 9.04 as I use xplane often.

---

