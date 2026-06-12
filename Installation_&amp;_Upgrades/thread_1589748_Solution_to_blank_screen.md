---
title: "Solution??? to blank screen?"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by Russell Burrows on 2010-10-06
My Wife has a HP mini 110 that had XP on it but since She got tired ofviruses/spyware I got asked for a solution.

My solution was Ubuntu NBR and so I downloaded and made a startup disk out of a 4GB usb stick.

Install went fine but wireless did not work?

Then silly me did a twenty second reset on the internet modem since the green internet light was flashing instead of a steady green.

Well it was our internet modem that needed server and password typed in for it to work.

Well the internet works fine now on the home pc but resetting the internet modem with the netbook connected had the result of disabling ETH0 or disabling the wired internet......sigh.

So a noob like me tried reading about several fixes but the simplest was to try to install again the NBR from the usb starup disk.

I inserted the usb stick and pressed F9 to change boot order.
The Netbook reboots and then hangs on a black screen and the usb power light shuts off!

Hmmmm.
Maybe its the usb stick so purchased another.
Nope.

The fix was I noticed that after selecting F9 change boot order then the machine reboots and for ten seconds on the screen there is an image of a star and a USB stick and then it goes to black screen.

The solution:
I said what if I press the enter key in those ten seconds when the star/usb image is on the netbook screen??

Ta da!!! Press the enter key when the star/usb image is on the netbook screen or the netbook ASSUMES that nothing is wanted done and thus it powers off! the usb stick and the netbook screen goes black!

Oh man I felt like such a doh!! 

Note to Ubuntu folks:

Please add a screen that asks or says:
please press enter key in ten seconds or usb startup drive will power off and netbook screen will turn black.

---

### Post by sikander3786 on 2010-10-07
Long post, couldn't understand exactly but from what I understood,

> please press enter key in ten seconds or usb startup drive will power off and netbook screen will turn black.

'Enter' is not required, it automatically should boot into the "Try Ubuntu without making changes" mode.

---

### Post by mörgæs on 2010-10-07
> **Russell Burrows said:**
> ...there is an image of a star and a USB stick...

Just a detail: The image is intended to show a man and a keyboard.

---

