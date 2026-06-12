---
title: "Installing Ubuntu 16.04 With NVIDIA GTX 1060 (nomodeset does not work)"
date: 2016-12-05
forum: Installation &amp; Upgrades
---

### Post by m-t-garcia1987 on 2016-12-05
I have been trying to install Ubuntu 16.04 on my desktop which has a GTX 1060 like I stated in the title. 

Whenever it attempts to boot into the installer I get a blank screen.

I tried pushing the down arrow and changing the settings to reflect nomodeset which I saw in some other posts, and this does not work for me.

I **cannot use my onboard graphics port** because I do not have the cable for it, nor the extra few bucks to go buy one.

What are my options here?

Edit

One of the messages I get from my monitor is screen resolution out of range change resolution 1920x1080 60hz. 
So just to be clear, I cannot even install ubuntu onto my system. I had it installed previously with this graphics card but I installed it with another card and then installed the drivers and swapped cards (I no longer have that other card).

Edit 2:

I used nomodeset and vga=795 in the boot options during boot to correct this.

---

