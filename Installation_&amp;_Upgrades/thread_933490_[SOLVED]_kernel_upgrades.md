---
title: "[SOLVED] kernel upgrades"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by ant1060 on 2008-09-29
Hi 
I am unable to run any kernel higher than 2.6.24-17  Any higher number kernel fails to install properly and I lose screen resolution, or there is an error message.
Any ideas?  Does this matter at all?  What could be causing it?
Thanks.

---

### Post by mikewhatever on 2008-09-29
Loosing screen resolution or getting errors doesn't necessarily mean the new kernel is not running. Are you trying to compile your own kernel? What errors do you get?

---

### Post by zvacet on 2008-09-29
[This]("http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html") can maybe be useful to you.

---

### Post by ant1060 on 2008-10-03
Thanks : I am trying to build the new kernel using Kernelcheck now.  The process takes 2-4 hours!!  Will post the outcome.  Thanks again :)

---

### Post by ant1060 on 2008-10-04
As promised : Kernelcheck worked fine, but was very slow (it took all night to complete the upgrade to 2.6.25.5-ultimate).

HOWEVER there were the following problems after reboot :

1) no wireless connection at all - no wifi light - nothing at all
2) no sound of any kind
3) the nvidia proprietary driver had been disabled - I could not reinstall it and reconfiguring the x-server produced ONLY a low resolution basic screen which I could not change
4) my native Belgian French keyboard was no longer recognised and I had to try and remember where the w, q, a, z and hyphens, commas etc were on a US keyboard so I could log on

So, in the end I had to give up again and have reverted once more to the trusty 2.6.24-17-generic kernel - the starting point of my thread.  BTW, I had to replace the xconf file with my backups, after reverting, as various keys and touchpad settings no longer worked.

Now, I am afraid what will happen in a few weeks' time when I try and upgrade to 8.10 Intrepid....  Will I be left with an unusable system?

Thanks for any reflections or ideas on this!

---

### Post by ant1060 on 2008-10-19
Today I had some time free and after about 4 hours' work I managed to get the 2.6.24-21 kernel up and running on my machine :)
The key to success was :

1) a cold restart into the -21 kernel which produced a wifi connection after all, from which I was able to run Envy NG to re-install the NVIDIA driver.  I had to do this four times in order to eliminate the problems which cropped up.  I was not able to get the -19 kernel to work, as not even a cold restart produced a wifi connection and life seemed too short to wrestle with that!

2) allowing the xorg.conf file to be written by NVIDIA using the sudo dpkg-reconfigure -phigh xserver-xorg command, and then tampering with the file until it recognised my native Belgian keyboard, and my Synaptics Touchpad settings (for scrolling down). I was unable to select the correct screen resolution nor save it to xorg.conf (once I had set it manually) through the NVIDIA Xsettings GUI.

Hope this might help someone else.

---

