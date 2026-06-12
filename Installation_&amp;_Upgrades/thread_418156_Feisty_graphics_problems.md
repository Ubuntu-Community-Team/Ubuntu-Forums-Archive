---
title: "Feisty graphics problems"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by Bealer on 2007-04-22
I currently can't get Feisty to work.

Previously in Edgy I had to use the Alternate CD. I've got a 21" monitor and ATI X1950 which cause problems with the live CD.

I would install then straight away go into recovery mode, run "sudo dpkg-reconfigure xserver-xorg", then reset the graphics settings. I could get it to work with the "vesa" driver, but not the "ati" one. I'd basically have to restrict the available screen resolutions to 800x600 and 1024x768. That way I could load up Ubuntu and install the "fglrx" driver ok.

However with Feisty I do the same thing and it no longer works. Very frustrating given I was hoping the above would be fixed, but it in fact now no longer works. Instead I can makes all the changes but upon loading Ubuntu I get nothing but a black screen. I can hear all the noises in the background and even log in, but just get a black screen.

Anyone got any ideas???

I've tried installing fglrx in Recovery Mode, but despite my machine having a proper network address, it can't resolve any of the repositories. It's annying as it's pushed me back to Windows, and something so core and critical the system you think they'd have picked it up during testing.

---

### Post by pepsi_max2k on 2007-04-22
don't suppose you have a copy of your old xorg.conf on hand? comparing the two might help you fix stuff, though if it's a driver issue then it prolly wouldn't fix anything anyway :(

---

### Post by Bealer on 2007-04-22
Found the solution.

I did a "dpkg-reconfigure xserver-xorg" having booted in Recovery Mode.

When setting everything, I only enabled 800x600 (You'll probably be able to get it to work with 1024x768). 

What I think I was doing wrong was setting the colour depth to 24-bit. I changed it to 16-bit and it booted up fine. I then installed the fglrx driver and all is fine :)

Strange, it did work in 24-bit colour depth with Edgy. Just not Feisty. Hopefully they'll fix these problems next release and I'll actually be able to use the live CD!

---

