---
title: "Jaunty not shutting down properly on wireless?"
date: 2009-03-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Sealbhach on 2009-03-24
Anyone got this?

On my laptop (Sony VaioVGN-FZ21M), if I'm on wireless and I switch off the wireless using the external wireless switch during shutdown, I get some text on the screen about a USB connection etc and then it halts... 

I have been holding down the power button to switch it off completely. I think it also happens if I unplug the USB mouse - I think last night I saw a message about hal...


.

---

### Post by Sealbhach on 2009-03-25
Nobody else having shutdown problems? Iwas wondering if i should report it as a bug. 


.

---

### Post by screaminj3sus on 2009-03-25
my laptop (gateway m6862) has hanged a couple times indefinitely during shutdown, it didn't give any message one time, but another is said WAN is in deep sleep or something.

---

### Post by Reiger on 2009-03-25
Easy workaround: don't mess with your hardware until it is powered off. :)
As an added bonus: there is no need to fiddle with the wireless switch if the laptop is going to be powered off anyways, that's like flipping the light switch in a house which is disconnected from the power plant... ;)

Now for another bonus: there is no need, at least AFAIK, because the system itself orders a power-off on the card. At least when I reboot in Vista I'll have to manually turn the power back on the hardware (using the switch). Disclaimer: I do not own a VAIO, I have an (old) ASUS X51RL.

---

### Post by Flag on 2009-03-26
I do have problems, the system won't power off, I don't get a normal shut down screen but a lot of garbage moving over my screen. Need to hit " enter " to shut down completely. Just like 8.10 ( which I skipped completely )

---

### Post by Reiger on 2009-03-26
You may have better luck with: Ctrl+Alt + F2, log in as user (or root) and issue ```
shutdown -hP now
```

---

