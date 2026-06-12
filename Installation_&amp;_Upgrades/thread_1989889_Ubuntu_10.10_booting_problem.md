---
title: "Ubuntu 10.10 booting problem"
date: 2012-05-28
forum: Installation &amp; Upgrades
---

### Post by Plane on 2012-05-28
Hello,

I've installed 64-bit Ubuntu 10.10 on my computer. When my computer restarts, it hangs at the Ubuntu loading screen and everything freezes. I need some help :S

---

### Post by carl4926 on 2012-05-28
You installed an older version in favour of the latest 12.04? Why
Have you tried the failsafe boot?

---

### Post by Plane on 2012-05-28
I just don't seem very fond of the newer one, and no I haven't used the failsafe boot. I don't think I can even get to it

---

### Post by carl4926 on 2012-05-29
When the grub menu comes up
try pressing e
and type: nomodeset
boot with that, see if it helps

If it's not that try using;  acpi=off

I take it the Live Desktop of the CD worked OK

---

### Post by Plane on 2012-05-29
It didn't work. I might be doing something wrong or it just doesn't want to work :(

---

### Post by carl4926 on 2012-05-29
> **Plane said:**
> It didn't work. I might be doing something wrong or it just doesn't want to work :(

Did the live cd you installed from work? I mean, did you boot to the live desktop and try it before install?

---

### Post by Plane on 2012-05-29
Yes it does work. I'm using it right now

---

### Post by carl4926 on 2012-05-29
Try adding

--verbose

to the boot line and see if you get the scrolling text as it boots, try and see if you can spot the problem area.

Or even just try the install again
Did the media check OK?

---

### Post by Shadius on 2012-05-29
I wonder if it's a bad install that can be remedied with a reinstall...

---

### Post by Plane on 2012-05-29
The media is fine. Just before it gets to the Ubuntu loading screen, it says something about an invalid something and then disappears really fast. Then after that, everything stops at the loading screen.

---

### Post by carl4926 on 2012-05-29
I'd try the install again
Be sure to not have auto login enabled.

---

### Post by mörgæs on 2012-05-29
Are you aware that security bugs in 10.10 are left unfixed? 

If you don't like the new Ubuntu then Xubuntu 12.04 is a better option.

---

### Post by Plane on 2012-05-29
It boots perfectly now! Thanks for the help :)

---

### Post by carl4926 on 2012-05-29
> **Plane said:**
> It boots perfectly now! Thanks for the help :)
Good to hear

---

### Post by Shadius on 2012-05-29
> **Plane said:**
> It boots perfectly now! Thanks for the help :)

Congratulations! Please mark the thread as solved. :)

---

