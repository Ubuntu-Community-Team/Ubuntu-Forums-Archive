---
title: "Touchpad quirk on Lenovo Y50-70"
date: 2021-01-24
forum: Installation &amp; Upgrades
---

### Post by nadrach on 2021-01-24
I have been using Lubuntu 18.04 on a Lenovo Y50-70 laptop. It has quirks, the worst being the colour balance (which is a known problem with this machine) and having to run the 4K screen at 1920x1080 because I could not find any scaling on LXDE (it is lightweight, so not unexpected). But the change to LXQt with 20.04 was a different ballgame and I could not work with the overall result. With the upcoming end of support for Lubuntu 18.04, a change becomes necessary.

So after experimentation I have gone with standard Ubuntu 20.04, which while still having the colour balance problem (might be solvable with a suitable profile file), sorted the display brilliantly, giving me 4K crispness on 200% scaling (except for 7-Zip on Wine, which stays at 4K - stare at the screen carefully to get the mouse in *exactly* the right place, but what the heck, I don't use the program often and it's still usable)

The exception is the touchpad. It has two quirks in Ubuntu that were not present in Lubuntu.

Firstly, on the login screen, tapping the touchpad for left-mouse-click does not work, but is OK once you login. Not earth-shattering, but indicative of something possibly amiss.

Secondly, when logged in, stroking the right-hand side of the pad for scrolling no longer works. The area is reserved so has been recognised, that is to say nothing moves on screen when you move your finger (but a little to the left gets normal touch screen mouse movement) but there is no scroll function. I presume this is some difference between Ubuntu WM and LXDE WM. Any suggestions as to what I can do to get the scroll function operating?

And yes, everything works with a mouse, but there are times when it's not practical to use one.

Thanks in advance for any help.

---

### Post by CelticWarrior on 2021-01-24
> [COLOR=#000000]except for 7-Zip on Wine,[/COLOR]
You know there's a native 7-zip desktop, don't you? And that not even that is needed, command line tools for supporting the format and more than enough and integrate correctly with the native tools?

---

### Post by nadrach on 2021-01-24
I have the native 7-zip desktop installed, but it runs 7-zip 16.02 which dates from 2016. Current stable (not alpha or beta) is 19.00 from 02/2019, which was created to deal with a security issue in the 7-zip encryption. I re-encrypted all my archives at the time. Going back is not an option.

---

### Post by nadrach on 2021-02-03
Problem solved. Ubuntu defaults to two-finger scroll on install with edge scroll disabled. Settings reversed. Sic friatur crustum.

---

