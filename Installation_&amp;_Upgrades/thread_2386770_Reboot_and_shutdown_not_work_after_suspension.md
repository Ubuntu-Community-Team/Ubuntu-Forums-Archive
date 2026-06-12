---
title: "Reboot and shutdown not work after suspension"
date: 2018-03-10
forum: Installation &amp; Upgrades
---

### Post by pema001 on 2018-03-10
Hello,

I have a problem with shutting down PC after wake from suspension - I push the button "power off" on ubuntu launcher - everything stops (even mouse and keyboard), the  desktop shows (without any icons on it) and nothing happens. I tried it also from CLI (sudo shutdown now), but same result.

Actually, when I turn it off without the previous suspension, it works fine. 

Here is the [video with my problem]("https://vse-my.sharepoint.com/:v:/g/personal/pokm05_vse_cz/EYL1ddCq8DVHr31LY2iVOTkB4SbAPGWGn8y3rdng5uLm2A?e=suUMwt").

Thanks for tips!

---

### Post by ajgreeny on 2018-03-10
What do you see if you use terminal with command ```
shutdown -h now
``` after coming out of suspension?

---

### Post by pema001 on 2018-03-10
Nothing, the system freezes immediately after clicking "enter" at the position, where I am. Even the blank desktop did not show.

---

