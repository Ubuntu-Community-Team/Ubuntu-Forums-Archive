---
title: "Portable installation of ubuntu 10.10 on external HDD..."
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by GuitarJim1987 on 2010-11-20
Hi all

I did have a quick search but I haven't had any luck in finding an answer to my problem. I have installed ubuntu 10.10 32 bit to an external HDD. Grub and everything is on that drive.

It works fine when booting on the laptop I installed it with however when I tried it on my dad's PC it won't boot. I saw the ubuntu logo on screen  for a brief second then the screen reported no input signal and stayed  like that. External HDD didn't sound like it was being accessed either.  Waited for a minute or so and hit ctrl+alt+del and again I saw the  ubuntu logo flash on screen before it restarted.

Hardware in dad's PC is:
AMD Phenom II X 2 545
Asus M4A785TD-V EVO 785G (using onboard graphics)
2GB DDR3

It still boots fine on my laptop. I was under the impression that the Kernal automatically scanned for hardware everytime it boots so transfering to another PC shouldn't be an issue but I appear to be wrong.

Any help much appreciated.

---

### Post by sikander3786 on 2010-11-20
Graphics drivers seem to be causing a problem there.

Did you install proprietary drivers for your previous PC's graphics card?

If you want it to be portable, leave the drivers to the defaults.

---

### Post by GuitarJim1987 on 2010-11-20
I didn't install any proprietary drivers however the laptop does have an Nvidia Card while my dad's has AMD. Will take a look.

---

### Post by sikander3786 on 2010-11-20
You can also try the nomodeset parameter and see if Resolution is causing a problem there.

You need to press and hold down Shift key from Bios screen until you see Grub menu.

Highlighting the first entry, press 'e' to edit it and remove "quiet & splash" and type "nomodeset" in their place. Then press Ctrl + X to continue boot and see if you can get to the desktop then.

---

### Post by GuitarJim1987 on 2010-11-20
Got it sorted, I don't remember installing the GPU driver but I must have done, deactivated it and it's loaded up fine. 

One other thing that's a bit weird is I keep losing wireless internet access while using ubuntu on my laptop. It still shows as connected on the nm-applet though.

---

### Post by sikander3786 on 2010-11-20
Yes I felt like it was going to be a graphics driver problem :-)

Glad to know it is sorted.

Regarding wireless, it would be better to start a new thread in the Networking & Wireless sub-forum. You'll find some experienced members regarding the problem there.

For the moment, you can mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

### Post by GuitarJim1987 on 2010-11-20
Will do, thanks buddy [:)]

---

